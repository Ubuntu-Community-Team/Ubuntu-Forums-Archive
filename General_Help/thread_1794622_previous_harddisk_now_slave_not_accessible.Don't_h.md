---
title: "previous harddisk now slave not accessible.Don't have permission"
date: 2011-07-01
forum: General Help
---

### Post by okkie on 2011-07-01
when I upgraded to 10.04 I bought a new hard disk and installed my system on it.I made my old hard disk my slave.I can however not access it as I do not have permission.My computer shows the slave disk as new volume and my new hard disk as 'file system'.My problem is I have a lot of information on the old disk which I need to transfer to the new disk among which all my music files.I think this has to do with repartitioning of the old disk but I lack the knowledge.
Any help will be much appreciated,thanks.

---

### Post by pawhtiobo on 2011-07-01
Hi,

Has i can understand, the old HDD also have an installation of Ubuntu on it? which filesystem is he using?

see ya...

---

### Post by okkie on 2011-07-02
Thanks for coming back.Yes it has afull system installed which gave me so many problems I reinstalled on a new hard drive.

---

### Post by okkie on 2011-07-02
If I click on the icon it opens lost+found and if I click on that it tells me I don't have permission to open.

---

### Post by wildmanne39 on 2011-07-02
> **okkie said:**
> If I click on the icon it opens lost+found and if I click on that it tells me I don't have permission to open.Hi, there is a couple of ways to do this, I do not know what file system you have so I will have to give you links for ubuntu and windows systems.
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
the way to mount ubuntu file system is
```
sudo chown -R username:username /media/storage

```
this command is run in a terminal. Where media/storage is is the path to your drive, it will be media/whaterver you named you files, and you will use the syntax of/media/storage as an example.

---

### Post by okkie on 2011-07-03
I am trying bit by bit.This is what I got so far.okkie@mealone:~$ sudo chown -R okkie:okkie /media/NewVolume 
chown: cannot access `/media/NewVolume': No such file or directory
okkie@mealone:~$ 
NewVolume is what the computer called the slave disk automatically.To make any changes to the slave disk with a full ubuntu 10.04 installation,I will have to get into it.If I click the icon it gives me lost+found.
Please give me an example  of a command line I must put into the terminal.

---

