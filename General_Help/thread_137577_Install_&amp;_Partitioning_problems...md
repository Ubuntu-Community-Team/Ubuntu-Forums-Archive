---
title: "Install &amp; Partitioning problems.."
date: 2006-02-28
forum: General Help
---

### Post by reazn on 2006-02-28
I have 2 hdd's. 1 is a 200gb drive with windows xp on it. 

The other is a blank 80gb drive that i plan on putting ubuntu on. 

Except, when i go throu the installation process, i get to the partitioning section and i can't see my drives. 

> Configure software RAID
Configure the Logical Volume Manager
Guided partition (does nothing)
Help on partitioning

Undo changes to partitions
Finish and write changes to disk (does nothing - comes back to this screen)

I belive i'm supposed to be able to see my drives in a list here to choose from? I cant.

---

### Post by wrtrdood on 2006-02-28
Odd.  Yes, you should see a list of existing partitions on both drives.  Any chance these are SATA?  There's been trouble with some of them not showing up.  (Dapper might work, though...)

---

### Post by reazn on 2006-02-28
the 200gb drive is sata, the 80gb drive (the one i intend on using) is IDE. 

Dapper?

---

### Post by Bachstelze on 2006-02-28
Dapper is the codename for Ubuntu 6.04, to be released next April.

Try disabling your SATA drive in the BIOS, your IDE one should be detected then.

---

### Post by reazn on 2006-02-28
Ahh, ok.. Will try now, thanks.

---

### Post by reazn on 2006-02-28
still couldn't see the drives :/

---

### Post by soonindallas on 2006-02-28
your disk might be broken

---

### Post by reazn on 2006-02-28
my disk is fine, i can format & use it in windows, but when i go to use it in ubuntu installation, it wont let me go any further :(

---

### Post by reazn on 2006-03-01
I've tried disabling the sata drive in BIOS, even unplugging it.. still to no avail.. I cannot see either the SATA or the IDE drive.. 

Installed ubuntu on a spare pc i have, with a 20gb IDE drive, it picked it up fine... 

Any suggestions?

---

