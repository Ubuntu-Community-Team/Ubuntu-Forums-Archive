---
title: "Backup with dd and partition mount points problem."
date: 2011-12-20
forum: General Help
---

### Post by flemur13013 on 2011-12-20
Hi - 

A week or so ago I backed up two partitions, / and /home, to a  USB drive (500M "FreeAgent Go") using:

```
$ dd if=/dev/sda7 of=/dev/sdg7  
$ dd if=/dev/sda9 of=/dev/sdg8
```Against standard advice I did the backups while the system was running....

When I was done I had TWO partitions mounted as "/" and TWO partitions mounted as "/home" !?  (shown in gparted and palimpsest).  They showed up that way whenever the USB disk was plugged in.

I deleted the USB partitions using windows/PartitionWizard because I didn't feel safe messing around with them in linux trying to fix it   (as per above).

Is this because I didn't use a LiveCD?  Or is it normal?  

What happens if I change something - delete or add a file, etc - on /home - does it change on both partitions? 

How to prevent it happening again?

TIA!

---

### Post by oldfred on 2011-12-20
dd does a byte by byte or even bit by bit copy even blank space. It has the nickname Data Destroyer as any typo or error often causes major problems.

You also copied the partition UUIDs, so all the grub & fstab entries see both or either randomly.
I prefer to use rsync as that only copies data not empty space, but you still have to update fstab & grub UUID entries if you want to use backup separately. Backup is just that and the way you did is so you can remove it and later copy it back as an exact image. But you cannot have both mounted. I also prefer not to spend time and space copying system files as I expect just to reinstall. So I only back up /home, some settings & most data. But if you have to have an image for various reasons then some of the full image methods may be better.

If you want to copy /, I think you have to do that from a liveCD so files are not open and then not copied. Many do not need to be as they are temp files.

Some ways to backup.
discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

[http://www.rsnapshot.org/](http://www.rsnapshot.org/)
[http://backintime.le-web.org/](http://backintime.le-web.org/)
[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)
[http://flyback-project.org/](http://flyback-project.org/)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

---

### Post by flemur13013 on 2011-12-20
Thanks!  I'll check those links and mark this "solved".

I like to make a complete copy of partitions and then then do incremental backups - and I usually install enough extra stuff that backing up /home doesn't cut it! (I keep non-system data like pictures and music on yet another partition, not /home...)

---

