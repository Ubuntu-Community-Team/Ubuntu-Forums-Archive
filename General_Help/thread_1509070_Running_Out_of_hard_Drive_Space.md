---
title: "Running Out of hard Drive Space"
date: 2010-06-13
forum: General Help
---

### Post by slalomchip on 2010-06-13
I installed Ubuntu 9.10 onto my laptop and then upgraded it to Ubuntu 10.4.  I've added some software packages along the way, such as MythTV and several smaller apps, but have not gone crazy in adding apps.  I have a 160GB hard drive.

I ran out of disk space recording a World Cup game and was surprised.  I deleted all of the MythTV recordings and ran Computer Janitor and now I have only about 50GB of free space!  It is not my primary computer, so I don't have a bunch of videos, music, pr pictures on it.

I did a clean install of Ubuntu 10.4 to a USB flash drive and it has only 3.7GB occupied on the drive.

Any recommendations of why I have over 100GB on the hard drive and any cures on how to clear out unneeded files?

Thanks.

---

### Post by slash86 on 2010-06-13
Try running "disk usage analyzer". It will display which files or folders are consuming a great amount of space.

hope it helps.

---

### Post by slash86 on 2010-06-13
as another tip, upgrades from versions never worked fine for me or my close friends... a fresh instalation is always preferred (in my opinion).

---

### Post by wilee-nilee on 2010-06-13
> **slalomchip said:**
> I installed Ubuntu 9.10 onto my laptop and then upgraded it to Ubuntu 10.4.  I've added some software packages along the way, such as MythTV and several smaller apps, but have not gone crazy in adding apps.  I have a 160GB hard drive.

I ran out of disk space recording a World Cup game and was surprised.  I deleted all of the MythTV recordings and ran Computer Janitor and now I have only about 50GB of free space!  It is not my primary computer, so I don't have a bunch of videos, music, pr pictures on it.

I did a clean install of Ubuntu 10.4 to a USB flash drive and it has only 3.7GB occupied on the drive.

Any recommendations of why I have over 100GB on the hard drive and any cures on how to clear out unneeded files?

Thanks.

I think your trying to stop a boulder with a feather Ubuntu cleans itself basically except for the cache which is small, get a external HD

```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
``` 
will clean stuff up, and bleachbit as well use this last one carefully though it will clean your bookmarks and passwords. Use xmarks on FF to save bookmarks and passwords

---

### Post by cbecker78 on 2010-06-13
> **slash86 said:**
> Try running "disk usage analyzer". It will display which files or folders are consuming a great amount of space.

hope it helps.

+1.  You want to click on the button to scan hard drives once you open it.  disk usage analyzer is in Applications -> accessories.

---

### Post by slalomchip on 2010-06-13
Disk Usage Analyzer shows that File System is only 5.3 GB (good news), but above that statement it says:

*Total filesystem capacity: **140.7** GB (used 81.4 GB available: 59.3 GB )*

These two statements appear to be contradictory.  I haven't partitioned the hard drive other than how Ubuntu partitioned it.  The Disk Utility app shows the following partitions:

[I]154 GB ext4
Extended 6.5 GB
Swap Space 6.5 GB[/I]

Disk Utility SMART Data self-tests also indicates everything else is working properly.

I'm not sure "autoremove" and "autoclean" are what I need right now.  Maybe later.

Ideas?

---

### Post by john newbuntu on 2010-06-14
Before you start anything, empty your trash in case you have not already done  so.

I'd suggest using a terminal and checking the facts.  Open up a terminal (apps->accessories->terminal) and run the following commands.  Please post the output:
```
df -Th
```
This will give you an idea on the approximate usage of objects in your filesystems.  

Also run this command from the root directory of your filesystem:
```
cd /
sudo du -k | sort -n > /tmp/files
gedit /tmp/files
```
This gives the actual space taken up in kilobytes sorted by size.  Do not post the results as it will be huge.  But take a look at it and you can see the big files/directories at the bottom.  Start cleaning up appropriately or consult on this forum to see if it really needs to be removed.
On a side note, your swap appears to be a tad bit on the larger side.  Just keep it at about 1.5 to 2 times your RAM unless you have a specific reason to do so.

---

### Post by slalomchip on 2010-06-14
Thanks for that last tip.  The /tmp/files file yeilded thatI had a bunch of full and incremental backups in /var/backup from Simple Backup (that I forgot I had setup).  This folder has permissions of drwxr-x---.  I switched to root and did a 

chmod 777 /var/backup

then deleted the old backups, then did a 

chmod 750 /var/backup

to restore the original privileges.  That took me to about 130GB free.  I'll take it. Filesystem says I'm using 4.5GB, so there must be other folders out there that have "---" for "other user permissions", but I'm not worried about it.

I'll now work with Simple Backup settings to not backup MythTV recordings and change the periods of fulls and incremental backups (I cloned the hard drive with Clonezilla).

BTW - I think my swap is correctly sized because I have 4GB memory in the laptop.

Thanks for all of the help.

---

