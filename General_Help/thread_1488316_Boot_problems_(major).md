---
title: "Boot problems (major)"
date: 2010-05-19
forum: General Help
---

### Post by TyPR124 on 2010-05-19
This is more of a Windows problem than a Linux one, but I am trying to fix it using Ubuntu Live CD. I don't have access to the computer right now, but I will tomorrow afternoon (I just spent a few hours trying to fix it, without any luck so far.)

Basically, my friend had a computer with failing hardware in it, and Vista installed. I got him another tower and put his HDD in it because he has a bunch of stuff he would like to keep. The hard drive looked like this

sda1 - ~10GB, Recovery (label Recovery, no actual recover stuff on there... no clue why)

sda2 - ~180GB, No label (had Vista installed on it, and all his stuff that he needs to keep)

sda5 - ~40GB, No label (had the remnants of an old installation on it, but didn't look important, and wasn't being used currently)


I installed XP on sda5, moved all the stuff he needed to sda5, and then went to format sda2. The format failed because it was set as the "System" drive, so (without thinking it through) I went into the XP cd and deleted the partition. And, of course, I also wiped out the ability of XP to boot.

First thing I thought of was, since it's installed on an extended partition, it can't boot from there to begin with, so if I move it to a primary it might work. Went into Ubuntu (Live CD) and 'moved' the partition from sda5 to sda3 (using sfdisk, I still have a backup of the original if needed, but everything seemed to have worked out.) I also changed the ID from F to 7 (to match the other two primary partitions. I will try changing it back to F tomorrow if I can't come up with anything else.)

That didn't help, so I went and tried to install GRUB, but it kept giving me an "Error 17. Unable to mount partition" for every partition on that HDD. So no GRUB apparently. I read somewhere that it may have been due to a problem with the flags in the partition table. If someone could verify this and tell me which flags need set in order to work, that would be very helpful.

Also, I tried setting sda3 to bootable, (before that, none of the partitions were) but that didn't do anything.

Every time I try to boot, I get a message saying "Boot Error". I'm not sure if that is coming from the BIOS, or Window's 'stage1' bootloader (I can find out tomorrow though, if it will help)

Now that I have been able to think about it more (since I've gotten home) I don't think GRUB would have helped anyhow since I'm pretty sure I've wiped out a part of Window's booting mechanism when I wiped the C drive (sda2)

Any suggestions? I would like to be able to do this without having to reinstall XP, but if it comes down to it I can backup the files to somewhere and do it again.


Sorry for the overly long post, and for it being more about Windows... if it should be moved to a more appropriate place, please do that.

Thanks

---

### Post by john newbuntu on 2010-05-20
So in the end it looks like you got XP on sda3.  It appears that the MBR that was last updated by Vista is pointing to la la land (sda2 ?) and hence the boot failure.
Assuming that the data on sda3 is ok, set the boot flag on sda3 partition and repair the VBR of sda3 and MBR of sda by running fixboot and fixmbr from the recovery console:
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

---

