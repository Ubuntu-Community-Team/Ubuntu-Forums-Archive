---
title: "rsync and full-disk backups"
date: 2010-03-20
forum: General Help
---

### Post by jdege on 2010-03-20
I've been using dump/restore for backups, for quite some time.  It's worked fine, but the process of recovering from a HD failure takes too long.

What with eSATA and external drive docks, what I'd really like is to use rsync to maintain a current clone of my entire system drive.  That is, start with a full disk clone, and then use rsync to keep it current.

I've seen plenty of instructions on how to do this with a directory tree, but I've seen none for doing it with a copy of the entire disk.  If, for example, I copy /etc/fdisk, then the copied disk would have entries with the same UUIDs as the original disk.  Which would mean that if the clone disk were to be bootable, its partitions would need the same UUIDs as the original disk.

Which they would be, if the cloned disk started as a full-disk clone, I think.  Am I wrong?

But that means that when the clone disk was active, I'd have partitions with duplicated UUIDs.  Is this going to cause problems?  When I boot, will I get the correct partitions loaded?

---

### Post by asmoore82 on 2010-03-20
It sounds like you just want whole snapshots of your system,
I would highly recommend Clonezilla Live: [http://clonezilla.org/](http://clonezilla.org/)
which has all of the tools(partimage, partclone, etc.) in a neat package.

---

### Post by GSF1200S on 2010-03-20
> **jdege said:**
> I've been using dump/restore for backups, for quite some time.  It's worked fine, but the process of recovering from a HD failure takes too long.

What with eSATA and external drive docks, what I'd really like is to use rsync to maintain a current clone of my entire system drive.  That is, start with a full disk clone, and then use rsync to keep it current.

I've seen plenty of instructions on how to do this with a directory tree, but I've seen none for doing it with a copy of the entire disk.  If, for example, I copy /etc/fdisk, then the copied disk would have entries with the same UUIDs as the original disk.  Which would mean that if the clone disk were to be bootable, its partitions would need the same UUIDs as the original disk.

Which they would be, if the cloned disk started as a full-disk clone, I think.  Am I wrong?

But that means that when the clone disk was active, I'd have partitions with duplicated UUIDs.  Is this going to cause problems?  When I boot, will I get the correct partitions loaded?

Im not sure I completely understand what you are asking. I use rsync to backup /home (which exists entirely on its own drive) to a backup drive which is also its own drive. I create a script to run rsync and then setup crontab to do it at an interval of 20 minutes.

I guess what Im wondering is- what is the backup for? If youre trying to backup in case the main drive fails, then a simple:
```
rsync -avh --delete-recursive / /media/externalbackupdrive
```
should work fine. Even if your UUID's are wrong when you go to boot off the second drive, you can use a liveCD to check the UUID of the backup drive/partitions by looking in /dev/disk/by-uuid. Then you would mount the backup drive in a directory and navigate to /etc/fstab on that drive and make corrections to the UUID label.

Can you clarify what you are asking? :)

---

### Post by jdege on 2010-03-20
> **asmoore82 said:**
> It sounds like you just want whole snapshots of your system,
I would highly recommend Clonezilla Live: [http://clonezilla.org/](http://clonezilla.org/)
which has all of the tools(partimage, partclone, etc.) in a neat package.
AIUI, Clonezilla doesn't work on mounted partitions, you need to boot from the Clonezilla media.  It'd be fine for creating the initial clone, but it'd not be able to keep the clone current, while the original disk was booted and mounted.

---

### Post by jdege on 2010-03-20
> **GSF1200S said:**
> Im not sure I completely understand what you are asking. I use rsync to backup /home (which exists entirely on its own drive) to a backup drive which is also its own drive. I create a script to run rsync and then setup crontab to do it at an interval of 20 minutes.
For a number of years, now, I've been running on a box with no fixed internal drives.  All of my drives are in removable bays.

Used to be, I'd spend an enormous amount of time futzing around with boot loaders and disk formatters, MBRs, and LILO configurations, trying to create a system in which I could boot my choice of a number of different OSes.  Linux, FreeBSD, OS/2, various flavors of Windows.  Then I had the opportunity to do some load testing  in a lab where all of the machines on the net had removable drives.  The experience convinced me that I'd never again build a machine around non-removable drives.

I'm currently in the process of moving from CentOS 5 to Ubuntu 9.10, and of moving from IDE drives to SATA.

What I want is to be able to have a primary SATA drive that I'm running my Ubuntu off of.  And a pair of backup SATA drives that are kept as reasonably current bootable copies.    The idea is that whichever of the backup drives is currently sitting in the eSATA dock, the backup scripts will update to be an up-to-date copy on some periodic schedule.  And daily, or whenever, I can remove the backup drive in the dock, plug in the other, and the backup scripts will bring it up-to-date.

My current backup scripts use dump to copy temporarily-mounted LVM snapshot partitions.  I figure I could do the same with rsync, or some similar tool.  Shut down any running databases, create the snapshot partition, restart the databases, and start the copy.

All of this should be no problem, except that I'd really like to be able to boot off the backup disks simply by selecting it from the BIOS.  And I don't see how to make that work.

What I'd like, is to be able to configure GRUB2 to load the OS off the disk that GRUB2 is loaded onto, rather than off of some fixed disk number.  And to have the OS that loads from that disk mount its partitions from the disk that the OS is loaded on, regardless of whether there are partitions on the other disks with the same UUIDs, or logical volume groups on other disks with the same names.

I was burnt, a few years ago, when it turned out that my restore process was nowhere near as well-developed as my backup process.  I lost a fair bit of data because I could not access the backups I'd been so caefully making.  Since then, I make it a point of doing a restore on a regular basis.  With my current configuration, that means booting off of a CD or some other recovery media, mounting my backup disk, and reading the files on it that describe the current configuration of the supposedly lost drive.  I then partition and format a bare drive, use restore to reconstruct the filesystems from the dump files, running grub to rebuild the MBR, and then I boot off the restored drive.  

The whole process takes about three hours.

In my ideal world, my backup media would be bootable drives, indistinguishable from the original, and I could switch to any backup in no more time than I could power-cycle the machine.  But I don't know how to make that work.

---

