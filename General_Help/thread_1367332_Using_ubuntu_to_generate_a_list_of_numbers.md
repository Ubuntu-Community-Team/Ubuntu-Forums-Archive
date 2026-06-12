---
title: "Using ubuntu to generate a list of numbers"
date: 2009-12-29
forum: General Help
---

### Post by checkm8 on 2009-12-29
I need a program from ubuntu that can generate a list of numbers sequentially (example starting from 0000000000 to 9999999999) into a txt file. Is there any way for me to do this?

---

### Post by scoon on 2009-12-29
Hey there, 

Certainly - just use your favorite scripting language to get it done.

---

### Post by jollysnowman on 2009-12-29
Here are some helpful keywords:

python, file, open, for, xrange, write

---

### Post by mali2297 on 2009-12-29
There is a command line tool for this specific purpose, called *seq*. In a terminal, run
```
seq -w 0 999 > foo.txt
```
and you will get a list of numbers ranging from 000 to 999 in the file *foo.txt*. 

Check the man page or run ```
seq --help
``` for more information.

---

### Post by checkm8 on 2010-01-04
> **mali2297 said:**
> There is a command line tool for this specific purpose, called *seq*. In a terminal, run
```
seq -w 0 999 > foo.txt
```
and you will get a list of numbers ranging from 000 to 999 in the file *foo.txt*. 

Check the man page or run ```
seq --help
``` for more information.

Thank you just what I needed I appreciate all of your help!

---

### Post by jamesisin on 2010-01-04
Please mark your thread as solved (in Thread Tools above).

---

