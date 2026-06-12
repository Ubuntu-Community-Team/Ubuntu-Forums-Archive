---
title: "unable to mount hard drive"
date: 2011-10-31
forum: General Help
---

### Post by Frogster on 2011-10-31
When trying to mount with Disk Utility I get

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 2 in /etc/fstab is bad
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

fstab reads

UUID=bf1c2c2c-7f33-43b6-ae30-d593717d4793 swap swap sw 0 0
UUID=6cb0d2c0-ed4b-430d-85f3-f0211242f37c /media/Big Empty ext3 remount,journal=update 0 0
UUID=b32785e0-04d3-4d65-9032-b0c095cdbe7d / ext4 defaults 0 1
UUID=6a3b8487-11cb-496c-9d4a-117428a8df67 /media/sda2 ext2 noauto 0 0
UUID=4880d5f5-f682-468b-b034-9c73000c6702 /media/sdc1 ext4 defaults 0 0
/dev/fd0 /media/floppy0 vfat noauto 0 0

How do I edit fstab to get my drive back and automatically mount? any help will be gratefully recieved

---

### Post by Rhizoid on 2011-10-31
> **Frogster said:**
> When trying to mount with Disk Utility I get

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 2 in /etc/fstab is bad
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

fstab reads

UUID=bf1c2c2c-7f33-43b6-ae30-d593717d4793 swap swap sw 0 0

UUID=b32785e0-04d3-4d65-9032-b0c095cdbe7d / ext4 defaults 0 1
UUID=6a3b8487-11cb-496c-9d4a-117428a8df67 /media/sda2 ext2 noauto 0 0
UUID=4880d5f5-f682-468b-b034-9c73000c6702 /media/sdc1 ext4 defaults 0 0
/dev/fd0 /media/floppy0 vfat noauto 0 0

How do I edit fstab to get my drive back and automatically mount? any help will be gratefully recieved

Where did the line ```
UUID=6cb0d2c0-ed4b-430d-85f3-f0211242f37c /media/Big Empty ext3 remount,journal=update 0 0
``` in fstab come from?  Did you add it manually?

---

### Post by Frogster on 2011-10-31
I think I may have accidentally

---

### Post by Rhizoid on 2011-10-31
> **Frogster said:**
> I think I may have accidentally

I'm pretty sure it's not going to understand the space between Big and Empty.  The media folder isn't the best place to auto mount something either...

Try changing line 2 to:

```
 UUID=6cb0d2c0-ed4b-430d-85f3-f0211242f37c /mnt/big.empty ext3 remount,journal=update 0 
```Then issue;

```
sudo mkdir /mnt/big.empty
``` in terminal (CTRL + ALT + t) (supplying your sudo password when required)

To test the mount works issue;

```
sudo mount -a
``` in terminal.

Let me know how that pans out ;)

Cheers,

---

### Post by coffeecat on 2011-10-31
> **Rhizoid said:**
> The media folder isn't the best place to auto mount something either...

Point of information. The folder /media is a perfectly valid place to automount something so long as you create a folder within it as your mountpoint. It doesn't matter that /media is used by udev for automounting removable drives and internal partitions from the Places menu. Functionality exists to prevent the system using the same mountpoint name as one the user might have chosen.

The advantage of using /media is that in releases before 11.10, you get a desktop icon for each mounted partition - in 11.10 you get a launcher icon.

To some people that's a disadvantage, and if you don't want a desktop/launcher icon, then /mnt is a perfectly valid place for a mountpoint.

On my own system I have my shared data partition mounted to /media/Data so that I have a clickable icon to open for the partition. For my partition with VirtualBox VDIs, I use a mountpoint in /mnt because I don't want to see an icon and I have symlinked the mountpoint to the usual place where VirtualBox VDIs go.

Horses for courses. :)

---

### Post by Frogster on 2011-10-31
Hi Rhizoid

This is how this pans out.

keith@Ernie:~$ sudo mount -a
mount: /mnt/big.empty not mounted already, or bad option
keith@Ernie:~$ 
 
*scatching head* :-) I hope it means more to you thn it does to me

---

### Post by Frogster on 2011-10-31
Hi Coffeecat a desktop icon for each mounted partition is fine for me.
Thanks for the input

---

### Post by coffeecat on 2011-10-31
> **Frogster said:**
> Hi Coffeecat a desktop icon for each mounted partition is fine for me.
Thanks for the input

Rhizoid will be able to solve your problem. I just wanted to add that little bit about /media and /mnt because there is a small amount of disagreement about which you should use and when, based mostly on the history of how and why those two directories came about.

Good luck!

---

### Post by Frogster on 2011-10-31
Coffeecat,

I seem to remember "talk" about /media and /mnt. :-)

---

### Post by Rhizoid on 2011-10-31
> **coffeecat said:**
> Rhizoid will be able to solve your problem. I just wanted to add that little bit about /media and /mnt because there is a small amount of disagreement about which you should use and when, based mostly on the history of how and why those two directories came about.

Good luck!

Thanks for the clarification coffeecat.

Frogster: try removing the remount option from fstab line 2.

Either choose /mnt/big.empty or /media/big.empty as your mount point.  Whichever you choose, make sure the directory you're going to use as the mount point exists.

---

### Post by Frogster on 2011-10-31
Thank you rhizoid, I can now reach the drive. I have my music back! Eyes are now closing. Tomorrow/today will decide on the chossen mount point.

Once again I learn buy my mistakes and I am saved by the members of the forum.

Sleep well

Frogster

---

