---
title: "Boot Failure After NVIDIA Proprietary Driver Install"
date: 2012-08-17
forum: General Help
---

### Post by jim_deadlock on 2012-08-17
I made the mistake of installing the proprietary NVIDIA driver which I downloaded from the website. Now I get the blank purple screen and I can't even load grub. I am able to boot from a live CD though. Any suggestions on how to remove the driver and/or access grub? I've tried holding shift to get grub, still get purple screen. Also tried deleting /etc/X11/xorg.conf after mounting main drive.

---

### Post by drs305 on 2012-08-17
The SHIFT feature should display the Grub menu. You can also repeatedly press the ESC button during boot when the SHIFT feature isn't enabled. There is a 3 second window so just try pressing it and see if you can get to the grub menu.

Once there, press 'e' to edit the Ubuntu entry. Cursor to the end of the 'linux' line and remove everything after "ro". Add "nomodeset" (no quotes) and press F10 or ctrl-x to boot.

This should take you to the Desktop, but since you have removed the X11 file I don't know if it's going to work or not. If it does, you can then add/remove the additional drivers to get your system working.

---

### Post by efflandt on 2012-08-17
12.04 seems to automatically install nvidia-current if installation senses that you have nvidia graphics.

Running the script from nvidia website probably messed that up and would make future kernel updates a pain because nvidia updates and kernel modules would no longer be automatic.  I don't know how you would fix that easier than reinstalling Ubuntu.

What video hardware do you have that you felt you needed something different than nvidia-current package?

---

### Post by jim_deadlock on 2012-08-17
Thanks drs305, I have my desktop back now.

> **efflandt said:**
> What video hardware do you have that you felt you needed something different than nvidia-current package?

Good question. I was trying to set up dual monitors but the 2nd monitor has a horrible green tint. It's not a problem with the monitor because on its own it displays fine. I should probably create a new thread for this problem though.

My card is a GeForce GTX 550 Ti.

---

