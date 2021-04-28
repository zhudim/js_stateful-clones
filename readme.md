# Cloning and transforming state

**Read [the guideline](https://github.com/mate-academy/js_task-guideline/blob/master/README.md) before start**

# Task description

Implement a function accepting 2 arguments: `state` and `transforms`.
The function should return an array of the same length as `transforms`.
The array should contain all previous versions of `state`.
Each element of the resulting array has to represent the state produced by the next operation.

**IMPORTANT!** You must not modify the `state` in any way!

- `state` is an initial object. It should always remain the same.

- `transforms` is an array of objects. Each object in this array has the two following properties:
  - First - `operation`: either `addProperties`, `removeProperties` or `clear`;
  - Second - `properties`:
    - if `operation` is `addProperties`, field `properties` contains an object
      with `key: value` pairs to add to the state;
    - if `operation` is `removeProperties`, field `properties` contains an array
      with the list of property names (keys) to remove from the `state`; (Not existing
      properties should be ignored)
    - if `operation is `clear` you should you should create an empty state object

Example of usage:

If `state` is {foo: 'bar', bar: 'foo'}, then

```
transformStateWithClones(state, [
  {operation: 'addProperties', properties: {name: 'Jim', hello: 'world'}},
  {operation: 'removeProperties', properties: ['bar', 'hello']},
  {operation: 'addProperties', properties: {another: 'one'}}
])
```

must return the following array:

```
[
  {foo: 'bar', bar: 'foo', name: 'Jim', hello: 'world'},
  {foo: 'bar', name: 'Jim'},
  {foo: 'bar', name: 'Jim', another: 'one'}
].
```

**The `state` object itself should not be modified and must remain {foo: 'bar', bar: 'foo'}.**

Then after calling

```
transformStateWithClones(state, [
  {operation: 'addProperties', properties: {yet: 'another property'}}
  {operation: 'clear'},
  {operation: 'addProperties', properties: {foo: 'bar', name: 'Jim'}}
])
```
we must get
```
[
  {foo: 'bar', bar: 'foo', yet: 'another property'},
  {},
  {foo: 'bar', name: 'Jim'}
].
```
the `state` variable must still contain
{foo: 'bar', bar: 'foo'}.
