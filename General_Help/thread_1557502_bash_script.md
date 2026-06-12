---
title: "bash script"
date: 2010-08-20
forum: General Help
---

### Post by elj33 on 2010-08-20
What does the following bash script ls-r

---

### Post by pastalavista on 2010-08-20
I think that should be ls -r with a space before the hyphen. To find out what commands do (very good idea before you run them) use the 'man' command```
man ls -r
```

---

### Post by WorMzy on 2010-08-20
It reverses the order of the ls output.

"ls" lists things alphabetically, starting (I guess) with numbers, then A, B, C, etc.
"ls -r" lists things the alphabetically, but starting at the other end, so Z, Y, X, etc.

---

### Post by samg34 on 2010-08-20
commands are formated as:
[command] [option] {-r|-l|--Verbose|-R}] [Parameter 1] [Parameter 2]

think of it like this. the Command is the Verb, the Option is the Adverb, the Parameter 1 is the Direct Object, and Parameter 2 is the Inderect object (or Object of Preposition)

---

### Post by dsiembab on 2010-08-20
try this one it works most of the time ls --help

---

