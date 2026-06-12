---
title: "Computer boots and displays initramfs"
date: 2012-05-04
forum: General Help
---

### Post by artti on 2012-05-04
I have a problem.

Computer boots and then displays BusyBox 1.1.17 and initramfs. I have tried to find some solutions, but nothing so far. I don´t have cd-reader, but I could boot from usb, which I have tried, but Puppy Linux loads stuff and then freezes with a black screen. I tried damn small linux, which doesn´t get far also, after hitting enter it freezes.

Grub is 1.99

Also I have Ubuntu Rescue Remix 12.04, but I guess that might not work for ubuntu from previous year. And universal usb installer 1.8.9.4 can´t make it on the usb. So currently I`m downloading older remix to give a try.

Could anyone guide me somehow?

Thanks in advance!

---

### Post by carl4926 on 2012-05-04
If you can't boot a live USB (which you could formerly), then I'd suspect something more or less terminal.

---

### Post by *^kyfds( on 2012-05-04
it might possibly be a hardware problem, but i'm not entirely sure as i'm not so great with the really complex linux bootloader stuff.

hardware specs?

---

### Post by artti on 2012-05-04
Damn Small Linux I could now load with failsafe option, but it results with error: Knoppix filesystem not found. Dropping to limited shell.

Freedom Zoostorm 10-270 Netbook
·         Intel Atom n270 1.6Ghz Processor
·         1GB DDR2 533Mhz Memory (Option of 1GB upgrade to 2GB)

---

### Post by carl4926 on 2012-05-04
You need to tell us if these were bootable before and that you can confirm they boot on another machine.

---

### Post by artti on 2012-05-04
I tried samsung nc10 and Puppy Linux booted nicely there. Is there anything I could do at initramfs or something or console?

---

### Post by electrojustin on 2012-05-04
Sounds like something broke at or below the kernel level if you're in busybox. Can you drop into a root shell using the "(recovery)" grub entry?

---

### Post by artti on 2012-05-05
Hmm... how can I get into root shell using the recovery grub entry?

Is it one when there is boot options, like ubuntu, ubuntu recovery and memory test and there is option to hit c which would bring up grub console. I can get there, but I have no clue what to do there.

Could I use memorytest somehow to see if it´s hardware problem?

---

### Post by artti on 2012-05-05
Wow... I don´t know, I just choose c to edit boot options( from menu where you can choose ubuntu and ubuntu recovery) and then I just exit and it started normally. Crazy. Now I have to back up stuff quickly and see what I could do. Any recommendations.

---

