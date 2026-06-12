---
title: "Maverick: gparted crashes on startup in amd64 livecd"
date: 2010-10-10
forum: General Help
---

### Post by shaggy999 on 2010-10-10
So I just booted the 64-bit liveCD of Maverick and when I run gparted it crashes and the window disappears while scanning drives. I tried running it from console and got this:

```

$ gksudo gparted
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...


```

Any ideas?

---

### Post by jbroome on 2010-10-10
Does the same thing on a regular install too.


Linux x2 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux

dpkg -l | grep gparted
ii  gparted     0.6.2-1ubuntu1       GNOME partition editor


lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

---

### Post by shaggy999 on 2010-10-11
I found a related bug report:

[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885)

---

### Post by flavouride on 2010-10-31
> **shaggy999 said:**
> I found a related bug report:

[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885)

I've got the same problem, gksu or gksudo didn't help

I'm on maverick amd64 as well.

---

### Post by manco1911 on 2010-11-27
Hy guys, i just installed maverick, and im having the same issue. 
I get the same error when gparted tries to start. Just crashes for no obvious reason. 

Just for the record, im running amd64 from a **USB HDD.** 

_Tests_:

#sudo gparted    --> crash on startup
#sudo gparted /dev/sda   --> starts up OK, (im running from sdb)
                           did't tried anything, since im not on my computer. 

**DEFINITIVE SOLUTION:**

I read somewhere (i cant find the thread again.. and no, its not on the history, im not on the same computer), i will reference to the original autor if i find it again. 

We need to install gparted 0.7. 

Here you have a link to deb package straight from ubuntu:
[http://packages.ubuntu.com/natty/amd64/gparted/download]("http://packages.ubuntu.com/natty/amd64/gparted/download")

You can put it on your repositories list, i just downloaded the .deb file (right click "save link as.."   or wget [link]). 
And installed it from terminal:

#sudo dpkg -i gparted_0.7.deb

That's it !  It works now. 
[Edit:   Just tested it, it works 100% !!]


This is the first time i post a solution on the forums, so.. yey ! [http://ubuntuforums.org/images/icons/icon10.gif](http://ubuntuforums.org/images/icons/icon10.gif)

---

