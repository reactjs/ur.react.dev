---
title: جلدی شروع کریں
---

<Intro>

تفصیلاتی گائیڈ میں خوش آمدید! یہ پیج آپکو React کے 80% مفاہیم کا تعارف کروائے گا جو آپ روزانہ استعمال کرتے ہیں۔

</Intro>

<YouWillLearn>

- کمپونینٹ بنانے اور نیسٹ کرنے کا طریقہ
- مارکپ اور اسٹائل کو کیسے شامل کریں
- ڈیٹا کو ڈسپلے کرنے کا طریقہ
- کنڈیشنز اور لسٹ کو رینڈر کرنے کا طریقہ
- ایونٹ کا جواب اور سکرین کو اپڈیٹ کرنے کا طریقہ
- کمپونینٹس کے درمیان ڈیٹا بھیجنے کا طریقہ

</YouWillLearn>

## کمپونینٹ کو بنانا اور نیسٹ کرنا {/*components*/}

React ایپس کچھ *کمپونینٹ* کو ملا کر بنتی ہیں۔ ایک کمپونینٹ یوزر انٹرفیس کا ایک حصہ کہلاتا ہے جس کے پاس اپنا لاجک اور ڈیزائن ہوتا ہے. کمپونینٹ ایک چھوٹا سا بٹن بھی ہوسکتا ہے اور ایک مکمل پیج بھی ہوسکتا ہے۔

React کمپونینٹ جاواسکرپٹ کے فنکشن ہوتے ہیں جو مارکپ کو واپس بھیجتے ہیں:

<div dir="ltr">
```js
function MyButton() {
  return (
    <button>I'm a button</button>
  );
}
```
</div>

ابھی اپنے `MyButton` کمپونینٹ بنایا، اسے آپ ایک اور کمپونینٹ میں نیسٹ (شامل) بھی کر سکتے ہیں:

<div dir="ltr">
```js {5}
export default function MyApp() {
  return (
    <div>
      <h1>Welcome to my app</h1>
      <MyButton />
    </div>
  );
}
```
</div>

آپ دیکھیں کہ `MyButton` بڑے لفظ سے شروع ہوتا ہے۔ اور اِسی طرح آپ پہچان سکتے ہیں کہ یہ ایک React کمپونینٹ ہے۔ React کمپونینٹ ہمیشہ بڑے لفظ سے شروع ہونے چاہئیں، جبکہ HTML ٹیگ چھوٹے لفظوں میں ہونے چاہئیں۔

نتیجہ ملاحظہ کریں:

<div dir="ltr">
<Sandpack>

```js
function MyButton() {
  return (
    <button>
      I'm a button
    </button>
  );
}

export default function MyApp() {
  return (
    <div>
      <h1>Welcome to my app</h1>
      <MyButton />
    </div>
  );
}
```

</Sandpack>
</div>

