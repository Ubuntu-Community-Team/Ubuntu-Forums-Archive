---
title: "Grub not found - Trying to recover grub after windows 7 install"
date: 2010-08-24
forum: General Help
---

### Post by zbirdman777 on 2010-08-24
I had to dual boot my computer again with windows unfortunately for school. This is something I've dealt with dozens of times in the past but when I try to recover grub 2 with the ubuntu live cd I get this:

sudo grub
sudo: grub: command not found

I can't seem to update grub or edit it like described in the 100s of guides on here. I don't know why this problem is coming up when I never had issues in the past with grub 2.

---

### Post by drs305 on 2010-08-24
Are you thinking of "sudo update-grub"?  

This is the command normally used to try to locate Windows if G2 doesn't find it the first time or to update the Grub2 menu when something has changed. Or are you having problems during the initial boot?

You can also look at this thread on restoring the other OS after a reinstall if it isn't booting at all. It explains how to recover Ubuntu or various Windows installs, depending on which one you lost after a subsequent install.

[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by tylerdurdin on 2010-08-24
this worked for me scroll to the bottom 

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by zbirdman777 on 2010-08-24
Your post worked drs305. Thank you for the fast help. You too Mr.Brad Pitt.

---

### Post by jdeal on 2011-02-27
drs305 your a savior!  I spent hours looking for the grub program on my mounted (but not booting) 10.04 install, 9.10, 10.04, and 10.10 liveCDs (all 64-bit) and never found it.  Your linked solution worked like a charm!  Thank YOU!:)

---

