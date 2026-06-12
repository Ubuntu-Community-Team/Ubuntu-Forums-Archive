---
title: "System Totally Crashed"
date: 2010-08-20
forum: General Help
---

### Post by Bre Ntt on 2010-08-20
Something way screwy happened to my system. 

I have been doing nothing but run-of-the-mill internet browsing today, havn't messed with any settings or installed any new software. 

I click on a link in Mozilla, and suddenly Mozilla vanishes from the screen and toolbar, leaving only my desktop, then a few seconds later the top and bottom toolbars on my desktop vanish, and finally a few seconds after that the two icons on my desktop vanish, leaving only my desktop picture and mouse cursor. 

So I restart my computer. It takes an unusual amount of time to go through the bios stuff, but doesn't boot, it just goes to a message that says the boot device isn't working.

I reboot again and get to the bios settings, but its on the CD, I tried to change it back to hardrive, but when I exit the bios its trying to boot from the cd again. 

So I'm guessing somethign happened to my hardrive. Because now I'm using the boot CD. But its hard to tell if its a hardware failure or a OS failure. Because of the way it crashed I'm thinking that it might be a software failure? Has anyone had an issue like this?

Oh, and in addition, when I installed from the boot disk intitially, it I got a message saying that there was an "unrecoverable error and we will now take you to the desktop environment so you can install from there". So it took me to the CD desktop, I didn't think anything of it because it installed fine and has been working for a while. 

Anyone know what hte problem could be?

---

### Post by TeoBigusGeekus on 2010-08-20
fsck your hard drive and post us the results.

---

### Post by Bre Ntt on 2010-08-20
OK, thanks for reading! 

Here is the result (including the command I used in case I didn't do it right):

=================================
ubuntu@ubuntu:/mnt/disk$ sudo e2fsck -fpC 0 /dev/sda1
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
===================================
Thats all it gave me...hmm maybe I didn't do it right.

---

### Post by Bre Ntt on 2010-08-20
Ok, I reinstalled but used an old 9.10 Karmic Koala CD instead, and everything installed perfectly and seems to be working splendidly.  

So I'm guessing it was an issue with 10.04?

hmm, I would like to use 10.04 though. Does anyone know what may have been causing the problem?

---

