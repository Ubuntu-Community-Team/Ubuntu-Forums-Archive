---
title: "GRUB Error: Couldn't commit pageflip"
date: 2012-08-31
forum: General Help
---

### Post by Jolladay on 2012-08-31
Hello,

I am using 11.10 and when I try to boot, before it gets to GRUB, it gives an error, "Error: Couldn't commit pageflip."

It stays on this screen and won't boot.

Does anyone know how to fix this?

Thanks!

-Jolladay

---

### Post by Jolladay on 2012-09-05
Does anyone know how to solve this?

-Jolladay

---

### Post by Jolladay on 2012-09-05
Bump Sorry! X( I can't find how to fix this anywhere, I'm hoping someone knows what this error means.

-Jolladay

---

### Post by oldfred on 2012-09-05
I have not seen that from grub??

Is it perhaps from BIOS? Nevermind it looks like a video error.

[http://www.mail-archive.com/grub-devel@gnu.org/msg12529.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12529.html)

Did system work before and have you changed anything in BIOS or video driver?

Grub relies on basic video but then tries to convert to video on system.

You may be able to change a video setting for grub with grub customizer.

HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)

---

### Post by Jolladay on 2012-09-05
The drive boots fine on other systems with different video cards. I set "nomodeset" in the grub config file but that doesn't seem to help. Is there a way to turn off double buffering? From your link it seems that that might be causing the issue.

-Jolladay

---

### Post by oldfred on 2012-09-05
Unless you do a grub update in your install changing the grub config file will not change boot. 

Are you able to get to menu before the error? Hold shift key from BIOS until menu if only one system.

---

### Post by Jolladay on 2012-09-05
After updating the grub file, I do a grub-update. It gives me the error before getting to the GRUB menu. Holding shift doesn't do anything.

---

### Post by oldfred on 2012-09-05
Did you try grub customizer?

You might just try the lowest level  of 640x480 and see if that works.

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)

(I am grasping at straws as I do not have a good solution. )

---

### Post by Jolladay on 2012-09-05
I have tried different resolutions. The resolution seems to be fine. It is strange. Sometimes if I poweroff the machine and the power it up, it goes to the grub menu just fine. Others times, it gets stuck just before the grub menu and displays error: unable to commit pageflip

---

### Post by oldfred on 2012-09-05
Does it make a difference between cold boot (total power down for several minutes) and a warm boot (reboot) ?

---

### Post by zumost on 2013-06-04
I ran into this same issue and this seems to be the only forum place talking about it.

It turns out this happened to me when I set the timeout in /etc/default/grub to equal to 0. I was able to load to a live disk and change grub.cfg in the boot partition so that the timeout was greater then 0. This fixed the commit pageflip error.

---

