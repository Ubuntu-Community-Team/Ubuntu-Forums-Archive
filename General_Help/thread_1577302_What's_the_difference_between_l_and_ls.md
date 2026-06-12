---
title: "What's the difference between l and ls ?"
date: 2010-09-18
forum: General Help
---

### Post by josteinaj on 2010-09-18
I've typed 'l' instead of 'ls' in the terminal by mistake a couple of times, and it seems to do pretty much - but not exactly - the same as 'ls' ('l' appends *, @ etc at the end of filenames which seem to indicate permissions and/or links).

I can't find any documentation on 'l'. 'l --help' gives exactly the same output as 'ls --help'. 'which l' gives nothing. There are no files in my filesystem called only 'l' either - just a couple of unrelated folders.

So what's the difference between l and ls?

---

### Post by CharlesA on 2010-09-18
It's an alias.

```
alias l='ls -CF'

```

---

### Post by squaregoldfish on 2010-09-18
It's an alias that calls ls with some different options - that's why it will display the help for ls.

To find out exactly what it's doing, enter

```
alias l
```

Steve.

---

