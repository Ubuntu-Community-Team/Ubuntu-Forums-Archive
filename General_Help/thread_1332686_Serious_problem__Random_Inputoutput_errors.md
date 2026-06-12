---
title: "Serious problem:  Random Input/output errors"
date: 2009-11-20
forum: General Help
---

### Post by a person on 2009-11-20
Twice today I've had apps just close, and when I try to run anything I'll get an input/output error.  I'll then force a reset, boot into a livecd, fsck, and run SMART tests.  Fsck and the SMART tests all come up fine (after I boot again, everything runs fine - until this happens again).  I am being told this is an issue with Ubuntu's ext4.  Can anyone shed some light on this?

---

### Post by Giblet5 on 2009-11-20
Poke around in the logs.

~/.xsession-errors

/var/log/messages

/var/log/Xorg.0.log

Did you create adequate swap space when you installed? Run the "free" command: how much swap space do you have?

---

### Post by a person on 2009-11-20
I originally didn't create any swap (I have 4gb of ram and I've never used swap in the last couple of years [that is, until I ran Vista in VirtualBox]), I don't really need it as I don't use hibernate (never works for me anyways).  I just created an 8GB swap partition just in case.  I'll poke around in my logs and come back if I find anything of note.

---

### Post by stonebit on 2009-11-20
Run memtest. It's on the boot cds and you can also get it standalone: [http://www.memtest.org/](http://www.memtest.org/) . 

I had funky errors when i moved from windows to linux a little over a year ago. Strange things like apps closing and crashing to file corruption were happening at random intervals. After a month of head scratching, i finally tried memtest and BOOM - i had a bad memory module. I have 4 2GB modules. The errors were not detected when i ran the test with all 8GB installed, but when i tested each individually, the errors showed up rather quickly. Make sure and run each module for at least 24 hours (or until errors show up) to rule out a module.

It seemed that windows (was using Vista x64) had some error correction built into it, which prevented these errors from mucking things up in windows. I switched back and forth between win and lin and only got errors in linux.

Also, even if you don't ever use 100% of your RAM, always run a swap 1.5x larger than your RAM. Some programs just put stuff there that doesn't need to be accessed quickly, but doesn't need to be saved to non-volatile memory. I think a min swap is 1x RAM, but giving yourself a little head room will never hurt either. I rarely hit above 6GB RAM usage, but my swap usage fluctuates between 5-30% when i run a bunch of apps, especially virtual machines.

---

### Post by a person on 2009-11-21
It happened again, even with swap.  Fsck came clean and so did the smart tests.  I'll take some time and run memtest before I go out next.  I have been told this is a kernel issue with ext4, but I'm not entirely sure on that.

---

