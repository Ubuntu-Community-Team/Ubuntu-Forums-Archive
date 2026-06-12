---
title: "Simple Backup Restore doesn't work"
date: 2011-05-16
forum: General Help
---

### Post by gunterb on 2011-05-16
Here's what I want to do: 
Copy the whole Ubuntu 10.04 partition/installation from my old laptop to the new one.

What I tried:
Used Simple backup to back up my Ubuntu installation to a USB hard drive. It yields a 10.4 gig folder containing 7 files. Installed 10.04 on the new laptop, used Synaptic to install Simple Backup, plugged in USB drive, started Simple Backup Restore, tagged the backup directory in Simple Backup Restore, and get the error:

Error: no backups found in the target directory.

I also tried copying the backup to the local drive, same difference.   

Help please

---

### Post by Mark Phelps on 2011-05-16
Would recommend you looking into using CloneZilla instead.  It will allow you to image off the entire partition and migrate that to another drive.

---

### Post by brunog on 2011-05-18
Hi Mark,
I have tried to follow your advice.
Current PC is old P4 and I want to migrate my Ubuntu partition to new PC.
Strage thing - when I create a USB clonezilla boot disk, it boots with the new PC and starts clonezilla live, but on the old PC it just says" Boot Error" and does not go further to running clonezilla  live.

Any advice?

Thanks

---

### Post by ntu on 2011-05-24
I have used gparted in a ubuntu live cd to copy from one hdd to another. It has a copy command. 

Edit: I note that gparted is not in the 10.4 live cd.

---

### Post by linuxinstalledfromhdd on 2011-05-24
remastersys works great for migrating an entire system setup. 

anything above the size of 4.7Gb would need to be manually saved to an external device. 

remastersys will create a live bootable rescue disc you can install to like architecture.

---

### Post by gunterb on 2011-05-24
Thanks for your suggestions. I'll check them out further on the weekend when I have plenty of time.

Cheers!

---

### Post by linuxinstalledfromhdd on 2011-05-24
Awesome..

---

### Post by gunterb on 2011-06-08
Thanks again for the suggestions.

I tried Clonezilla. It managed to corrupt the  bootloader in the new laptop (no menu, no OS, nada past POST), so I ended up re-installing UBUNTU, and had to fiddle making WINDOZE to boot again. So am now somewhat hesitant using a similarly dangerous scheme. Hence I still like the idea of a backup/restore program that works for partitions, or complete installations of UBUNTU.

---

