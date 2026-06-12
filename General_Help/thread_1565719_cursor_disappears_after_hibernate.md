---
title: "cursor disappears after hibernate"
date: 2010-09-01
forum: General Help
---

### Post by wahoobob on 2010-09-01
I have had a strange problem crop up.  After installing Ubuntu Tweaks (that's about all I remember changing) the cursor disappears whenever I hibernate or suspend the laptop.  I am running 10.04.1 and have compiz running but changing to less effects seems to have no effect on this problem.  when I have no cursor the only thing I can do is restart and it reappears and does fine until I suspend or hibernate.  Any thoughts?.................

Some hours later -  I just found the setting that caused this.  The tweak has a box that was clicked to disable the touchpad while typing.  This caused the blank cursor when awakened.  working now.  this shouldn't happen, but I guess this is one to leave alone.

NEXT DAY!!!  Here we go again.  cursor disappears after suspend.  HELP!

---

### Post by wahoobob on 2010-09-02
bump, bump

---

### Post by DogMatix on 2010-09-03
Here is a launchpad bug report that seems to address your problem

[Bug Report Link]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/552058")

...and here is another Ubuntu Forums thread discussing similar issues [>> Here]("http://ubuntuforums.org/showthread.php?t=841087")

---

### Post by wahoobob on 2010-09-04
:rolleyes:> **DogMatix said:**
> Here is a launchpad bug report that seems to address your problem

[Bug Report Link]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/552058")

...and here is another Ubuntu Forums thread discussing similar issues [>> Here]("http://ubuntuforums.org/showthread.php?t=841087")

OK, great advice on these page.  the Fn + 7 key and changing desk tops both work.  This will make the problem small and I'll wait for the update that repairs the bug.  thanks:rolleyes: for the hlp.

---

