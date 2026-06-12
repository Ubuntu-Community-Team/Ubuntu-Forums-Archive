---
title: "colours in ls"
date: 2010-02-26
forum: General Help
---

### Post by cucuru on 2010-02-26
hello, I dont know why when I do ls I have all the files and folders written in black, in another computer I have different colours depending on the permissions.

do you know how to solve it? it's very annoying use ls -l

thanks! regards!

---

### Post by underquark on 2010-02-26
TRY:

man dircolors

OR:

info dircolors

AND SEE:

dircolors --print-database

---

### Post by sisco311 on 2010-02-26
Check if ls is an alias for ls --color=auto:
```
alias
```
if not, append the ~/.bashrc file with:
```
alias ls='ls --color=auto'
```
then run:
```
. ~/.bashrc
ls
```

---

### Post by underquark on 2010-02-26
> **sisco311 said:**
> Check if ls is an alias for ls --color=autoAh, yes.  That's more likely than the color database having been altered.

---

### Post by cucuru on 2010-02-26
Perfect! thank you very much!!!

---

### Post by sisco311 on 2010-02-26
You're welcome!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

