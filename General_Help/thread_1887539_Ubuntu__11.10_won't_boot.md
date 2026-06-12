---
title: "Ubuntu  11.10 won't boot"
date: 2011-11-27
forum: General Help
---

### Post by anthonykr on 2011-11-27
Hi all,

I've been using 11.10 for a while with no problems, but when I went to boot it today I got a series of messages of the form:

udevd[101]: timeout: killing '/sbin/blkid -o udev -p /dev/sda5' [241]

and then finally:

udevd[101]: '/sbin/blkid -o udev -p /dev/sda5' [241] terminated by signal 9 (Killed)

and then the system freezes.

If I boot in recovery mod, but then get another message, that seems to be on a loop, of the form:

ata1.00: status: { DRDY ERR }
ata1:00: error: { UNC  }
ata1.00: configured for UDMA/133

and also:

ata1.00: failed command: READ FPDMA QUEUED

I have tried to boot with a USB stick (got the the stage of seeing the 'not a COM32 image', but pressed tab and typed 'live') but this seems to freeze as well...

Any advice would be VERY much appreciated! 

Thanks!

---

### Post by dabl on 2011-11-27
> **anthonykr said:**
> 

ata1.00: status: { DRDY ERR }
ata1:00: error: { UNC  }
ata1.00: configured for UDMA/133

and also:

ata1.00: failed command: READ FPDMA QUEUED



Those errors come from the ata hard disk driver.  There's a problem with your hard drive, or the filesystem on it.

Two things to try:

- fsck the OS partition

- use smartmontools (or a GUI version such as comes on the Parted Magic Live CD) and check the condition of your hdd

---

### Post by anthonykr on 2011-11-27
Thanks very much

I booted in recovery mode, and dropped to the root prompt, typed 'fsck' and then this just started the loop of errors again (the DRDY ERR, {UNC} and failed command: READ FPDMA QUEUED errors that I mentioned in the original post).

Is there any other way to do this?

---

### Post by anthonykr on 2011-11-27
It seems that using the fsck option from the recovery prompt, or trying it from the command line, or using the other (remount?) option in recovery mode ALL start this same error loop...

---

### Post by dabl on 2011-11-27
You can't fsck a mounted partition. You'll have to boot a Live CD or a Live USB stick, and then fsck the partition where your OS is.

Or if you have something like a Parted Magic Live CD, or GParted Live CD, you can boot that and use the tools that are on it.

---

### Post by oldtimer7777 on 2011-11-27
Do you hear any new loud clicks when the hard drive is running? 

It could be time to replace out that hard drive.

> **anthonykr said:**
> Hi all,

I've been using 11.10 for a while with no problems, but when I went to boot it today I got a series of messages of the form:

udevd[101]: timeout: killing '/sbin/blkid -o udev -p /dev/sda5' [241]

and then finally:

udevd[101]: '/sbin/blkid -o udev -p /dev/sda5' [241] terminated by signal 9 (Killed)

and then the system freezes.

If I boot in recovery mod, but then get another message, that seems to be on a loop, of the form:

ata1.00: status: { DRDY ERR }
ata1:00: error: { UNC  }
ata1.00: configured for UDMA/133

and also:

ata1.00: failed command: READ FPDMA QUEUED

I have tried to boot with a USB stick (got the the stage of seeing the 'not a COM32 image', but pressed tab and typed 'live') but this seems to freeze as well...

Any advice would be VERY much appreciated! 

Thanks!

---

### Post by anthonykr on 2011-11-27
Thanks for the comments guys,

Firstly, thankfully there have been no loud clicks coming from the hard drive.

Secondly: I can't boot into another version of ubuntu using the USB, I get to the state where it tells me that it isn't a COM32r image, press tab to see the options and then type live... it adjusts the resolution and freezes.

I also had a gparted usb to hand, and tried to boot into that, I get to the state where I see:

SYSLINUX 4.04 EDD 2011-04-18 Copyright (C) 1994-2011 H. Peter Anvin et al

and then I just see a blinking cursor below this, and no further progress, it seems stuck here.

---

### Post by anthonykr on 2011-11-27
Just as a follow up: I managed to get to the gparted options screen on another attempt, although when I tell it to boot into gparted it just loops the same old error messages from previous comments :(

---

### Post by dabl on 2011-11-27
> **anthonykr said:**
> Just as a follow up: I managed to get to the gparted options screen on another attempt, although when I tell it to boot into gparted it just loops the same old error messages from previous comments :(

You need to make a Parted Magic Live CD or Live USB stick:  [http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)

You need to use that, so your damaged drive/partition is not mounted when you fsck it and check the drive condition.

---

### Post by amorris28 on 2012-07-14
I think I'm having that same problem, but I'm not sure how to go about trying the solutions that have been posted in this thread.

Currently, I'm running Windows 7 and attempting to replace it with Ubuntu. I have a Ubuntu boot disc and I installed it fine on my other computer. When I restart this computer and boot from the Ubuntu disc, I get the same "terminated by signal 9 (Killed)" error. It stops at that point and I can input commands at which point I just ctrl+alt+del to reboot.

Is this a problem with my hard drive and how can I check?

---

