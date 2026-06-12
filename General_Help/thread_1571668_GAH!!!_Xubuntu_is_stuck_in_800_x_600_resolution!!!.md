---
title: "GAH!!! Xubuntu is stuck in 800 x 600 resolution!!! Help!"
date: 2010-09-09
forum: General Help
---

### Post by nmbluerock on 2010-09-09
Hey guys,

So yeah I decided to try and install Xubuntu on my old laptop that was previously installed with Windows 98. At first everything was fine but once it was installed I could not figure out how to change the resolution anywhere above 800 x 600. My monitor is a 1024 by 768 so i know something was up. I tried looking at forums but none of the suggestions seemed to work. Please help.

Oh and btw. As much as I love to use Ubuntu and its varients. I am extremely illiterate to code. If you give me instructions I can follow them, of what to type in but I need in depth help on this one.

---

### Post by bodhi.zazen on 2010-09-10
What video card are you using ?

---

### Post by nmbluerock on 2010-09-10
I believe its a Trident XP

---

### Post by MacinViLLe on 2010-09-10
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=289039&page=2](http://ubuntuforums.org/showthread.php?t=289039&page=2)


And this:

[http://www.linuxforums.org/forum/ubuntu-help/125771-xubuntu-screen-resolution.html](http://www.linuxforums.org/forum/ubuntu-help/125771-xubuntu-screen-resolution.html)

---

### Post by nmbluerock on 2010-09-10
I am using Xubuntu 10.04 LTS. I got through the first part but the

grep -i driver /etc/x11/xorg.conf

came up with "No such file or directory"

---

### Post by bodhi.zazen on 2010-09-10
> **nmbluerock said:**
> I am using Xubuntu 10.04 LTS. I got through the first part but the

grep -i driver /etc/x11/xorg.conf

came up with "No such file or directory"

That is because xorg.conf is depreciated, it is an empty file by default. You can write a configuration file and save it in /etc/X11/xorg.conf if you wish, see the links for advice.

---

