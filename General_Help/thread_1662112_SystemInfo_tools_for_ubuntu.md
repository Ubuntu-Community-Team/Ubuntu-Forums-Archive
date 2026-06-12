---
title: "System/Info tools for ubuntu"
date: 2011-01-07
forum: General Help
---

### Post by LetsMugSanta on 2011-01-07
Yeah so I am really familiar with the majority of Windows tools such as the cmd line, msconfig, registry and other things.

So my question is, are there any tools for ubuntu, such as memory analyzers, hard disk, system usage, etc. Are there also any guides/documentation on them? I am only familiar with probably the gconf-editor

---

### Post by Frogs Hair on 2011-01-07
This link can be useful and the system monitor and disk utility are handy too . [http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

---

### Post by TeoBigusGeekus on 2011-01-07
My preferred tool for ram and cpu resources' analysis is htop.
```
sudo apt-get install htop
```
from terminal to install it. You run it typing 
```
htop
```

For hard disk usage analysis you can run the df command with the -h parameter (human readable sizes)
```
df -h
```

An awesome book about Ubuntu is [this]("http://ubuntu-manual.org/").
If you want to start discovering the great power that the command line gives you, you could start with [this]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") book.

---

### Post by Chesamo on 2011-01-07
gnome-system-monitor does that. So does sysinfo.

---

### Post by TeoBigusGeekus on 2011-01-07
Oh, I forgot to tell you that for every command in linux, you can see its documentation/manual by running the command man with the command's name.
So to see the manual of htop and df, you should run
```
man htop
```
and
```
man df
```
respectively.

---

### Post by LetsMugSanta on 2011-01-07
Thanks for the help and docs.

---

