---
title: "ms-sys 2.2.1 msgfmt: error while loading shared libraries"
date: 2012-01-22
forum: General Help
---

### Post by Kabroon on 2012-01-22
I came across this thread googling, which is basically the same problem I have:
[http://ubuntuforums.org/showthread.php?t=1689788](http://ubuntuforums.org/showthread.php?t=1689788)

He was running ubuntu 10.10. I have 10.04 32-bit

I'm trying to install ms-sys 2.2.1 but at the 'make' step it comes back with the following:


**The Problem is that ms-sys comes gets stuck in 'make'**
```
msgfmt: error while loading shared libraries: libgettextsrc-0.18.1.so: cannot open shared object file: No such file or directory
make: *** [mo/sv.mo] Error 127

```
and
**apt-cache search libgettext dev**
replies with

```
gettext - GNU Internationalization utilities
libgettext-ocaml-dev - OCaml internationalization library

```
someone also suggested to get libgblib2. I just tried it out of desperation but I have it already.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglib2.0-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

Any help to get ms-sys working would be greatly appreciated!

---

### Post by WorMzy on 2012-01-22
That library isn't available in Lucid. Try compiling an older version of ms-sys?

---

### Post by Kabroon on 2012-01-22
Thanks
So that's the problem. I went to the lowest possible version with win 7 mbr, but it comes back with the same error. So I need to find another way to get win 7 mbr onto usb -.-

---

### Post by tounteeundism on 2012-01-22
Thank you for the good writeup. It in fact was a amusement account it. Look advanced to far added agreeable from you! By the way, how can we communicate? [Houston garage doors](http://softwareforwebsite.com/hoteditor_forums/mybb_123/showthread.php?tid=423&pid=441453#pid441453)

---

### Post by Kabroon on 2012-01-23
> **tounteeundism said:**
> Thank you for the good writeup. It in fact was a amusement account it. Look advanced to far added agreeable from you! By the way, how can we communicate? [Houston garage doors]("http://softwareforwebsite.com/hoteditor_forums/mybb_123/showthread.php?tid=423&pid=441453#pid441453")

You can contact me via pm. And I'm glad at least someone enjoyed it :P

---

