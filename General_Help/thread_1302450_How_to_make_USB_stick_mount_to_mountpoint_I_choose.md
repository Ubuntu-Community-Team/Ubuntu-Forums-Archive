---
title: "How to make USB stick mount to mountpoint I choose"
date: 2009-10-27
forum: General Help
---

### Post by abacabus on 2009-10-27
Hi there.

I have several USB-sticks with different labels on them , and when I put them in the computer they all automatically mount to different mountpoints, like "media/7013-A7C7" or something. I want all USB-sticks to mount to "media/disk", and subsequent sticks to "media/disk-1", "media/disk-2" and so on. How can I do that?

Thanks in advance

PS I am using ubuntu 9.10

---

### Post by dcstar on 2009-10-27
> **abacabus said:**
> Hi there.

I have several USB-sticks with different labels on them , and when I put them in the computer they all automatically mount to different mountpoints, like "media/7013-A7C7" or something. I want all USB-sticks to mount to "media/disk", and subsequent sticks to "media/disk-1", "media/disk-2" and so on. How can I do that?

Thanks in advance

PS I am using ubuntu 9.10

Label them accordingly.

---

### Post by abacabus on 2009-10-31
Thank you for an answer. Unfortunately it did not answer what I really want to know, so I rephrase the question a bit:

How can I make any USB-stick, no matter what label it has, mount to "media/disk" ?

---

### Post by mc4man on 2009-10-31
> How can I make any USB-stick, no matter what label it has, mount to "media/disk

Don't believe that's possible in karmic

I didn't use jaunty so don't know what happened there. Prior to karmic if a usb drive didn't have a volume label then it would mount to /media/disk,

If others without labels were added while 1st. one was still mounted then media/disk-1, media/disk-2, ect.

In karmic even if there is no label set it's 'given' one so to speak, like /media/49EE-39DD ( where exactly that comes from don't know.

If you want disk, disk-1 ect. then as previously mentioned, label the drives as such.

---

### Post by FishFoot on 2009-11-06
I made some headway on something similar.

First I had to unmount the device (but leave it connected).  Then I opened "System -> Administration -> Disk Utility".  That seems to list all the available disks with the volumes found on the disks.  I clicked the volume that I wanted to set to a static mount point and I set the "Label" field.  

One minor annoyance, it capitalized whatever I put in there.  In this case I was trying to set my cell phone (an HTC Diamond) up.  Normally I set the mount point as /media/Diamond.  Doing it this way forced me to use /media/DIAMOND.

Annoying... but it worked.  I used to do this with gconf-editor and I have to say this mechanism is much more graceful.

---

### Post by prkfriryce on 2010-01-06
> **FishFoot said:**
> 
One minor annoyance, it capitalized whatever I put in there.  In this case I was trying to set my cell phone (an HTC Diamond) up.  Normally I set the mount point as /media/Diamond.  Doing it this way forced me to use /media/DIAMOND.



Has anyone else encountered this issue? Is there a workaround for the disk label so the disk utility does not capitalize it?  

I noticed the same condition occurs when you label a disk using gparted too.

---

### Post by ericeclifford on 2010-03-29
> **prkfriryce said:**
> Has anyone else encountered this issue? Is there a workaround for the disk label so the disk utility does not capitalize it?  

I noticed the same condition occurs when you label a disk using gparted too.

I am also having problems auto mounting to a specific directory for USB sticks.

I think the best way is to just edit fstab, and make it like

mount /dev/sda1 /media/disk
mount /dev/sdb1 /media/disk-1

I am sure this isnt the correct format, but it is something similar to the regular fstab configs.

I have a USB stick in atm, and the device is /dev/sda1 according to fdisk -l.

Besides that, I dont think the add too much support for it.

---

