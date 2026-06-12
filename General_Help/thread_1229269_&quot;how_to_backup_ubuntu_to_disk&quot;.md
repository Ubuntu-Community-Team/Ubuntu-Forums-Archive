---
title: "&quot;how to backup ubuntu to disk&quot;"
date: 2009-08-01
forum: General Help
---

### Post by davewickett on 2009-08-01
I have ubuntu 9.04 and vista daul-boot on my c drive.i want to extend ubuntu's partition and I have to delete two partitions so I am scared I could lose some stuff or even worse everything on my computer.so what i need help with is how to back up my computer,do I back up ubuntu or do I back up ubuntu and vista together,also what happens about my grub??.Also I want to backup to disk not hard drive because of messing with my partitions.any help would be greatly apprciated thankyou......

:confused::confused::confused:

---

### Post by shp on 2009-08-01
You'll need another computer or a portable hard drive to copy the disk to if you want to backup the entire disk.
If you want to just backup the files just log into each os and copy your important files to the disks.

BTW in my personal experience the partition managers do not usually screw up your disk.

---

### Post by lisati on 2009-08-01
> **davewickett said:**
> I HAVE UBUNTU 9.04 AND VISTA DAUL-BOOT ON MY C DRIVE.I WANT TO EXTEND UBUNTU'S PARTITION AND I HAVE TO DELETE TWO PARTITIONS SO I AM SCARED I COULD LOSE SOME STUFF OR EVEN WORSE EVERYTHING ON MY COMPUTER.SO WHAT I NEED HELP WITH IS HOW TO BACK UP MY COMPUTER,DO I BACK UP UBUNTU OR DO I BACK UP UBUNTU AND VISTA TOGETHER,ALSO WHAT HAPPENS ABOUT MY GRUB??.ALSO I WANT TO BACKUP TO DISK NOT HARD DRIVE BECAUSE OF MESSING WITH MY PARTITIONS.ANY HELP WOULD BE GREATLY APPRCIATED THANKYOU......

P.S I ALSO HAVE A D DRIVE WITH HP RECOVERY ON. THANKS AGAIN ALL:confused::confused::confused:

Ow my poor eyes! No need to shout! (It's bad form to type in ALL CAPITALS unless there's something wrong with your system that prevents you typing normally)

---

### Post by adamitj on 2009-08-01
> **shp said:**
> You'll need another computer or a portable hard drive to copy the disk to if you want to backup the entire disk.
If you want to just backup the files just log into each os and copy your important files to the disks.

BTW in my personal experience the partition managers do not usually screw up your disk.

Interesting...
I have an external USB disk with 250 GB. My notebook's hd is 160 GB. Assuming my external disk is formated as NTFS, what should I do to make an image backup file of my partitions?

---

### Post by shp on 2009-08-01
> **adamitj said:**
> Interesting...
I have an external USB disk with 250 GB. My notebook's hd is 160 GB. Assuming my external disk is formated as NTFS, what should I do to make an image backup file of my partitions?

Yeah sure why not.
[http://clonezilla.org/](http://clonezilla.org/)

I used it instead to backup to an ssh server but apparently works for external drives.

---

### Post by prshah on 2009-08-01
> **davewickett said:**
> I WANT TO BACKUP TO DISK NOT HARD DRIVE BECAUSE OF MESSING WITH MY PARTITIONS.

Find full details here:[[SOLVED] Exact duplicate of entire HDD]("http://ubuntuforums.org/showthread.php?t=874643")

---

### Post by davewickett on 2009-08-02
> **shp said:**
> You'll need another computer or a portable hard drive to copy the disk to if you want to backup the entire disk.
If you want to just backup the files just log into each os and copy your important files to the disks.

BTW in my personal experience the partition managers do not usually screw up your disk.

And i do have a portable drive that is 250gb 
Its ok i have just under 10 gb on my d drive with my recovery on it. So i want to do is put something on it like damn small linux on it .And with my c drive that as Ubuntu & Vista on i want to just give that all to Ubuntu.What would i do install the new os on my d drive first then wipe out Vista with Gparted iso 
thanks, And would this be a bad thing doing this as i just need something like that on my d drive so i can still get on the net just incase things go wrong 1 day with Ubuntu.

---

