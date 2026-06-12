---
title: "Two Hard Drives both with Ubuntu, what do I do?"
date: 2010-10-16
forum: General Help
---

### Post by jereece on 2010-10-16
The motherboard on my home built computer died so I bought a new one.  I also thought it had corrupted Ubuntu because I got an error message "Kernel Panic" several times before it failed. Since I thought I was going to have to reformat and reinstall Ubuntu, I figured I would go ahead and get a larger hard drive.  

On the old hard drive I had Ubuntu 10.4.  On the new drive I installed Ubuntu 10.10.  After installing the new board and drive and installing Ubuntu 10.10, I added the old drive with the intension of using it as a slave.  So I plugged it into the SATA2 slot. When I booted up my computer however, it booted from the old drive, not the new one.  If the new drive is in SATA1 and the old one is in SATA2, why would it boot from SATA2?  

So now comes my delima.

1.  Do I try to move everything from the old drive to the new one and wipe the old one clean?
 - If I do this, I assume I can export my bookmarks from Chrome and emails from Evolution. I don't know if I can export and import my tasks from Osmo however. 

OR

2.  Do I just keep the old drive as the OS and use the new one as a slave to keep the data on?  Then upgrade to 10.10.

Any thoughts on this is appreciated.

Jim

---

### Post by coffeecat on 2010-10-16
> **jereece said:**
> On the old hard drive I had Ubuntu 10.4.  On the new drive I installed Ubuntu 10.10.  After installing the new board and drive and installing Ubuntu 10.10, I added the old drive with the intension of using it as a slave.  So I plugged it into the SATA2 slot. When I booted up my computer however, it booted from the old drive, not the new one.  If the new drive is in SATA1 and the old one is in SATA2, why would it boot from SATA2? 

Have a look in the BIOS. It's probably set to boot from the drive in SATA2 which will still have grub stage 1 in the mbr looking for your 10.04 install. I had something similar. I put the bootup drive in SATA1, but when I tried booting up the re-assembled machine it tried to boot from SATA3. Goodness knows why. Soon fixed with some BIOS changes though.

---

### Post by sikander3786 on 2010-10-16
You can always select whatever drive you want to boot from the Bios menu.

Not a good idea to move all the data from one drive to the other. No benefit.

---

### Post by jereece on 2010-10-16
> Not a good idea to move all the data from one drive to the other. No benefit.

My thought were that if I keep the OS on one drive and the data (files, photos, etc.) on the second drive if the OS ever became corrupt (like my kernel panic issue) it would not affect the data on the second drive.  

I appreciate the dialog.  

Jim

---

### Post by sikander3786 on 2010-10-16
> if I keep the OS on one drive and the data (files, photos, etc.) on the second drive

If that is the case, I'll recommend it. If you don't have a second hard disk, a separate partition does the job there. You can mount your /home on a separate partition and keep all your data and configuration in case of a reinstall.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

