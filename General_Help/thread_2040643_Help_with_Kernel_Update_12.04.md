---
title: "Help with Kernel Update 12.04"
date: 2012-08-11
forum: General Help
---

### Post by strange_cathect on 2012-08-11
A few days ago during a system update, something went wrong. I got an error message that said I could only do a "partial upgrade." I was not upgrading to a new version of Ubuntu. I assume this was a kernal upgrade of some kind?

Since that time, when I boot up, I have to choose the kernel I want to use in Grub. I need help fixing this so I can return to a normal boot.

My current kernel version is 3.2.0-29-generic-pae. Is this the current version? 

Can I reinstall it easily or upgrade somehow?

Thanks.

---

### Post by Sidewinder1 on 2012-08-11
3.2.0-29-generic-pae is in fact the current kernel. I'm not really sure what you mean by a "normal boot". I have always (since 2007), been presented with a kernel selection page upon boot; that may be because all of my machines are true dual boot (with win xp I'm somewhat ashamed to admit). So the selection page is totally normal. If no input from you, it should automatically boot into 3.2.0-29 after approximately 10 seconds.
I can't address the "partial upgrade" problem without further info. Did it list any packages which could not be upgraded?
You might also want to change your profile here, to list Precise in lieu of Maverick. :-)

HTH,
Side

---

### Post by strange_cathect on 2012-08-11
I never have that choice, upon boot I got straight to the login screen. I just updated my grub. That seems to have cleared things.

---

### Post by Sidewinder1 on 2012-08-13
Congrats! I'm glad that you got it fixed. You may wish to mark the thread as "solved."
:-)

---

