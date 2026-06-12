---
title: "Black Lines; Cannot see system monitor!"
date: 2010-02-04
forum: General Help
---

### Post by josepaul on 2010-02-04
Hi guys, whenever I open system monitor, I just get a loada black and white lines, I have no idea what this is, this never comes for any other application/program and it stops me from being able to kill non-responding processes, I know there is at least another way to do it, command line and all that but I am new and I'm not fully comfortable with command line so if you could tell me what is going on here, then it will be greatly appreciated ;)

I've attached a screen shot of the problem

Thanks for the help ;)

---

### Post by Iowan on 2010-02-04
I had [something]("http://ubuntuforums.org/showthread.php?t=289272") like that once - a few versions ago.

---

### Post by josepaul on 2010-02-05
> **Iowan said:**
> I had [something]("http://ubuntuforums.org/showthread.php?t=289272") like that once - a few versions ago.

Thanks man, I'll try that tonight

---

### Post by josepaul on 2010-02-08
Nope doesn't work, any other ideas anyone?

---

### Post by efflandt on 2010-02-08
What video device do you have (output from **sudo lspci -v** related to it) and how much video RAM does it have.  I have seen that on older video cards (system notifications were crosshatched too), but I lost track of a post somewhere with a possible solution.  If it is an older ATI card you might try xorg-driver-fglrx package.

---

### Post by josepaul on 2010-02-08
The video card is Radeon Mobility M6 LY 128mb, I haven't installed drivers or anything, its too old I think, but for my use for this very old machine (just a bit of word processing, mails and some movies). Does installing that driver solve the problem? If so, then I guess I can't do anything about it, btw this problem only started when I switched from janty to karmic... but thanks for the help anyway people :)

---

### Post by josepaul on 2010-03-14
Finally found the solution :); [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001")
[QUOTE=Jamal Fanaian]It turns out the issue is related to the new acceleration method in Karmic. Adding the following to the **Device section** fixes it.

Option "AccelMethod" "EXA"[/QUOTE]

---

