# Fork info

- Forked on 1/1/2023
- Added some optimizations when typing speed is set to 0
  - Characters / lines to type are copied straight into the text buffer
    (and straight on the page) if speed is set to 0 at the beginning of
    the component, or after a `<Reset>`
  - Text is animated in "sections" instead of character by character when
    speed is set to 0 at other times, which still isn't pefect due to each
    render executing asynchronously, but it reduces the number of renders, so
    that's an improvement
- Added a prepare hook to fix builds when installing this fork via a Git URL

Original README proceeds below:

# React-typing-animation

[![npm version](https://img.shields.io/npm/v/react-typing-animation.svg)](https://npm.im/react-typing-animation) ![Licence](https://img.shields.io/npm/l/react-typing-animation.svg)

> A fully-featured typing animation in React that supports any valid JSX.

<p align="center"><img src ="https://github.com/adamjking3/react-typing-animation/blob/master/typing.gif" /></p>

## Motivation

There were other JS typing animations that existed when I created this, but they were all lacking in robust features. This component aims to support all of the following features:

✅ Type text from any valid JSX

✅ Preserve DOM structure/styling

✅ Change typing speed anywhere in tree

✅ Add a delay anywhere in tree

✅ Backspace animation

✅ Reset lines / full tree

✅ Loop functionality

✅ No dependencies (CSS or JS)

## Demo

View the [live demo](https://adamjking3.github.io/react-typing-animation-example/)

**or**

```shell
git clone https://github.com/adamjking3/react-typing-animation
cd react-typing-animation
npm install
npm start
```

Then open http://localhost:3000/ in a browser.

**Feature requests and pull requests welcome**

## Installation

```shell
npm i --save react-typing-animation
```

## Usage

```jsx
import Typing from 'react-typing-animation';

const AnimatedTypingComponent = () => (
  <Typing>
    <span>This span will get typed.</span>
  </Typing>
);
```

## Documentation

|     Property     |    Type    |                                            Default                                             | Required |
| :--------------: | :--------: | :--------------------------------------------------------------------------------------------: | :------: |
|     element     | string |   div                                                                                             |   no    |
|     children     | React node |                                                                                                |   yes    |
|    className     |   string   |                                                                                                |    no    |
|    cursorClassName     |   string   |                                                                                                |    no    |
|     cursorElement     | string |   span                                                                                             |   no    |
|      cursor      | React node | [`<Cursor />`](https://github.com/adamjking3/react-typing-animation/blob/master/src/Cursor.js) |    no    |
|      hideCursor      |  boolean   |                                             false                                              |    no    |
|      speed       |   number   |                                            50 (ms)                                             |    no    |
|    startDelay    |   number   |                                             0 (ms)                                             |    no    |
|       loop       |  boolean   |                                             false                                              |    no    |
| onStartedTyping |  function  |                                            () => {}                                            |    no    |
| onBeforeType |  function  |                                            () => {}                                            |    no    |
| onAfterType |  function  |                                            () => {}                                            |    no    |
| onFinishedTyping |  function  |                                            () => {}                                            |    no    |

*Note: if `cursorElement` is set as an empty string, a React.Fragment element will be used to wrap children.*

### Backspace Component

```jsx
import Typing from 'react-typing-animation';
...
  <Typing>
    <span>This span will get typed, then erased.</span>
    <Typing.Backspace count={20} />
  </Typing>
```

| Property |  Type  | Default | Required | Description |
| :------: | :----: | :-----: | :------: | :---------: |
|  count   | number |    1    |  false   |             |
|  delay   | number |    0    |  false   |             |
|  speed   | number |   -1    |  false   |             |

### Delay Component

```jsx
import Typing from 'react-typing-animation';
...
  <Typing>
    <div>
      There will be a 1000ms delay here,
      <Typing.Delay ms={1000} />
      then this will be typed.
    </div>
  </Typing>
```

| Property |  Type  | Default | Required | Description |
| :------: | :----: | :-----: | :------: | :---------: |
|    ms    | number |         |   yes    |             |

### Speed Component

```jsx
import Typing from 'react-typing-animation';
...
  <Typing speed={50}>
    This line will be typed at 50ms/character,
    <Typing.Speed ms={200} />
    then this will be typed at 200ms/character.
  </Typing>
```

| Property |  Type  | Default | Required | Description |
| :------: | :----: | :-----: | :------: | :---------: |
|    ms    | number |         |   yes    |             |

### Reset Component

```jsx
import Typing from 'react-typing-animation';
...
  <Typing>
    <span>This line will stay.</span>
    <span>This line will get instantly removed after a 500 ms delay</span>
    <Typing.Reset count={1} delay={500} />
  </Typing>
```

| Property |  Type  | Default | Required | Description |
| :------: | :----: | :-----: | :------: | :---------: |
|  count   | number |    0    |  false   |             |
|  delay   | number |    0    |  false   |             |
|  speed   | number |   -1    |  false   |             |

## Contributing

After cloning the repository and running npm install inside, you can use the following commands to develop and build the project.

```shell
# Starts a webpack dev server that hosts the demo at http://localhost:3000
npm start

# Lints the code with eslint
npm run lint

# Lints and builds the code, placing the result in the dist directory.
npm run build
```

Pull requests are welcome!

## License

[MIT](https://github.com/adamjking3/react-typing-animation/blob/master/LICENSE)
