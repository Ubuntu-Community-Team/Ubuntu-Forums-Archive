---
title: "parted script"
date: 2010-05-12
forum: General Help
---

### Post by warpig on 2010-05-12
Hi All,

Apologies if this has already been answered somewhere, but I couldn't find anything specific to my question.  I've got a parted command that I'm running on a few machines, but I need to specify the partition number (which you can do with fdisk).  The reason I'm using parted is because I'm dealing with large volumes (> 2.2TB) which fdisk doesn't support.  The command is:

parted --script -- $disk_device mkpart primary lvm 0 -1

where $disk_device is the physical disk.  Basically, I need to specify it as the fourth primary partition.  Any ideas?  Thanks in Advance!

Cheers,
Leigh

---

### Post by srs5694 on 2010-05-12
I don't know of a way to do that with parted; however, my sgdisk program, part of the [GPT fdisk](http://www.rodsbooks.com/gdisk/) package, will do the job, although you'll need two or three commands. If I understand what you're trying to do, the commands would be:

```

startSector=`sgdisk -f $disk_device`
endSector=`sgdisk -E $disk_device`
sgdisk --new=4:$startSector:$endSector --typecode=4:8e00 $disk_device

```

You could omit the call that sets startSector and instead use a fixed sector value, such as 2048. If the disk has absolutely no partition table on it at all, or if you want to wipe anything that already exists, you could add a call to "sgdisk -Z -g $disk_device" before those in order to wipe the disk out before proceeding.

---

### Post by warpig on 2010-05-12
Thanks for the info, I'll take a look and see if it fits our needs.

---

