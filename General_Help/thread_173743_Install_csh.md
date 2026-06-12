---
title: "Install csh"
date: 2006-05-10
forum: General Help
---

### Post by seth0x2b on 2006-05-10
Hey guys. I'm new to Ubuntu and I can't seem to install anything.
I tried "apt-get install csh" and it says it can't find it.Could it be that the repository does not have this old thing?
I also tried to install a new version of gaim, because Hoary uses 1.1.4, and the latest is 1.5.0, and it gives this:
```
seth@orion:~$ sudo apt-get install gaim
Reading package lists... Done
Building dependency tree... Done
gaim is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
seth@orion:~$

```

Is there a list of many repo's out there?

10x in advance

---

### Post by joft on 2006-05-11
Hi,

The webpage of the csh ubuntu package:
[http://packages.ubuntu.com/breezy/shells/csh](http://packages.ubuntu.com/breezy/shells/csh)
says, that it is in universe (repository). So you might have to update your /etc/apt/sources.list file. Add another line like:
```
deb http://archive.ubuntu.com/ubuntu breezy universe
```
and then do
```
sudo apt-get update
```

---

### Post by seth0x2b on 2006-05-11
10x for the links.I managed to get csh after all. I needed to run Maya 7 for linux, and I got it installed, but no csh(wich is a must). I found that Hoary does come with tcsh, installed it, and now it works like a charm :)
Cheers

---

