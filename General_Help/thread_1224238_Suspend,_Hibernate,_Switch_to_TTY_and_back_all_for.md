---
title: "Suspend, Hibernate, Switch to TTY and back all force GDM restart"
date: 2009-07-27
forum: General Help
---

### Post by Forlornity on 2009-07-27
Running Jaunty 64 on a Lenovo x200t.
Every time I switch to a tty and back to X (with ctrl+alt+f1 then f7) I find myself back on the login screen, the same thing occurs when I hibernate or suspend.

Apart from this (and horrible battery life and acpid issues) Ubuntu's working perfectly.

TVMIA, Forlornity

---

### Post by Forlornity on 2009-07-28
Sorry to bump, but I'm rather puzzled about this one. Any ideas?

---

### Post by gdi2k on 2009-08-03
I have the same issue running Jaunty 64 on a Lenovo x200. 

However, I can switch to a tty and back without problems in general, and find that if I resume from suspend very shortly after suspending (within a minute or so), it resumes normally. Any longer though, and I end up back at gdm. 

[This bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/332347") may be related.

---

### Post by gdi2k on 2009-08-04
Another reason for this may be that you're running with UXA acceleration - did you follow the long thread about improving Intel graphics performance? It recommended the use of UXA. 

[**This page**]("https://wiki.ubuntu.com/X/UxaTesting") shows a number of x200 / x301 owners with broken suspend / resume resulting from UXA accel. 

If so, just comment out the line
```
Option          "AccelMethod"                   "uxa"
```
in your xorg.conf file and things may improve.

---

### Post by Forlornity on 2009-08-18
There was no uxa line in my xorg.conf, so I assume it's not enabled.
Trouble occurs every time, even if I resume immediately after suspend or hibernate is finished. And it happens on switch from TTY of course.

---

### Post by gdi2k on 2009-09-02
I solved all my issues by moving to Intel's latest [2.80 driver release]("http://lists.freedesktop.org/archives/xorg/2009-July/046534.html").

Karmic will include this new driver by default, but if you'd rather not wait until October, you can grab it from this PPA: 
[https://launchpad.net/~morgwai/+archive/jaunty-backports](https://launchpad.net/~morgwai/+archive/jaunty-backports)

Note that I also run the latest 2.31 RC kernel from here: 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

This may be a prerequisite to running the latest Intel driver successfully (the release announcement says "The driver certainly will work best with an i915 module from a recent kernel (2.6.31)"). 

Works fine for me, but you may just want to wait for Karmic if it's all too much of a faff for you.

---

