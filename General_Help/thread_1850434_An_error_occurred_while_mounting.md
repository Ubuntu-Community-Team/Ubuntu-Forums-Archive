---
title: "An error occurred while mounting /"
date: 2011-09-26
forum: General Help
---

### Post by thewinchester on 2011-09-26
Ok, this has me stumped and there's just too many answers none of which seem to be helping. Also a n00b, so chances are I don't know how to find the right one.

Ubuntu 11.04, 64-bit install, only OS installed.

For some reason, my server rebooted this evening whilst playing back a video via Twonkyserver. Upon reboot, the following error message appeared:

```
An error occurred while mounting /
```

Along with S to skip, or M for manual recovery mode.

Have not been able to resolve this problem, so any assistance on how to diagnose and recover from this would be greatly appreciated.

**Steps to fix**

[LIST=1]
[*]Have tried booting into recovery mode and update the GRUB bootloader but no change.
[*]Have gone into maintenance shell, and run fdisk -y on /dev/sdc3 (where my root partition is), and no errors or indicators of what is wrong are yielded excepting that partition in question was not cleanly unmounted.
[*]Have attempted to boot my installer from USB, and no recover/repair option seems to be available.
[/LIST]

**blkid output**
```
/dev/sda1: LABEL="simmer-e" UUID="blah (having to type this out, so won't type it all here)" TYPE="ntfs"
/dev/sdb1: LABEL="simmer-f" UUID="blah" TYPE="ntfs"
/dev/sdc1: UUID="blah" TYPE="swap"
/dev/sdc3: UUID="blah" TYPE="ext2"
/dev/sdc5: LABEL="disk-1" UUID="blah" TYPE="ext2"
```

**/etc/fstab output**
```

proc		/proc				proc	nodev,noexec,nosuid			0	0
UUID=blah	/				ext2						0	1
UUID=blah	none				swap	sw					0	0
UUID=blah	/media/disk-1			ext2						0	0
UUID=blah	/media/simmer_e			ntfs-3g	defaults,uuid=1000,locale=en_US.utf8	0	0
UUID=blah	/media/simmer_f			ntfs-3g	defaults,uuid=1000,locale=en_US.utf8	0	0

```

---

### Post by searchfgold6789 on 2011-09-26
11.04 uses ext4, not ext2, you must have had Ubuntu for a while, or there must be something wrong with your fstab... Verify that the info in your fstab is correct by using GParted and a Live CD.
However, you can rest easy: it's got nothing to do with grub. By the time you get this error Linux will have booted successfully, it's just trying to run scripts that get you from things like ```
find (hd0,0) and run the 0s and 1s you find there
```to```
mount a filesystem and load, parse and run the files you find there
```Also check the filesystem, there are guides online.

---

### Post by thewinchester on 2011-09-27
> **searchfgold6789 said:**
> 11.04 uses ext4, not ext2, you must have had Ubuntu for a while
Yes, machine was previously running v10.

> **searchfgold6789 said:**
> Verify that the info in your fstab is correct by using GParted and a Live CD.<snip>

Also check the filesystem, there are guides online.
I know what a Live CD is, know of GParted, but have no idea how to verify fstab is correct using GParted.

Let's be perfectly honest, my understanding of fstab is more than a little limited.

GParted is able to see all the drives, the information it sees matches up with fstab. As to checking the file system, was able to run the GParted check feature on the / partition (as well as the 900GB partition also on that disk), and no errors were reported. The outcome remains the same and problem unresolved.

Is that what you meant by this, or is there something else I'm supposed to do? If so, what specifically is it, and could you please point me towards to a guide on how to achieve it.

---

### Post by zhiansun on 2011-10-31
I run into this problem recently when using ubuntu on VM virtualbbox and it stop me to use my linux system. Does anyone have an idea how to fix it?
 
Thank you!

---

