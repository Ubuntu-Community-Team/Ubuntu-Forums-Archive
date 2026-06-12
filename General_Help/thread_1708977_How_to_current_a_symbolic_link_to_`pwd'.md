---
title: "How to current a symbolic link to `pwd'"
date: 2011-03-17
forum: General Help
---

### Post by legendbb on 2011-03-17
How to use `pwd' to create a symbolic link?

$ ln -s `pwd' {link}

assuming `pwd' itself will expand to the current path.

thanks,

---

### Post by ~Plue on 2011-03-17
try within back quotes
```
ln -s **`**pwd**`** {link}
```

---

### Post by legendbb on 2011-03-17
Great thanks,

My mistake, inline command should be included within backquotes,

---

### Post by tredegar on 2011-03-17
**bash** backquotes are deprecated (meaning, "they still work but may not do so in the future, so please update your code before it breaks".)

**$(pwd)** is easier to read, and type (too many people try to use **[COLOR="Red"]'[/COLOR]pwd[COLOR="Red"]'[/COLOR]**, and it does not work), does the same thing as **`pwd`** and will be supported in future (until the next bash re-think).

Strictly speaking just a . "dot" is the equivalent of **`pwd`** or **$(pwd)** and is faster to type, not deprecated, and most unlikely *ever* to change. Please try it:
```
ls `pwd`
ls $(pwd)
ls .
```
All the same, no?

So ```
ln -s . {link}
```
should do it for you, and you'll be future-proofed for years (maybe ;) )

---

