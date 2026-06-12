---
title: "If I plug in an IDE drive to my Ubuntu system..."
date: 2009-10-16
forum: General Help
---

### Post by Roasted on 2009-10-16
Will it show up in /media without having to be mounted?

Me, personally? I mount my drives automatically via fstab. I know somebody who had a system crash and prior to it, backed 80gb of data up across a pair of 40gb drives. They are running on a brand new hard drive with Ubuntu and want to plug in the IDE 40gb drives in to bring the data off of them.

I know with USB, the devices auto-mount to /media/disk or something generic. What about IDE and SATA devices? Do they still get mounted to a generic tag?

---

### Post by Zimmer on 2009-10-16
Simple (hopefully) answer.
Personally, I add 'DISK MOUNTER' to the gnome panel. Attached Drives show up there ready to be mounted...  I expect that if you used disk mounter for these drives you mention they will be mounted /media/disk  /media/disk-1  etc...

I have a couple of old IDE drives that  I put in a USB external enclosure: have no problems mounting them or booting Ubuntu from them...

---

### Post by ackley on 2009-10-16
Whenever I've done this, the drives show up under the places menu. Click them, enter your password, and they usually get mounted to /media/disk or /media/disk-1 if you have two drives.

If that doesn't work, you could always mount them manually. Just find out where they're located, using ```
sudo fdisk -l
``` and mount them to a place of your liking.

---