`export default` لفظ فائل میں مرکزی کمپونینٹ کی وضاحت کرتا ہے۔ اگر آپ جاواسکرپٹ کے کچھ حصوں سے ناواقف ہیں تو [MDN](https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export) اور [javascript.info](https://javascript.info/import-export) سیکھنے کے لئے اچھی جگہیں ہیں۔ 

## مارکپ کو JSX کے ساتھ لکھنا {/*writing-markup-with-jsx*/}

جو آپنے اوپر مارکپ کوڈ دیکھا ہے جو *JSX* کہلاتا ہے۔ یہ ضروری نہیں ہے، لیکن بیشتر React پراجیکٹ اپنی آسانی کے لئے JSX کو استعمال کرتے ہیں۔ جتنے بھی [ٹولز ہم لوکل ڈویلپمنٹ کے لیے بتاتے](/learn/installation) ہیں وہ JSX کی حمایت کرتے ہیں۔

JSX کے قوانین HTML سے زیادہ سخت ہیں۔ آپکو ٹیگ کو کچھ اس طرح بند کرنا ہوتا ہے `</br>`. آپکا کمپونینٹ ایک سے زائد JSX ٹیگ کو واپس بھی نہیں بھیج سکتا۔ آپکو ایک سے زائد ٹیگ کو کسی ایک ٹیگ میں شامل کرنا ہوتا ہے، مثلاً `<div>...</div>` یا پھر خالی `<>...</>` ریپر :

<div dir="ltr">
```js {3,6}
function AboutPage() {
  return (
    <>
      <h1>About</h1>
      <p>Hello there.<br />How do you do?</p>
    </>
  );
}
```
</div>

اگر آپکے پاس کافی زیادہ HTML ہے جسے JSX میں تبدیل کرنا ہے تو آپ [آنلائن کنورٹر](https://transform.tools/html-to-jsx) استعمال کر سکتے ہیں۔

## اسٹائل شامل کرنا {/*adding-styles*/}

React میں آپ CSS کی کلاس `className` کا استعمال کرتے ہوے واضح کرتے ہیں۔ اور یہ بلکل [`class`](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/class) HTML کی طرح ہی کام کرتی ہے :

<div dir="ltr">
```js
<img className="avatar" />
```
</div>

پھر آپ اس کے لئے CSS کا کوڈ ایک الگ فائل میں لکھتے ہیں :

<div dir="ltr">
```css
/* In your CSS */
.avatar {
  border-radius: 50%;
}
```
</div>

React کوئی خاص طریقہ مقرر نہیں کرتا کہ آپ کیسے سی ایس ایس فائلوں کو شامل کریں۔ سب سے آسان صورت میں ، آپ ایک [`<link>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link) ٹیگ کو اپنی HTML میں شامل کریں گے۔ اگر آپ بلڈ ٹول یا فریم ورک استعمال کرتے ہیں تو، آپ کو اسکی دستاویزات یا گائیڈ دیکھنی چاہیے۔

## ڈیٹا کو ڈسپلے پر دکھانا {/*displaying-data*/}

JSX آپکو مارکپ کو جاواسکرپٹ میں لکھنے کی صلاحیت فراہم کرتا ہے۔ کرلی بریسز `{}` کے ساتھ آپ دوبارہ جاواسکرپٹ کا استعمال کر سکتے ہیں تاکہ `variable` کو اپنے کوڈ میں شامل کر کے یوزر کو دیکھا سکیں۔ مثلاً، یہ `user.name` کو ڈسپلے پر دکھائے گا :

<div dir="ltr">
```js {3}
return (
  <h1>
    {user.name}
  </h1>
);
```
</div>

 آپ جاواسکرپٹ کو `attributes` JSX میں بھی استعمال کر سکتے ہیں، لیکن اسکے لیے آپکو کوٹیشنز `""` کی بجائے کرلی بریسز `{}` کو استعمال کرنا ہوگا۔ مثلاً `"className="avatar` استعمال کرنے سے `avatar` کو CSS کی کلاس سمجھا جائیگا، لیکن `src={user.imageUrl}` استعمال کرنے سے `user.imageUrl` کو جاواسکرپٹ کا ویریبل سمجھا جائیگا، اور `src` کو ویریبل کی ویلیو پاس کردی جائیگی :

<div dir="ltr">
```js {3,4}
return (
  <img
    className="avatar"
    src={user.imageUrl}
  />
);
```
</div>

آپ JSX کی کرلی بریسز `{}` میں پیچیدہ جاواسکرپٹ ایکسپریشنز کا بھی استعمال کر سکتے ہیں، مثلاً [دو سٹرنگز کو جمع کرنا](https://javascript.info/operators#string-concatenation-with-binary): 

<div dir="ltr">
<Sandpack>

```js
const user = {
  name: 'Hedy Lamarr',
  imageUrl: 'https://i.imgur.com/yXOvdOSs.jpg',
  imageSize: 90,
};

export default function Profile() {
  return (
    <>
      <h1>{user.name}</h1>
      <img
        className="avatar"
        src={user.imageUrl}
        alt={'Photo of ' + user.name}
        style={{
          width: user.imageSize,
          height: user.imageSize
        }}
      />
    </>
  );
}
```

```css
.avatar {
  border-radius: 50%;
}

.large {
  border: 4px solid gold;
}
```

</Sandpack>
</div>
 
اوپر والے کوڈ میں `{{}}=style` کوئی نیا سینٹیکس نہیں ہے، بلکہ یہ ایک سادہ جاواسکرپٹ کا ہی آبجیکٹ `{}` ہے جسکو `{}=style` کے اندر رکھا گیا ہے۔ 



## کنڈیشنل رینڈرنگ {/*conditional-rendering*/}

React میں کنڈیشن لکھنے کا کوئی خاص طریقہ نہیں ہے، بلکہ آپ بلکل اُسی طرح لکھتے ہیں جیسے جاواسکرپٹ کا نارمل کوڈ لکھا جاتا ہے۔ مثلاً، آپ [`if`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else) اسٹیٹمینٹ کو استعمال کر سکتے ہیں JSX کو مشروط طور پر شامل کرنے کے لئے :


<div dir="ltr">
```js
let content;
if (isLoggedIn) {
  content = <AdminPanel />;
} else {
  content = <LoginForm />;
}
return (
  <div>
    {content}
  </div>
);
```
</div>


اگر آپ مختصر کوڈ لکھنا پسند کرتے ہیں تو آپ [کنڈیشنل `?` آپریٹر](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator) کا استعمال کر سکتے ہیں۔ یہ `if` کے برعکس JSX کے اندر ہی کام کر سکتا ہے :

<div dir="ltr">
```js
<div>
  {isLoggedIn ? (
    <AdminPanel />
  ) : (
    <LoginForm />
  )}
</div>
```
</div>

جب آپکو `else` اسٹیٹمینٹ کی ضرورت نا ہو تو آپ [لاجیکل `&&` سینٹیکس](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND#short-circuit_evaluation) کا بھی استعمال کر سکتے ہیں جوکہ مزید مختصر ہوجاتا ہے :

<div dir="ltr">
```js
<div>
  {isLoggedIn && <AdminPanel />}
</div>
```
</div>

یہ سب طریقے مشروط طور پر `attributes` کو واضح کرنے کے لیے بھی کام آتے ہیں۔ اگر آپ جاواسکرپٹ کے اس طرح کے کچھ حصوں سے ناواقف ہیں تو آپ ہمیشہ `if...else` سے شروعات کر سکتے ہیں۔

## Rendering lists {/*rendering-lists*/}

You will rely on JavaScript features like [`for` loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for) and the [array `map()` function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) to render lists of components.

For example, let's say you have an array of products:

```js
const products = [
  { title: 'Cabbage', id: 1 },
  { title: 'Garlic', id: 2 },
  { title: 'Apple', id: 3 },
];
```

Inside your component, use the `map()` function to transform an array of products into an array of `<li>` items:

```js
const listItems = products.map(product =>
  <li key={product.id}>
    {product.title}
  </li>
);

return (
  <ul>{listItems}</ul>
);
```

Notice how `<li>` has a `key` attribute. For each item in a list, you should pass a string or a number that uniquely identifies that item among its siblings. Usually, a key should be coming from your data, such as a database ID. React uses your keys to know what happened if you later insert, delete, or reorder the items.

<Sandpack>

```js
const products = [
  { title: 'Cabbage', isFruit: false, id: 1 },
  { title: 'Garlic', isFruit: false, id: 2 },
  { title: 'Apple', isFruit: true, id: 3 },
];

export default function ShoppingList() {
  const listItems = products.map(product =>
    <li
      key={product.id}
      style={{
        color: product.isFruit ? 'magenta' : 'darkgreen'
      }}
    >
      {product.title}
    </li>
  );

  return (
    <ul>{listItems}</ul>
  );
}
```

</Sandpack>

## Responding to events {/*responding-to-events*/}

You can respond to events by declaring *event handler* functions inside your components:

```js {2-4,7}
function MyButton() {
  function handleClick() {
    alert('You clicked me!');
  }

  return (
    <button onClick={handleClick}>
      Click me
    </button>
  );
}
```

Notice how `onClick={handleClick}` has no parentheses at the end! Do not _call_ the event handler function: you only need to *pass it down*. React will call your event handler when the user clicks the button.

## Updating the screen {/*updating-the-screen*/}

Often, you'll want your component to "remember" some information and display it. For example, maybe you want to count the number of times a button is clicked. To do this, add *state* to your component.

First, import [`useState`](/reference/react/useState) from React:

```js
import { useState } from 'react';
```

Now you can declare a *state variable* inside your component:

```js
function MyButton() {
  const [count, setCount] = useState(0);
  // ...
```

You’ll get two things from `useState`: the current state (`count`), and the function that lets you update it (`setCount`). You can give them any names, but the convention is to write `[something, setSomething]`.

The first time the button is displayed, `count` will be `0` because you passed `0` to `useState()`. When you want to change state, call `setCount()` and pass the new value to it. Clicking this button will increment the counter:

```js {5}
function MyButton() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <button onClick={handleClick}>
      Clicked {count} times
    </button>
  );
}
```

React will call your component function again. This time, `count` will be `1`. Then it will be `2`. And so on.

If you render the same component multiple times, each will get its own state. Click each button separately:

<Sandpack>

```js
import { useState } from 'react';

export default function MyApp() {
  return (
    <div>
      <h1>Counters that update separately</h1>
      <MyButton />
      <MyButton />
    </div>
  );
}

function MyButton() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <button onClick={handleClick}>
      Clicked {count} times
    </button>
  );
}
```

```css
button {
  display: block;
  margin-bottom: 5px;
}
```

</Sandpack>

Notice how each button "remembers" its own `count` state and doesn't affect other buttons.

## Using Hooks {/*using-hooks*/}

Functions starting with `use` are called *Hooks*. `useState` is a built-in Hook provided by React. You can find other built-in Hooks in the [API reference.](/reference/react) You can also write your own Hooks by combining the existing ones.

Hooks are more restrictive than other functions. You can only call Hooks *at the top* of your components (or other Hooks). If you want to use `useState` in a condition or a loop, extract a new component and put it there.

## Sharing data between components {/*sharing-data-between-components*/}

In the previous example, each `MyButton` had its own independent `count`, and when each button was clicked, only the `count` for the button clicked changed:

<DiagramGroup>

<Diagram name="sharing_data_child" height={367} width={407} alt="Diagram showing a tree of three components, one parent labeled MyApp and two children labeled MyButton. Both MyButton components contain a count with value zero.">

Initially, each `MyButton`'s `count` state is `0`

</Diagram>

<Diagram name="sharing_data_child_clicked" height={367} width={407} alt="The same diagram as the previous, with the count of the first child MyButton component highlighted indicating a click with the count value incremented to one. The second MyButton component still contains value zero." >

The first `MyButton` updates its `count` to `1`

</Diagram>

</DiagramGroup>

However, often you'll need components to *share data and always update together*.

To make both `MyButton` components display the same `count` and update together, you need to move the state from the individual buttons "upwards" to the closest component containing all of them.

In this example, it is `MyApp`:

<DiagramGroup>

<Diagram name="sharing_data_parent" height={385} width={410} alt="Diagram showing a tree of three components, one parent labeled MyApp and two children labeled MyButton. MyApp contains a count value of zero which is passed down to both of the MyButton components, which also show value zero." >

Initially, `MyApp`'s `count` state is `0` and is passed down to both children

</Diagram>

<Diagram name="sharing_data_parent_clicked" height={385} width={410} alt="The same diagram as the previous, with the count of the parent MyApp component highlighted indicating a click with the value incremented to one. The flow to both of the children MyButton components is also highlighted, and the count value in each child is set to one indicating the value was passed down." >

On click, `MyApp` updates its `count` state to `1` and passes it down to both children

</Diagram>

</DiagramGroup>

Now when you click either button, the `count` in `MyApp` will change, which will change both of the counts in `MyButton`. Here's how you can express this in code.

First, *move the state up* from `MyButton` into `MyApp`:

```js {2-6,18}
export default function MyApp() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <div>
      <h1>Counters that update separately</h1>
      <MyButton />
      <MyButton />
    </div>
  );
}

