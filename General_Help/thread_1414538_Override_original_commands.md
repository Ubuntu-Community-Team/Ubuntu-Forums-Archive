---
title: "Override original commands"
date: 2010-02-23
forum: General Help
---

### Post by los21282 on 2010-02-23
Is there a way to override original commands?  For example, if i wanted ls to run a script to do a specific action before it listed the directory.  Thank you

---

### Post by nothingspecial on 2010-02-23
For me, at least, you will have to explain further.

---

### Post by los21282 on 2010-02-23
well right now if i type "ls" i will get the directory listing.  But what if i want it to execute a script that will echo out "you are now listing a directory" and then actually do what it is supposed to do.  I guess i want something like an alias only instead of using a new name for the command i can override one that already exist.

---

### Post by sisco311 on 2010-02-23
> **los21282 said:**
> well right now if i type "ls" i will get the directory listing.  But what if i want it to execute a script that will echo out "you are now listing a directory" and then actually do what it is supposed to do.  I guess i want something like an alias only instead of using a new name for the command i can override one that already exist.

well, then use... an alias. :)

```
alias ls='echo whatever && ls --color'
```

---

### Post by nothingspecial on 2010-02-23
You can alias ls (or any other command for that matter).

So in .bashrc ```
alias ls='ls -options -you -want -to -give -it'
```

Or to make ls cp alias ```
ls='cp'
``` etc

---

### Post by los21282 on 2010-02-23
Doesn't work :)  Alias only work with a new command.  For example your code would work if it had ll instead of ls.

---

### Post by los21282 on 2010-02-23
well it seems to work on the user .bashrc file but not the main /etc/bash.bashrc for all users.  Any ideas why that might be?

---

### Post by nothingspecial on 2010-02-23
Try restarting bash after you define the alias.

```
bash
```

:D

---

### Post by sisco311 on 2010-02-23
> **los21282 said:**
> Doesn't work :)  Alias only work with a new command.  For example your code would work if it had ll instead of ls.

It should work. 

i.e. ls, by default, is already an alias for *ls --color=auto*.

---

### Post by los21282 on 2010-02-23
well i can't get it to work for all users.  I'll just make a script to copy the file to all user directories.  Thanks for the help

---

### Post by sisco311 on 2010-02-23
Bash executes first the commands in the /etc/bash.bashrc then the commands in the ~/.bashrc file. By default, ls is defined as an alias for 'ls --color=auto' in the ~/.bashrc file, which overrides the alias defined in the /etc/bash.bashrc file.

So comment out/remove the "alias ls='ls --color=auto'" line in the ~/.bashrc file & you should be all fine.

---

