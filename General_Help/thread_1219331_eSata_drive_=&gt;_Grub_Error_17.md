---
title: "eSata drive =&gt; Grub Error 17"
date: 2009-07-21
forum: General Help
---

### Post by doas777 on 2009-07-21
hello all,

I recently plugged a new external hard disk into the eSata port on the back of my PC, and found that while it was plugged in, I could not boot successfully, recieving a Grub 17 error. unplug the drive, and everything boots fine.

I'm guessing that plugging the drive in has altered my Sata port order or my /dev assignments, but all my internal drives are listed in the fstab as UUID devices not /dev/sdxx, so changing a sdxx identity shoudln't be a problem right? grub does load initially, so I have to assume that my MBR disk is still the first in the chain.

so assuming that this drive will not always be present on my system, what do you folks think? any ideas on getting this working?

---

### Post by Janeway on 2009-07-21
Hi,

I think that is caused by the new partition table grub finds on startup, because external sata drives do net behave different than internals.

You should use gparted to make sure there is no active partition marked on the external drive.

You could also try to run a grub-update when the external drive is plugged in. If there is no active partition that should not cause problems when not having plugged in the external drive.

Regards
Janeway

---

### Post by doas777 on 2009-07-21
> **Janeway said:**
> Hi,

I think that is caused by the new partition table grub finds on startup, because external sata drives do net behave different than internals.

You should use gparted to make sure there is no active partition marked on the external drive.

You could also try to run a grub-update when the external drive is plugged in. If there is no active partition that should not cause problems when not having plugged in the external drive.

Regards
Janeway

Thanks for the reply. I came to the same conclusion, so I hooked it up over usb, and partitioned and formatted (ext4). Unfortunately, transfer speed seems to be only about 33 MB/s over usb (it *should* be usb2; have to check) to sata2. I just checked fdisk and the only disks with boot attributes are internal. Still no boot with esata though.

I'll look into grub-update right now. I had kinda assumed that if grub knew about my device, it would wreak havok if not present, but it may well be that by not keeping it in the loop, i acheived that which i had sought to avoid. ironic wot? 

Thanks again, I'll let you know how it works out.
franklin

---

### Post by doas777 on 2009-07-21
I'm afraid that i have been unable to get to a point where i can run update-grub while the drive is connected. live cd can't find /boot.

i did confirm that my eSata device is being assigned /dev/sda and pushing all the other drives down a letter. that may be messing up the hd(2,0) setting for ubuntu.

I think now i'm going to try to convert my menu.lst to use UUID instead of /dev names, and try updating grub again. then theoretically, it shouldn't care if name changes. but i don't think I can uuid the windows partition.

any ideas anyone? think I'm heading the right direction?

---

### Post by doas777 on 2009-07-21
ok, so my menu.lst uses only UUIDs (commented xp for the moment), and updated grub with the drive unplugged but still get 17 errors if the esata drive is plugged back in.

---

### Post by Dejai on 2009-07-21
Seems to be a common problem with Ubuntu Machines there are a lot of other posts around. I have even had this error before, (I have done a fair bit of work with grub in the past as well). Pretty much "17 : "Invalid device requested" This error is returned if a device string is recognizable but does not fall under the other device errors."

Here is some form of solution in a previous post [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

If it isn't what ya looking for please post back. Not using the Phoenix AwardBios by any chance?

---

### Post by doas777 on 2009-07-22
> **Dejai said:**
> Seems to be a common problem with Ubuntu Machines there are a lot of other posts around. I have even had this error before, (I have done a fair bit of work with grub in the past as well). Pretty much "17 : "Invalid device requested" This error is returned if a device string is recognizable but does not fall under the other device errors."

Here is some form of solution in a previous post [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

If it isn't what ya looking for please post back. Not using the Phoenix AwardBios by any chance?

interesting. my abit IP35 Pro does have a Phoenix bios. I had seen this thread, but since I don't have an asus board, I gave it a pass. I went back and attempted to set the recommended bios settings but they were already set by default, so i don;'t think that is the answer. any other ideas?

---

