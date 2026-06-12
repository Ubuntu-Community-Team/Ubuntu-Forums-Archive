---
title: "Ubuntu 9.10 boot error (may be graphics)"
date: 2009-11-03
forum: General Help
---

### Post by apurvas84 on 2009-11-03
I installed Ubuntu 9.10 3 days back and things worked fine. I have dual boot setup and GRUB loads properly.

Yesterday, I tried upgrading the proprietary nVIDIA 3D graphics drivers from 173 to 185 (recommended). The installation failed and I didn't think much of it. 

When I booted into Ubuntu later, I got a flashing screen asking for my login. This was in the command prompt. So the graphical interface did not show up.

When I try typing, it sometimes recognizes the keystroke and sometimes does not. So, entering my password is impossible.

I am a novice about all things Linux so any help will be greatly appreciated.

Thanks

---

### Post by ranch hand on 2009-11-03
Do you have a LiveCD?

---

### Post by apurvas84 on 2009-11-04
Yes, I do have a live CD. I just have the CD that I burned from the ISO. I guess it doubles up as a live cd too.

---

### Post by ranch hand on 2009-11-04
Well, I think you are going to have to chroot into your system from the LiveCD to straighten this out.

If your install failed on the video driver but got far enough to create a /etc/X11/xorg.conf file, that has probably become the problem.  9.10, by default, does not have this file.  If you need it, then it is generated.

I think that your problem is the OS is looking for that driver and not finding it and so you are hosed.

Removing that file should fix the problem.

First, fire up your LiveCD and boot to the desktop on it (first option on the menu).  Go to places and you should see your installed OS in the left column.  See if that file is there before we go off hlf  cocked.

---

### Post by apurvas84 on 2009-11-04
Thank you, thank you!
I booted in the recovery mode and deleted the file from there. 
Restarted and the computer worked. However my previous nvidia drivers were gone (ver 173).

Tried reinstalling and somehow got things to work. 

Thanks a lot again! :p

---

