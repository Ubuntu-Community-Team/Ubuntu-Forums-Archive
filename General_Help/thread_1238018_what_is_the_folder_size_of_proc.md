---
title: "what is the folder size of /proc ?"
date: 2009-08-12
forum: General Help
---

### Post by madhavhmk on 2009-08-12
I am suspecting that a lot of unwanted files are getting into this folder when I setup some custom commands in /usr/bin

I just want to compare the folder size of /proc to see if it is building up....I am running out of HDD space and trying to remove any unwanted files...

So guys, Please help me out....
Just check your respective porc folder in root and tell me its size..!!!!

---

### Post by MG37221 on 2009-08-12
Mine's 3GB running 9.04 64bit.

---

### Post by madhavhmk on 2009-08-12
Thanks.....so I see that is not a problem, coz mine is showing 856MB in 8.04


I am suspecting that files are building up in some folder due to modification in /usr/bin I ll check it out....

Thanks again for the help

---

### Post by CatKiller on 2009-08-12
[/proc]("http://en.wikipedia.org/wiki/Procfs") takes up no hard drive space. It doesn't exist.

---

### Post by P4man on 2009-08-12
In Applications / accessories you'll find a neat little app to monitor your HD usage. Not sure about the english name "disk usage" I think.

---

### Post by mcduck on 2009-08-12
> **CatKiller said:**
> [/proc]("http://en.wikipedia.org/wiki/Procfs") takes up no hard drive space. It doesn't exist.

+1 for this.

Virtual filesystems and pseudo filesystems don't take any real disk space. Don't let the fact that everything is a file in Linux confuse you to think that every file you see actually exists in your hard drive. :)

---

### Post by credobyte on 2009-08-12
> **CatKiller said:**
> [/proc]("http://en.wikipedia.org/wiki/Procfs") takes up no hard drive space. It doesn't exist.

```
30,077 items, totalling 1012.3 MB
```
If it doesn't exist, how it's possible to see 30k files / 1Gb ( impossible to hold such an amount in RAM ) ?

---

### Post by mcduck on 2009-08-12
Simply because some of the data is in RAM, some of it is in your hard drive, and some of it might not really even exist.

/proc contains process information. So what ever processes are running in your computer, they all show as files inside /proc.

[http://en.wikipedia.org/wiki/Procfs]("http://en.wikipedia.org/wiki/Procfs")

Many of the system directories are like this, for example /dev, /proc, /sys, and ~/.gvfs don't contain actual files in the same meaning as files you would store in your harddrive.

Everything is a file in Linux, every running process, every device and hardware component, and even many components that you might not actually have show as files somewhere in the filesystem. And obviously your mouse, for example, doesn't take any disk space or memory, not even when it shows as /dev/mouse in the filesystem..

---

