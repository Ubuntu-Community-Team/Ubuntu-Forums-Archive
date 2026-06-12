---
title: "Too much background activity in Xubuntu 9!!!"
date: 2009-10-13
forum: General Help
---

### Post by ProDigit on 2009-10-13
Hi,

My HD just broke, and for now I'm helping myself with Xubuntu 9.04 on a USB stick.
I regularly see the light lit up of my USB stick, and have the impression it's doing stuff on the background.
I don't like this, because the USB stick is pretty slow and has delays booting certain windows.
I installed Xubuntu on a EXT2 formatted partition on the 4GB USB drive.
I enabled noatime within fstab (changed another ..time parameter to noatime).
Now I'd like to know how to further improve xubuntu for a USB stick.
I'd also like to know how to disable the background activity!
So far I'm only running a firefox window, and the USB stick gets accessed for 3 seconds about every 13 seconds.

Anyone has any clue what that could be?

---

### Post by ProDigit on 2009-10-14
Bump...

---

### Post by anonymous_user on 2009-10-14
Check what services are enabled. Also if Xubuntu has search indexing, disable it.

---

### Post by kerry_s on 2009-10-14
add "elevator=as" on the kernel boot line in /boot/grub/menu.lst.
example:
```
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/hda2 ro elevator=as
``` 

that will make it wait to right out to disk, less writes.

---

### Post by ProDigit on 2009-10-14
> **anonymous_user said:**
> Check what services are enabled. Also if Xubuntu has search indexing, disable it.

I can find very little info on search indexing in Xubuntu. Any hints would be appreciated!


> **kerry_s said:**
> add "elevator=as" on the kernel boot line in /boot/grub/menu.lst.
example:
```
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/hda2 ro elevator=as
``` 

that will make it wait to right out to disk, less writes.

I tried this, and with next reboot see if it helps.
In the kernel line I have "ro quiet splash" at the end, where you added "elevator=as"
Should I just add that to the line, or get rid of "quiet splash"?

---

### Post by kerry_s on 2009-10-14
> I tried this, and with next reboot see if it helps.
In the kernel line I have "ro quiet splash" at the end, where you added "elevator=as"
Should I just add that to the line, or get rid of "quiet splash"?

just add it to the end.

---

### Post by ProDigit on 2009-10-15
I've done the elevator=as, though I don't know if it makes that much difference...
Perhaps before it froze more, as where now the OS freezes much less (that's just an impression, but I haven't measured it yet)...

As for the disk activity, it still seems to go on.
I do not have a swap partition, so it can't be reading to and from swp (I have 2GB of ram so should be enough for Xubuntu).

Anyone has any idea why the USB stick gets accessed every 10 seconds (when only Firefox is running)?
Apart from a dictionary I don't have any add ons installed.

---

### Post by Mighty_Joe on 2009-10-15
Have a look at my post in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680").  I've linked to some optimizations like moving logging and caching to tmpfs and it will take a lot of the load off the flash drive.  
You can use e2fsck -D to optimize the directories in an ext2 volume:
```
sudo e2fsck -fD /dev/sda1
```
You can't do it on a mounted filesystem, so you'll have to boot the Live CD to do it.  
I've been using ext3 on my latest USB flash drive install and it feels faster than ext2.  I used [these tips]("http://en.opensuse.org/Speeding_up_Ext3") to get the most out of it.  It's more stable than ext2 in my experience. No more boots delayed by "the volume not unmounted properly" messages.

---

### Post by ProDigit on 2009-10-29
> **Mighty_Joe said:**
> Have a look at my post in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680").  I've linked to some optimizations like moving logging and caching to tmpfs and it will take a lot of the load off the flash drive.  
You can use e2fsck -D to optimize the directories in an ext2 volume:
```
sudo e2fsck -fD /dev/sda1
```
You can't do it on a mounted filesystem, so you'll have to boot the Live CD to do it.  
I've been using ext3 on my latest USB flash drive install and it feels faster than ext2.  I used [these tips]("http://en.opensuse.org/Speeding_up_Ext3") to get the most out of it.  It's more stable than ext2 in my experience. No more boots delayed by "the volume not unmounted properly" messages.

I tried the following:

```
sudo e2fsck -fD /dev/sdb1
```
(since my drive is sdb1) and I get:
```
e2fsck 1.41.4 (27-Jan-2009)
/dev/sdb1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

Pass 1: Checking inodes, blocks, and sizes
Deleted inode 269540 has zero dtime.  Fix<y>? yes

Pass 2: Checking directory structure
Symlink /usr/lib/python2.6/dist-packages/calibre/ebooks/lrf/web/profiles/economist.py (inode #309163) is invalid.
Clear<y>? 

/dev/sdb1: e2fsck canceled.

/dev/sdb1: ***** FILE SYSTEM WAS  MODIFIED *****
/dev/sdb1: ***** REBOOT LINUX *****


```

Arg, just read that it had to be done from another drive, as I was still running the OS from that drive...

---

### Post by ProDigit on 2009-10-29
> **anonymous_user said:**
> Check what services are enabled. Also if Xubuntu has search indexing, disable it.

how?

---

