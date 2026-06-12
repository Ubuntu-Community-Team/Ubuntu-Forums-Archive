---
title: "Terminal &quot;cd&quot; command"
date: 2010-04-29
forum: General Help
---

### Post by fterh on 2010-04-29
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

fabian@fabian-ubuntu:~$ cd /Downloads
bash: cd: /Downloads: No such file or directory
fabian@fabian-ubuntu:~$ cd /
fabian@fabian-ubuntu:/$ cd /boot
fabian@fabian-ubuntu:/boot$ 

```

Why is it that when I cd /Downloads into the Downloads directory it tells me "No such file or directory", yet if I were to cd / into the file system and then I cd /boot into the boot folder it works? :confused:

---

### Post by sonik88 on 2010-04-29
To move into another directory you first need to make sure that this directory exists.:P

When you open a terminal you are in your default directory. From there you can move down (cd Desktop), up (cd ..) or from root to anywhere (like cd /boot).

Try before cd the ls command to make sure that the directory you wanna move into is there.

Cheers

---

### Post by dino99 on 2010-04-29
note that everything is case sensitive with ubuntu and linux in general

---

### Post by rnerwein on 2010-04-29
hi
i don't want to hassle you - but be carefull to run commands as root.
but your question about your cd --> have a look first at the filesystem structers in unix.
the Download directory exists in your home dirictory.
a little step first: do a "pwd" and you see where you are and then a ls to see the contens (most of it ) ouf yuor directory.
but i'll tell you - first read some documentations or you will never be happy with unix/linux systems.
have much fun - and good luck.
ciao

---

### Post by fterh on 2010-04-29
I think I get it, the "/" slash in front means "from root", not from "current directory". Thanks! :)

---

