---
title: "harddrive check failed!!!!"
date: 2009-08-30
forum: General Help
---

### Post by colinireland on 2009-08-30
Hey,

I am running ubuntu 9.04 and when ever I boot up and get the scheduled filesystem check I get an error. sda3 is my /home partition. The system seems to be running fine if i just skip this disk check. sda1 has no errors. Can anyone tell me how I can fix this. I dont have a clue how to manually fix this. Im sort of afraid I will make a balls of it and loose all my data. Here are the errors that were produced.

Thanks,
Colin



unclean shutdown, checking drives:
/dev/sda3

Checking drive /dev/sda3: 67% (stage 1/5, 1814/1886)
Error reading block 61371369 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 14860312

/dev/sda3: UNEXPECTED INCONSISTENCY; run fsck manually
(i.e. without -a or -p options)
fsck died with exit status 4

* File system check failed                               [Fail]
A log has being saved in /var/log/fsck/checkfs if that location is writeable. Please repair the filesystem manually.

* A maintenance shell will now be started
Control-D will terminate this shell and resume system boot.
Give root password for maintenance
(or type Control-D to continue):

Here is what was written to the log:
-----------------------------------------------
Log of fsck -C3 -R -A -a 
Sun Aug 30 15:39:24 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sda3 contains a file system with errors, check forced.
Error reading block 61371369 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 14860312.  

/dev/sda3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Sun Aug 30 15:45:44 2009
----------------

---

### Post by Liolikas on 2009-08-30
You should check then Ignore? Yes Force write? Yes

---

### Post by Zill on 2009-08-30
> **colinireland said:**
> ...Im sort of afraid I will make a balls of it and loose all my data...
You are very unlikely to lose all your data if you keep your backups up to date. ;-)

If your data is important to you then keep regular backups - a hdd can fail at *any* time!

---

### Post by colinireland on 2009-08-30
> **Zill said:**
> You are very unlikely to lose all your data if you keep your backups up to date. ;-)

If your data is important to you then keep regular backups - a hdd can fail at *any* time!

Im am in the process of buying a new external harddrive. My other one is full  to the brim! How can I fix this error manually though?

---

### Post by oldos2er on 2009-08-30
You should run fsck on the drive; either boot into recovery mode and choose fsck from the menu, or if you have a LiveCD you can boot from it and run fsck from inside gparted.

---

### Post by colinireland on 2009-08-31
> **oldos2er said:**
> You should run fsck on the drive; either boot into recovery mode and choose fsck from the menu, or if you have a LiveCD you can boot from it and run fsck from inside gparted.

I booted into recovery mode and ran fsck. Once it hit the /dev/sda3 partition it said something along the lines of running fsck on mounted partitions could cause me to loose data. Any sugestions?

---

### Post by jheaton5 on 2009-08-31
```
sudo /sbin/shutdown -hF now
```

This will restart your system and run fsck before mounting your drive.

---

### Post by oldos2er on 2009-08-31
> **colinireland said:**
> I booted into recovery mode and ran fsck. Once it hit the /dev/sda3 partition it said something along the lines of running fsck on mounted partitions could cause me to loose data. Any sugestions?

 Unmount the partitions. You might need the LiveCD for this.

---

