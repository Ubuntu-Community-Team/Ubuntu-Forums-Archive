---
title: "Backup to external SATA drive"
date: 2009-08-07
forum: General Help
---

### Post by mogators on 2009-08-07
My Linux server has an internal 1TB drive for storage of all my data files that is shared onto my network.  This device is /dev/sdb1 and is ext3 formatted (mounted as /srv/share/data1).  I just purchased an external 1TB eSATA drive to serve as a backup for this drive.  I have not even plugged it in yet so don't know if Ubuntu will auto recognize it or what.  I was going to try using grsync to do the backups.  Is this a good route to take for doing incremental backups?  I installed grysnc but it does not show up under the Applications anywhere.  I can start it using command line though.  Can someone tell me how to add this to the Applications menu and how to configure the eSATA drive for use with grsync?

---

### Post by cosine352 on 2009-08-07
It should be in the 'Applications --> Internet'. If it is not there you can add it from 'System --> Preferences --> Main Menu' Click on the internet tab and add check grsync

---

### Post by amac777 on 2009-08-07
On my system, it get's installed to 'applications->system tools'.

GRsync is a tool focused to make a copy or synchronize data effeciently because it only copies the portions of files that have actually changed. But, by itself, it's not that good as a true backup tool because if one of your original files gets corrupted or deleted, the next time you run grysnc to synchronize your backup copy then the file will be corrupted on both the original and the backup.

For doing incrmental backups where you still keep the older versions of files incase you need them later, check out 'rsnapshot' or 'rdiff-backup'. Both are good tools and in the repositories.

[http://rsnapshot.org/](http://rsnapshot.org/)

[http://rdiff-backup.nongnu.org/](http://rdiff-backup.nongnu.org/)

Additonal: rsnapshot will probably require you to format the new drive as ext3 (or ext2) to get the full advantages of hard links and unix style permissions. I think rdiff-backup should work fine regardless of what file system you have on the new drive. But there might be some issues with maximume sizes of files. Not 100% sure. I keep all my drives in ext3 or ext2 since I only use Linux.

---

### Post by mogators on 2009-08-08
> **cosine352 said:**
> It should be in the 'Applications --> Internet'. If it is not there you can add it from 'System --> Preferences --> Main Menu' Click on the internet tab and add check grsync

OK, I found it there.  Weird place for it to be.  Used the 'Main Menu' editor to move it to the System Tools.

---

### Post by mogators on 2009-08-08
> **amac777 said:**
> On my system, it get's installed to 'applications->system tools'.

GRsync is a tool focused to make a copy or synchronize data effeciently because it only copies the portions of files that have actually changed. But, by itself, it's not that good as a true backup tool because if one of your original files gets corrupted or deleted, the next time you run grysnc to synchronize your backup copy then the file will be corrupted on both the original and the backup.

For doing incrmental backups where you still keep the older versions of files incase you need them later, check out 'rsnapshot' or 'rdiff-backup'. Both are good tools and in the repositories.

[http://rsnapshot.org/](http://rsnapshot.org/)

[http://rdiff-backup.nongnu.org/](http://rdiff-backup.nongnu.org/)

Additonal: rsnapshot will probably require you to format the new drive as ext3 (or ext2) to get the full advantages of hard links and unix style permissions. I think rdiff-backup should work fine regardless of what file system you have on the new drive. But there might be some issues with maximume sizes of files. Not 100% sure. I keep all my drives in ext3 or ext2 since I only use Linux.

Thanks for the info, I'll check those out.

---

