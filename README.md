# template-conv

Convert simple templates.

```js
import convertTemplate from "template-conv";
```

```js
const result = "hello world!";
const tests = [
  ["hello $0!", "world"],
  ["hello $0$1", ["world", "!"]],
  [
    "$111 $1$11",
    {
      $111: "hello",
      $1: "world",
      $11: "!",
    },
  ],
  [
    (a) => {
      const world = a.$0 === "hello" ? "world" : "";
      return `$0 ${world}!`;
    },
    "hello",
  ],
];
tests.map(([template, args]) => {
  console.assert(convertTemplate(template, args) === result);
});
```
