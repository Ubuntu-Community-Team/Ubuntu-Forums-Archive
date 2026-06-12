---
title: "Ctrl+Alt+F1 doesn't open a new shell"
date: 2009-09-19
forum: General Help
---

### Post by amitst on 2009-09-19
Since past few days Ctrl+Alt+F1-10 doesn't open a new shell (within X-server). The monitor switches off to power saving mode. How to overcome this issue?

---

### Post by Switch08 on 2009-09-19
system, preferences, keyboard shortcuts

---

### Post by prshah on 2009-09-19
> **amitst said:**
> Since past few days Ctrl+Alt+F1-10 doesn't open a new shell (within X-server). The monitor switches off to power saving mode. How to overcome this issue?

If the monitor is "switching off" when you change the mode, it is probably because it cannot handle a particular refresh rate for the text mode. You can change this default mode by specifying it as a kernel parameter.

To find the correct kernel parameter, add the kernel option "vga=ask" to the end of the kernel boot line during the grub bootup screen. (Post back if you want more details on this.)

This will give you a list of modes usable in text mode. Choose a suitable mode and see if it solves your problem, otherwise reboot and then select another mode.

Apparently you can also use something called "boot up manager" (?) to do this; I don't have specific knowledge about this and cannot advise more details.

---

### Post by amitst on 2009-09-20
Great! I can now open new shells with Ctrl+Alt+F1. I added a vga=0x318 parameter (in /boot/grub/menu.lst) and it started working. My X server resolution is 1440x900 and the vga=ask param didn't listed this resolution.

One minor change I have noticed is that the initial Ubuntu progressbar image is shifted a bit towards right (instead of appearing in the center).

Thanks for the help PRShah!:P

---

### Post by P4man on 2009-09-20
> **amitst said:**
> 
One minor change I have noticed is that the initial Ubuntu progressbar image is shifted a bit towards right (instead of appearing in the center).


The splash screen uses a different resolution and graphics mode. You need to press the "auto" button on your monitor to calibrate it, but its possible it doesn't have enough time to do so. It was like that on my machine. I had to make the boot pause to give my monitor enough time to adjust after pressing "auto", then it saves the settings, and all is well.

---

### Post by Mycen on 2012-09-08
> **prshah said:**
> If the monitor is "switching off" when you change the mode, it is probably because it cannot handle a particular refresh rate for the text mode. You can change this default mode by specifying it as a kernel parameter.

To find the correct kernel parameter, add the kernel option "vga=ask" to the end of the kernel boot line during the grub bootup screen. (Post back if you want more details on this.)

This will give you a list of modes usable in text mode. Choose a suitable mode and see if it solves your problem, otherwise reboot and then select another mode.

Apparently you can also use something called "boot up manager" (?) to do this; I don't have specific knowledge about this and cannot advise more details.

Hey there, I run 12.04 and I have exactly the same problem (monitor standby when swith to ctr-alt-F1, although sometimes it does work properly, and the next boot it's rubbish again). However, I don't know exactly what's meant by 'add to the end of the kernel boot line'. Is there a file I should edit? which one? I've looked for the mentioned /boot/grub/menu.lst, but there's no such file in the directory. I do have a video.lst there:
> vbe
vga
video_bochs
video_cirrus

Should i change the vga line to 'vga=ask'?
TIA!

---

### Post by oldos2er on 2012-09-08
Old thread closed, please don't bump old threads. If you have a question or problem, please start a new thread.

---

