---
title: "Input/Output Error"
date: 2010-05-14
forum: General Help
---

### Post by ut1988 on 2010-05-14
I have a computer with Windows XP, but have had problems and so am using a liveCD to install Ubuntu 10.4. When I tried installing the OS, it came up with a message saying write error: input/output error. Looking online, it seems to be a corrupt HD or something, so I have tried using the sudo wipe and sudo shred commands in Terminal to wipe the drive and try an install again. However, the same input/output error message comes up each time! Any ideas on how to solve this? Thanks so much.

---

### Post by ut1988 on 2010-05-14
As a follow up, I have restarted the computer, the disk was written on slow speed. Could it be a physical problem with the hard drive? Or can I solve it somehow?

---

### Post by ut1988 on 2010-05-14
Any ideas?

---

### Post by efflandt on 2010-05-14
Does the end of **dmesg** (typed in a terminal) give any more of a clue (or **dmesg | less** to make it easier to scroll through with cursors, pgup/pgdn, q to quit less)?

It could either be a problem with the hard drive (bad sectore? especially since XP has been glitching), or that your system (some Asus motherboards in particular) does not like the new partition alignment.  One of my computers with Asus mobo does not like the new partition alignment (HP a530n from 2004), but works with **partman/alignment=cylinder** kernel parameter.

See [http://www.ubuntu.com/getubuntu/releasenotes/1004#Partition%20alignment%20changes%20may%20break%20some%20systems](http://www.ubuntu.com/getubuntu/releasenotes/1004#Partition%20alignment%20changes%20may%20break%20some%20systems)

But if a drive has bad sectors, in some cases it may be  difficult to partition.  Normally a drive internally maps out bad  sectors, but if it runs out of error map sites and you start seen bad sectors,  that is a bad sign.

---

### Post by ut1988 on 2010-05-15
I am not looking to partition the drive or anything, just install Ubuntu. Would removing the partitions possibly help?

---

