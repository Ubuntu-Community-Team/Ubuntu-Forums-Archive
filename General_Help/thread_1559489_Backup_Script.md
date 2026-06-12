---
title: "Backup Script"
date: 2010-08-23
forum: General Help
---

### Post by gavinjb on 2010-08-23
Hi,

I have been away form Linux for a while so please stay with me (but at last I have got the company I work for to support Linux for remote access!) anyway since I last used Linux I have purchased a QNAP NAS Drive and I am looking at a way to write a script to backup to the drive.

I need the script to be able to check that the NAS Drive is mounted before starting to do the back (don't know if it still does it, but I have had problems in the past where backup scripts have backed up data to a mount point folder as the drive wasn't mounted)

The NAS Windows Share is \\192.168.2.150\Backup (it can also be mounted as NFS)

I could do with some help on the best way to set this up in fstab and then some thoughts on my old backup script (see below

```

#! /bin/bash

OPTIONS="-r --force --delete --ignore-errors -a"

# grep '/media/nasbackup/LinuxBackup/' /etc/mtab

# Check USB Drive Mounted
if [ "`grep 'nasbackup' /etc/mtab`" ]
then
	# Run Backup
	echo “Starting Backup”
	echo /home/gavin/Desktop
	rsync /home/gavin/Desktop/ $OPTIONS /media/nasbackup/DataBackup/Desktop/
	echo /home/gavin/Documents/
	rsync /home/gavin/Documents/ $OPTIONS /media/nasbackup/DataBackup/Documents/
	echo /home/gavin/Music/
	rsync /home/gavin/Music/ $OPTIONS /media/nasbackup/DataBackup/Music/
	echo /home/gavin/Pictures/
	rsync /home/gavin/Pictures/ $OPTIONS /media/nasbackup/DataBackup/Pictures/
	echo /home/gavin/Videos/
	rsync /home/gavin/Videos/ $OPTIONS /media/nasbackup/DataBackup/Videos/
	echo “Backup Completed”
else
	# Unable to find USB Drive
	echo “backup disk not available”
	exit 0
fi

```

Ideally I would like someway of detecting if the NAS drive ever goes down halfway through a backup and then exiting the backup.

Any help that you can give would be appreciated

Thanks,



Gavin,

---

