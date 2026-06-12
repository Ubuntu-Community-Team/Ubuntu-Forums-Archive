---
title: "Is it possible to reformat your hardrive?"
date: 2009-12-24
forum: General Help
---

### Post by Deathrow_cy on 2009-12-24
through ubuntu? My ubuntu is installed *inside* vista, is it possible to reformat my hardrive so everything, and absolutely _EVERYTHING_ is gone. 

My goal here is to make my pc brand new. Because vista is ****ing up on me, i have to use ubuntu. So yeah is it possible to delete all the data of this pc _from_ ubuntu?

-Cheers

---

### Post by oldos2er on 2009-12-24
You'll need to boot from a LiveCD, and assuming you want to install Ubuntu as your only OS, choose the installation option 'use entire disk'.

---

### Post by SuperSonic4 on 2009-12-24
Only through a live cd - but remember to back up important data

---

### Post by 3Miro on 2009-12-24
Backup anything worth backing up and then boot live CD. Install Ubuntu with either use the automatic option "use the entire disk" or manually reformat/repartition everything, just read up on that.

Auto option has failed for me on couple of occasions and it may render the computer temporarily unbootable. You can always boot with the live CD and work from there, read up on manual partition and make swap, / and /home partitions.

---

### Post by running_rabbit07 on 2009-12-24
> **3Miro said:**
> read up on manual partition and make swap, / and /home partitions.

Very good idea.

I would also suggest using the GParted LiveCD.

---

### Post by oldfred on 2009-12-24
One more for manual partitioning but you do have to have some understanding of partitions.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

---

### Post by Deathrow_cy on 2009-12-24
Ill give a little more detail to my problem, i wanted to reset my vista to brand new, so when i clicked reinstall and make new from the installation disk vista failed me and made a SECOND vista which doesn't even work. So now i have 3 operating systems (2 vistas that don't work and my good ol' trusty ubuntu). And because i was so pissed at the situation (for the lack of a better word) I decided to clear everything off my hard drive and install vista again. Problem is, i dont know how.

Anyway what your telling me is i need to order a ubuntu live cd so i can reformat?

P.S: I do not plan on backing up anything.

---

### Post by Mahngiel on 2009-12-24
just download the ubuntu version you would like to use as an .iso, and burn it to a disk. my karmic fits on one CD-R and has gparted on it.  just burn the disk, pop it in the drive, and restart. when you get the prompt menu at startup, choose to try Ubuntu. when it finishes loading, terminal "sudo gparted" and you can create a new partition table, which erases everything. from there, you can double click the icon on the desktop to install ubuntu. then enjoy being M$ free.

---

### Post by running_rabbit07 on 2009-12-24
> **Mahngiel said:**
> just download the ubuntu version you would like to use as an .iso, and burn it to a disk. my karmic fits on one CD-R and has gparted on it.  just burn the disk, pop it in the drive, and restart. when you get the prompt menu at startup, choose to try Ubuntu. when it finishes loading, terminal "sudo gparted" and you can create a new partition table, which erases everything. from there, you can double click the icon on the desktop to install ubuntu. then enjoy being M$ free.

Not that it really matters, but the GParted CD is much more thorough and from experience, works better.

---

