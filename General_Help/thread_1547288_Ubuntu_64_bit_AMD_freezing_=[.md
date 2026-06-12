---
title: "Ubuntu 64 bit AMD freezing =["
date: 2010-08-06
forum: General Help
---

### Post by jinba.ittai on 2010-08-06
Specs
AMD Dual core Athlon II
6 Gb DDR2 
Nvidia GT 260
450PSU


Dual boot with windows 7
Two different physical hard drives for each OS



So i figured id intsall 64 bit on my new system to take advantage of the 6 gb of ram. During the install it froze once, restarted and installed again erasing the whole HD for ubuntu. Now everytime i boot into ubuntu, a few minutes after using firefox or even installing updates it completely freezes on me. I can move the mouse but no keyboard keys are recognized and no windows can move, nor open and programs.


Figured id post this before i go back down to 32 bit. I really needed 64 bit for the work that i do on linux, but i guess ill need to find another way to get a 64 bit distro working. Unless someone can help me =]

---

### Post by davidmohammed on 2010-08-06
freezes can be due to many issues - most that I've seen are due to graphics.

Since you have a nvidia graphics card, can I suggest you boot with "nomodeset" in your grub boot string

i.e. reboot - press shift to display your grub.  Press e to edit.

find the line with "...quiet splash -- " and change it to read "... nomodeset quiet splash -- "

CTRL + X to boot.

---

### Post by jinba.ittai on 2010-08-06
hmm, what if, i connected the vga to the onboard card, then installed nvidia shiz to get the card working properly? Think that might help? it does show the screen offset, leaves a black space in th eleft side. ima try that, then if that doesnt work illt ry what you told me.

---

### Post by jinba.ittai on 2010-08-06
All fixed, managed to get the drivers installed for the video card and everything works perfectly now!

Now, how to change this thread to solved?

---

### Post by slooksterpsv on 2010-08-06
> **Sandy V Jina said:**
> All fixed, managed to get the drivers installed for the video card and everything works perfectly now!

Now, how to change this thread to solved?

At the top of this Thread is a link that says Thread Tools, drop it down and mark it as solved.

---

### Post by jinba.ittai on 2010-08-06
> **slooksterpsv said:**
> At the top of this Thread is a link that says Thread Tools, drop it down and mark it as solved.


Thanks!

---

