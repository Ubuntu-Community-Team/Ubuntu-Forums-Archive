---
title: "FInding where an alias points"
date: 2011-07-28
forum: General Help
---

### Post by max_sph on 2011-07-28
Hey guys,

Is there anyway to print on screen in a terminal window what an alias actually does?
For example, if I had an command that was an alias to open something in some directory, is there a way of finding out what the alias actually does?
Thanks :)

EDIT:: Sorry, forgot to mention: is there a way without looking in .bashrc / .bash_profile etc?

---

### Post by WorMzy on 2011-07-28
```
which <command>
```
e.g.
```
wormzy@sakura[pts/3]:~$ which ls
ls: aliased to ls --color=auto

```

---

### Post by seawolf167 on 2011-07-28
Maybe something like

```
cat ~/.bashrc | grep -i alias
```

---

### Post by vanadium on 2011-07-28
If you want to know what aliases you have defined, use the "alias" command.

---

### Post by seawolf167 on 2011-07-28
> **WorMzy said:**
> ```
which <command>
```e.g.
```
wormzy@sakura[pts/3]:~$ which ls
ls: aliased to ls --color=auto

```

This wouldn't work for any custom aliases created in ~/.bashrc though since they wouldn't be binaries in the $PATH variable

---

### Post by seawolf167 on 2011-07-28
> **vanadium said:**
> If you want to know what aliases you have defined, use the "alias" command.

Even easier than I thought it would be - thanks for the info!

---

### Post by WorMzy on 2011-07-28
My bad. I use zsh, which replaces the which command with an in-built shell command which takes into account aliases.

---

### Post by Habitual on 2011-07-28
```
alias <alias>
alias | grep <alias/part-of-alias/etc/>
```

---