function MyButton() {
  // ... we're moving code from here ...
}

```

Then, *pass the state down* from `MyApp` to each `MyButton`, together with the shared click handler. You can pass information to `MyButton` using the JSX curly braces, just like you previously did with built-in tags like `<img>`:

```js {11-12}
export default function MyApp() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <div>
      <h1>Counters that update together</h1>
      <MyButton count={count} onClick={handleClick} />
      <MyButton count={count} onClick={handleClick} />
    </div>
  );
}
```

The information you pass down like this is called _props_. Now the `MyApp` component contains the `count` state and the `handleClick` event handler, and *passes both of them down as props* to each of the buttons.

Finally, change `MyButton` to *read* the props you have passed from its parent component:

```js {1,3}
function MyButton({ count, onClick }) {
  return (
    <button onClick={onClick}>
      Clicked {count} times
    </button>
  );
}
```

When you click the button, the `onClick` handler fires. Each button's `onClick` prop was set to the `handleClick` function inside `MyApp`, so the code inside of it runs. That code calls `setCount(count + 1)`, incrementing the `count` state variable. The new `count` value is passed as a prop to each button, so they all show the new value. This is called "lifting state up". By moving state up, you've shared it between components.

<Sandpack>

```js
import { useState } from 'react';

export default function MyApp() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <div>
      <h1>Counters that update together</h1>
      <MyButton count={count} onClick={handleClick} />
      <MyButton count={count} onClick={handleClick} />
    </div>
  );
}

function MyButton({ count, onClick }) {
  return (
    <button onClick={onClick}>
      Clicked {count} times
    </button>
  );
}
```

```css
button {
  display: block;
  margin-bottom: 5px;
}
```

</Sandpack>

## Next Steps {/*next-steps*/}

By now, you know the basics of how to write React code!

Check out the [Tutorial](/learn/tutorial-tic-tac-toe) to put them into practice and build your first mini-app with React.
