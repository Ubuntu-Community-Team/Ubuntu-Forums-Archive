---
title: "Filesystem set itself to read-only"
date: 2009-07-12
forum: General Help
---

### Post by gaspodog on 2009-07-12
Recently, I noticed that I was getting errors with some applications, and found that my root filesystem had been set to read only somehow (not through anything I'd done). When I rebooted, I was taken to the console and required to run fsck. After that, the system rebooted correctly and things seem to be working again.

Does Ubuntu automatically make filesystems read-only if it detects some sort of error? Which log file can I look in to try to determine what went wrong in the first place?

Thanks!

---

### Post by chriskin on 2009-07-12
do you mean that you log in as a user and find root read-only?

---

### Post by michy99 on 2009-07-12
The main partition is indeed set to mount as read-only if there is a problem with the mount. If this happens, you need to figure out what is causing the problem.

---

### Post by Arand on 2009-07-12
Whenever this has happened to me it has always worked out by manually running fsck from a livecd (fsck -- file system check {I think...})

Open a terminal and do:```
sudo fsck -f /dev/sdx#
```where "x" is the hard-drive designation, normally "a" (if you have only one disk); and "#" is the partition number where ubuntu is installed.
Example:```
sudo fdisk -f /dev/sda5
```
(-f parameter does the check even if it is marked as clean before)

To easily find the designation you can use gparted and note the name of the ubuntu partition.

 - Arand

---

### Post by gaspodog on 2009-07-12
chriskin:

The switch seemed to happen after I'd been using the system for a while - suddenly things started throwing errors because they could no longer write to the filesystem. They'd been working fine until then.

The fsck from the console after reboot seems to have fixed it, I'm just curious as to whether this is what's supposed to happen during a session if a disk problem arises, and whether I can find out what's causing the problem.

---

