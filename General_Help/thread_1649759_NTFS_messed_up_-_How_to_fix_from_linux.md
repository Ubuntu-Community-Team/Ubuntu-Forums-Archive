---
title: "NTFS messed up - How to fix from linux?"
date: 2010-12-20
forum: General Help
---

### Post by searchfgold6789 on 2010-12-20
Hi,
I've recently acquired an old Dell laptop. Which is fine with me, except that no one seems to know any of the Windows passwords... I planned on installing Debris Linux onto it, but GParted will not let me resize the Windows partition (which takes up all of the space on the diminutive 30GB hard disk) because the file system is all corrupt. I cannot check the file system, because when I boot into the Windows XP CD, it asks me for the Administrator Password, which I do not know. I cannot force-mount the partition, copy the files to some external source, delete and replace the file system, copy them back, and then FIXMBR because I do not know if that would work, and besides I do not know the password for the Administrator for the WinXP CD. (would it work? do I need to FIXMBR?)
And I don't want to delete Windows entirely, but I wish it were that simple, beleive me!
So, my only options left are:

[LIST]
[*]Somehow CHKDSK /p from within a Live CD
[*]Somehow make GParted ignore the broken file system
[*]Somehow hack the Administrator password
[*]Use a partition editor that ignores the broken file system
[/LIST]
Does anyone know how I could go about doing any one of these? Is there an other option I did not list?
Thank you so much,
 - He-who-is-tired-of-using-the-Live-CD (search)

---

### Post by calavier62 on 2010-12-20
It might not be the FS that is corrupted, but the hard drive surface itself. If GParted doesn't allow you to do something, it usually means that the hard drive itself is basically toast. 

I would recommend you use SpinRite (you can get it for free from numerous different *cough* sources *cough*); or that you find a hard drive wiping utility that is bootable.

---

### Post by ezsit on 2010-12-20
Boot from a live CD, like the Ubuntu or gparted CDs. Open a terminal and at the command prompt, type:

sudo cfdisk

and press enter. The cfdisk program is a wonderful command line program for partitioning. Once in cfdisk, you should be able to delete the partitions and create new partitions. Be sure to Write your changes to disk before you exit.

---

### Post by 73ckn797 on 2010-12-20
When you boot with the Windows CD you usually do not need a password, at least to use the disk for recovery/repair mode. Did you try using "admin" for the password?

You said the partition uses all 30GiB. Is the drive completely full with data? A resize will not work if the disk is full.

This all may not work but I suggest it anyway.

---

### Post by searchfgold6789 on 2010-12-20
The partition is half full, not the disk :P
I am still able to force-mount it, plus boot into windows. I appreciate the help so far!
Is there any tool that will allow me to force the resizing of the partition?

---

### Post by leclerc65 on 2010-12-20
I use Gparted live CD without any restrictions you mentioned, Windows or Linux partitions.

---

### Post by Mark Phelps on 2010-12-21
Sorry, but the FACT of the matter is that there is NO Linux utility that can fix ALL the problems you might encounter with NTFS partitions.

While there is ntfsfix, it only fixes SOME of the problems.  In fact, from their MAN page:

> ntfsfix is a utility that fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk. It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows. 

There are times, and yours might be one of them, when the only way to actually fix an NTFX partition is to boot into MS Windows and run chkdsk.

---

### Post by searchfgold6789 on 2010-12-25
SOLVED: Apparently, GParted was not having a problem with NTFS being broken, but just couldn't read the partition. I installed ntfsprogs using synaptic and everything went just fine.

---

