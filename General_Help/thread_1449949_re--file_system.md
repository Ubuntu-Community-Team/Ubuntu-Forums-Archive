---
title: "re--file system"
date: 2010-04-08
forum: General Help
---

### Post by nischalinn on 2010-04-08
When I entered the command "**df**",it shows:

[LEFT]**tmpfs   **              944M     0  944M   0% /lib/init/rw
**varrun     **           944M  128K  944M   1% /var/run
**varlock         **      944M     0  944M   0% /var/lock
**udev       **           944M  148K  944M   1% /dev
**tmpfs   **              944M  972K  943M   1% /dev/shm
**lrm         **          944M  2.4M  942M   1% /lib/modules/2.6.28-11-generic/volatile


What is this **tmpfs ,****varrun, ****varlock, ****udev, ****tmpfs & ****lrm?     **     [/LEFT]

---

### Post by bobcollard on 2010-04-08
> **nischalinn said:**
> When I entered the command "**df**",it shows:

[LEFT]**tmpfs   **              944M     0  944M   0% /lib/init/rw
**varrun     **           944M  128K  944M   1% /var/run
**varlock         **      944M     0  944M   0% /var/lock
**udev       **           944M  148K  944M   1% /dev
**tmpfs   **              944M  972K  943M   1% /dev/shm
**lrm         **          944M  2.4M  942M   1% /lib/modules/2.6.28-11-generic/volatile


What is this **tmpfs ,****varrun, ****varlock, ****udev, ****tmpfs & ****lrm?     **     [/LEFT]

They are directories, for instance, **varrun** can be found in your File Manager under "file system/var/run" (Without the quotes)  Some people call them files, the correct term in this instance is directory.  The slashes (/) separate the directories showing one inside the other.

---

### Post by cdenley on 2010-04-08
They are filesystems, as the column is named at the top. Those happen to be filesystems physically stored in memory, not a hard drive.

---

### Post by srs5694 on 2010-04-08
To elaborate a bit further, Linux creates several *virtual filesystems* to facilitate specific purposes. For instance, /dev is a virtual filesystem that holds files that give access to your hardware (hard disks and partitions, sound hardware, printers, etc.). Putting /dev on a virtual filesystem enables the kernel to modify its files very easily, adding or deleting files as devices are added or deleted. For instance, when you plug in a USB flash drive, entries for it and its partitions will appear. The alternative, which was common several years ago, was to have a /dev directory on the root (/) filesystem that held device files that pointed to common devices. The problem then was that such a directory was hard to update dynamically, so some device files would point to non-existent hardware and/or the /dev directory might be missing files for some hardware on the computer.

For the most part, you as a user don't need to worry about these directories. On occasion you may need to specify a device filename in /dev or access a file in /proc, but mostly these virtual filesystems operate behind the scenes and do their thing without the need for user intervention.

---

