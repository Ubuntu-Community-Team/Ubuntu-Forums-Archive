---
title: "Abandoning RAID-1 attempts"
date: 2010-08-23
forum: General Help
---

### Post by shortmort37 on 2010-08-23
I've lamented my attempts in other threads; (*sigh*):

[http://ubuntuforums.org/showthread.php?t=1432450](http://ubuntuforums.org/showthread.php?t=1432450)

I officially give up.  I want to eliminate the remnants of the RAID (which, at this point, includes unused device /dev/sdb1).  I've changed it's partition type from RAID back to linux; I've tried formatting it; I've tried zeroing the superblock on /md0 and /sdb1:

mdadm --zero-superblock /dev/md0
mdadm: Unrecognised md component device - /dev/md0

sudo mdadm --zero-superblock /dev/sdb1
mdadm: Couldn't open /dev/sdb1 for write - not zeroing

I've tried to "fail" it:

mdadm --manage /dev/md0 --fail /dev/md0
mdadm: set device faulty failed for /dev/md0:  No such device

In the GUI disk utility, I can attempt to remove the component - which, invokes mdadm:

Error removing component: helper exited with exit code 1: 'mdadm --manage /dev/md0 --remove /dev/sdb1' failed with: 'mdadm: hot remove failed for /dev/sdb1: Device or resource busy

I've deleted /etc/mdadm/mdadm.conf files too - I've tried a lot of things that I've read in a lot of different threads, to no avail.  Is there no way to get rid of it?

adTHANKSvance,
Dan

---

### Post by oldfred on 2010-08-23
Drives retain meta data:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

sudo apt-get remove dmraid
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470)

---

### Post by shortmort37 on 2010-08-24
> **oldfred said:**
> Drives retain meta data:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb


There was only ever one device in my RAID (see attachment) - I got hung up with grub before the other could be added.  So, I tried these commands:

dan@ubuntu:~$ sudo dmraid -E -r /dev/sdb
no raid disks and with names: "/dev/sdb"
dan@ubuntu:~$ sudo dmraid -E -r /dev/sdb1
no raid disks and with names: "/dev/sdb1"

Please advise...

Thanks
Dan

---

### Post by oldfred on 2010-08-25
You could try just zeroing out the partition table. Not sure where RAID writes its info.  I assume you have backed up or do not care about any data on drive.

This will blank MBR and partition table of sdb:
Zero out MBR and partition table
dd if=/dev/zero of=/dev/sdb bs=512 count=1

Zero out MBR only of sdb
dd if=/dev/zero of=/dev/sdb bs=446 count=1

Or zero out entire drive, may take a while.
If it is /dev/sdb, now use dd to wipe it of all data, partitions, and MBR information with command: 
dd if=/dev/zero of=/dev/sdb.

You will have to repartition and reformat partitions after you zero out the partition table.

---

### Post by shortmort37 on 2010-08-25
> Or zero out entire drive, may take a while.
If it is /dev/sdb, now use dd to wipe it of all data, partitions, and MBR information with command: 
dd if=/dev/zero of=/dev/sdb.

YES!  This worked!  Thank you, thank you!

Since the goal of RAID-1 for this device was to maintain a backup in case of drive failure - I wonder, might it be possible to cron something like

dd if=/dev/sda0 of=/dev/sdb0

(with an identical swap partion on sdb, as on sda), and be able to boot sdb in the event sda fails?  Or, would I have to run this from, say CD, with both drives unmounted?

Thanks so much for your help!

Dan

---

### Post by oldfred on 2010-08-26
I am not real knowledgeable on the use of dd which is very powerful (and dangerous). One disadvantage is that you have to copy from and to the same size drive. Some have used it to move to a new larger drive and it litterally converted the new larger drive to the smaller drive and we had a real good time trying to get the drive to see its full size. If also copies UUIDs which are used by fstab & grub. While good for an identical backup without having to update new UUIDs if a different disk, if you keep both drives plugged in grub & Ubuntu do not know which UUID is which and may randomly boot one drive or the other. Then you do not know which is more current. 

I prefer using rsync for backups. I changed script below to one of my paths and commented out some of the original.

Quote:
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
use a text editor and paste this into a file. name it mybackup.sh
Code:

#!/bin/bash
# backup script
# a - archive, retain file settings
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
echo "starting..."
rsync -aruvP /mnt/data_DT/Documents /usr/local/fred/data/

#rsync -auvP /home /media/backup
#rsync -auvP /share /media/backup
#rsync -auvP /media/floppy /media/backup
#rsync -auvP /etc /media/backup
echo "done"
exit 0

make it executable
Code:

chmod +x mybackup.sh

run it
Code:

./mybackup.sh

of course, do the dry run first as I said before
thank you very much. I made a symbolic link from /bin/backup to /root/backup.sh, thanks!!!!!

---

