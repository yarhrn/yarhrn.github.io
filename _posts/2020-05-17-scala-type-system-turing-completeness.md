---
layout: post
published: true
title: "Proof of scala type system turing completness"
visible: 1
---

According to Stackoverflow answer:
> It means the type system has enough features in it to represent arbitrary computations. 

To prove Turing completeness several techniques could be used:
- implement Turing machine
- implement SKI combinator calculus
- implement Rule 110.

Rule 110 is a name of elementary cellular automata. 


Let's imagine we have an infinite array of 1 and 0. There is a pointer that encodes the current position.
Also, we can access to the left and right elements regarding pointer.
We can iterate over the array and produce a new array by converting the value in the cell and its two neighbors to 1 or 0.
That's it, naive explanation of elementary cellular automata.

Rule 110 is one of 256 possible elementary cellular automata.
It can be presented as

|left|current|right|result|
|-|-|-|-|
|1|1|1|0|
|1|1|0|1|
|1|0|1|1|
|1|0|0|0|
|0|1|1|1|
|0|1|0|1|
|0|0|1|1|
|0|0|0|1|

This table can be presented as a boolean formula 
```
(not right and current) or (right and not (left and current))
```

<script src="https://gist.github.com/yarhrn/0a99d216850942f1f63059fcc4b8e32e.js"></script>

Credits:
- [Rule 110](https://en.wikipedia.org/wiki/Rule_110)
- [Turing completeness](https://en.wikipedia.org/wiki/Turing_completeness)
- [Type-level programming](https://apocalisp.wordpress.com/2010/06/08/type-level-programming-in-scala/)