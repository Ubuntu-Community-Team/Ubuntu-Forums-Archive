---
title: "Error setting a value into a python 2d array."
date: 2009-09-30
forum: General Help
---

### Post by valros on 2009-09-30
Something odd is ocurring, when I set array[1][1] = 1 it produces:

[
[0,1,0],
[0,1,0],
[0,1,0]]

instead of:

[
[0,0,0],
[0,1,0],
[0,0,0]]

---

### Post by Bachstelze on 2009-09-30
Can't reproduce. Maybe paste your actual code?

---

### Post by valros on 2009-09-30
[http://pastebin.com/d41375b61](http://pastebin.com/d41375b61)

I see now that its how I appended each row, god I hate this link crap, how can I set each row as itself?

---

### Post by diesch on 2009-09-30
You 2d array contains three times the same 1d array:

```

>>> a=[[0,0,0]]*3
>>> a
[[0, 0, 0], [0, 0, 0], [0, 0, 0]]
>>> a[1][1]=1
>>> a
[[0, 1, 0], [0, 1, 0], [0, 1, 0]]

```You have to create a new 1d array for every item in your 2d array:
```

>>> a=[[0,0,0] for i in range(3)]
>>> a
[[0, 0, 0], [0, 0, 0], [0, 0, 0]]
>>> a[1][1]=1
>>> a
[[0, 0, 0], [0, 1, 0], [0, 0, 0]]

```

---

