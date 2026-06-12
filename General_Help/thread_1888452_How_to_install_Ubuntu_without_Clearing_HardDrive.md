---
title: "How to install Ubuntu without Clearing HardDrive"
date: 2011-11-29
forum: General Help
---

### Post by tears of the river on 2011-11-29
[SIZE="2"][FONT="Verdana"]Ive convinced a freind to replace his windows 7 with Ubuntu however He has 500 GB of important information which he will be unable to make back ups of so can someone plz give a viable solution (Not Dual boot plz coz **keeping windows is not an option**) to the problem that is there any way to install ubuntu without deleting the whole hard drive
preferably a way to install ubuntu onto c drive while replacing windows


p.s. if you do a dual boot will you be able to view the files and folders under the other drives like c,d,e drives of windows???[/FONT][/SIZE]

---

### Post by searchfgold6789 on 2011-11-29
Yes, you'll be able to see all of the Windows files and folders, and open and make changes. If you installed Ubuntu alongside Windows, then you'd be given an option at startup to either start Ubuntu or windows, but ubuntu will be selected by default. And you can hide this boot menu as well so it boots straight to Ubuntu.
 - search

---

### Post by oldfred on 2011-11-29
You really need backups. And you should keep a DVD set of the windows recovery, so you do have a way to go back. And many find one application they cannot live without and have to dual boot. It took me 5 years to get off XP and the equivalent app in Linux is not as good, but I now find it good enough.

Only if the data is worthless do you not have a way to make backups. Systems fail. I have had two hard drives just stop working, one was relatively new. I have accidentally deleted data and had to have large amounts of space to recover. I have had power failures that corrupted data.

---

### Post by tears of the river on 2011-11-29
> **searchfgold6789 said:**
> Yes, you'll be able to see all of the Windows files and folders, and open and make changes. If you installed Ubuntu alongside Windows, then you'd be given an option at startup to either start Ubuntu or windows, but ubuntu will be selected by default. And you can hide this boot menu as well so it boots straight to Ubuntu.
 - search

SO if he dual boots windows and Ubuntu and after the dual boot is complete he formats the c drive i.e. uninstalls windows will that ensure that the data on the other drives is untouched and he only has Ubuntu on his system. It wont create any problems will it???

---

### Post by Mark Phelps on 2011-11-30
Let's get terms straight so we all know what we're discussing, OK?

Physical hard drives are "drives"; sections organized on those drives are called "partitions".

Windows is installed into one or two partitions.  If the PC came preloaded with Win7, then there are two partitions: a small (100MB or so) Win7 boot partition, and a larger Win7 OS partition.  The second one contains the OS programs, applications, and files. There may be other partitions as well, so open up the Disk Management utility in Win7 and see what is there.  If there are already four partitions, you will have to remove one to make room.

If you have no means for backup, and you do NOT want to dual-boot with Win7, my recommendation is to move the data you want to keep into Ubuntu, remove that data from Win7, then run the Win7 Disk Management utility, and shrink the Win7 OS partition as much as it will allow.

One approach is to shrink down Win7 and NOT migrate the data files out of the Win7 OS partition, but the problem with this, is that writing to the Win7 OS data partition from Ubuntu (presuming you ever want to CHANGE any of the data) is risky and could end up corrupting the Win7 OS filesystem -- then making the data files inaccessible.

The second alternative, moving the data files to Ubuntu, without an external drive, is going to be a long and tedious process, requiring that you mount the Win7 OS partition, copy some of the data files over to Ubuntu, then access the files in Ubuntu to confirm they are OK -- and continuing this until all the files are copied.  I mention copy instead of move, because if anything goes wrong when moving files, the originals can be lost.

After all the files are copied, if you want to recover the space used by the files in Win7, you will need to boot into Win7, remove the files, and use the Disk Management utility to shrink down the Win7 OS partition.  Then, to resize Ubuntu to use the new space, you will need to boot from an Ubuntu desktop CD (because you can't resize a partition while it is in use) and use Gparted to resize the Ubuntu partition.  Then, reboot back into Ubuntu.

To install Ubuntu, you will first need to boot into Win7 and use the Disk Management utility to look at the partitions.  IF there are already four of them, that is the maximum allowed, and you will have to remove one to allow the installer to create a new one for Ubuntu.  You will also probably have to shrink down the Win7 OS partition to make some room.  Use the Win7 Disk Management utility to do this.

---

