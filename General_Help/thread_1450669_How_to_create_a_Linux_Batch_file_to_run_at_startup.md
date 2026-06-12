---
title: "How to create a Linux Batch file to run at startup?"
date: 2010-04-09
forum: General Help
---

### Post by schwabdale on 2010-04-09
I am use to microsoft products. 
In microsoft windows, I can make a batch file that says to delete a file on the desktop during startup. 

I would like to create a "batch file" or command that runs at logon in Ubuntu. 
An example: If I wanted to delete a certain file on the desktop called "new.pdf" everytime I logon, 
                     Could I make some kind of file the has the commands "rm new.pdf" in it and run it as 
                     a file during login?

---

### Post by patchwork on 2010-04-09
You can add it to your /etc/rc.local

---

### Post by schwabdale on 2010-04-09
> **patchwork said:**
> You can add it to your /etc/rc.local


Can you please be more specific... I know very little about this. A step by step would be awesome!

---

### Post by patchwork on 2010-04-09
The rc.local is executed on start-up (actually, it is executed on each muti-user runlevel, but for our purposes start-up will suffice).

Just open the file..```
sudo gedit /etc/rc.local
```
and add the 'rm /some/file/name' command before the 'exit 0'

---

### Post by schwabdale on 2010-04-09
I will post when I get it to work. Thanks

---

### Post by xhalarin on 2010-04-09
As a best practice, you should use gksudo instead of sudo whenever launching a program that operates with a graphical user interface:

[http://ubuntuforums.org/showthread.php?t=1419876&highlight=gksudo](http://ubuntuforums.org/showthread.php?t=1419876&highlight=gksudo)

```
gksudo gedit /etc/rc.local
```

---

