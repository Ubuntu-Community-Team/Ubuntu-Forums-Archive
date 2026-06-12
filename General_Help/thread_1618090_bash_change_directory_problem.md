---
title: "bash change directory problem"
date: 2010-11-10
forum: General Help
---

### Post by grrrbob on 2010-11-10
Im using ubuntu 10.04 (lucid) with kernel linux 2.6.32-25-generic-pae and gnome 2.30.2

When in the terminal i have noticed that there are certain folders which i cannot access yet i can access them from gui. example being a game installed 
"bash: cd: Fallout: No such file or directory"
provides this error
this error also shows up when accessing wine program files
"desktop:~/.wine/drive_c$ ls
Program Files  users  windows
desktop:~/.wine/drive_c$ cd Program Files
bash: cd: Program: No such file or directory"

any ideas why this is happening and what i can do to resolve this?

kind regards

---

### Post by TeoBigusGeekus on 2010-11-10
Bash can't recognize names with spaces.
Try this
```
cd Program\ Files
```

---

### Post by grrrbob on 2010-11-10
thank you

---

### Post by ironic.demise on 2010-11-10
Also remember Ubuntu is case sensitive.
```
cd windows
``` will not be able to get into directory WINDOWS
'single' and "double" qoutes will help if there are a lot of spaces as you won't need to put a \ in long filenames

---

