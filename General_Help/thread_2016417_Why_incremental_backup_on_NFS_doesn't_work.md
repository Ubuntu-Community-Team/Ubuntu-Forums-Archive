---
title: "Why incremental backup on NFS doesn't work ?"
date: 2012-07-04
forum: General Help
---

### Post by archi02 on 2012-07-04
Hello,

I'm using BackinTime for my daily PhD backups. Everything works well, snapshots are done, correctly incrementals... only on local repertory.

If I ask for a backup on a NFS partition, the backups works too (I get no errors), but never incremental. I've as much complete snapshots as backups done.

I tried to mount my NFS partition in the classic way with fstab, and even with automount (uid/gid : 1000/1000, I don't know if it could help)... for same results.

Why incremental backup on NFS doesn't work ? What I miss ?

---

### Post by archi02 on 2012-07-05
up... any idea ? :)

---

### Post by SeijiSensei on 2012-07-05
Perhaps because so many of us roll our own solutions for backups.  Have you asked the BackinTime people about this?

Off the top of my head, all I can think of is that something is changing the datestamps on the mounted share.  Is it mounted continuously, or do you mount/unmount the exported share between backups?  If the latter, try keeping it mounted continuously for a day or two and see if that helps any.

---

### Post by Cavsfan on 2012-07-05
I know this has nothing to do with BackinTime but, if you do not find a solution to your problem., you might consider this.
I was recently introduced to a CLI backup program that works flawlessly. It backs up an entire system, which cannot be mounted at the time it is being backed up or restored.
It will restore that backup onto a partition and it doesn't care about what size it is. I mean it will restore a backup where the size is different that what it was.
It doesn't care. You can format the partition as I have done.
Edit: What is nice is if you are backing up 50GB used on a partition that is say 150GB total, it will just need 50GB on the backup drive. So, the backup partition or drive doesn't have to match the size of the drive you are backing up.
I back up all three OS partitions in the one Backup partition.

It is called **fsarchiver** and it doesn't do incremental backups, but it sure has saved me a few times.
It is in the repositories. I created a backup partition as it cannot be on a NTFS drive.
I have 3 linux systems on this PC and I backed up and restored Precise twice with perfect success.
Also, I labeled the partitions so I didn't have to enter a long UUID or any of that.
**sudo tune2fs -L Precise /dev/sda5** - my Precise install is on sda5 and once I entered this command. It lists that volume as "Precise".

I also labeled the backup partition **sudo tune2fs -L Backup /dev/sda6**

I logged into Lucid, mounted the backup and made the backup like this:
**cd /media/Backup/**
**fsarchiver savefs -z 3 -v precise.backup.fsa /dev/sda5**
The -z 3 parameter is compression level 1-9. The higher the level the slower the process.
Then following that is the file name I gave it and the partition which it is on. There are a lot more options as you can see from the man page.

Then I restored that backup in the same way with this command:
**fsarchiver restfs precise.backup.fsa id=0,dest=/dev/sda5**

This is just a suggestion I thought I would share. It may not be what you need and if so just disregard.

---

