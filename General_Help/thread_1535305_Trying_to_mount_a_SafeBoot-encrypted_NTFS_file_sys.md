---
title: "Trying to mount a SafeBoot-encrypted NTFS file system"
date: 2010-07-20
forum: General Help
---

### Post by gradysghost on 2010-07-20
My employer requires that all portable devices have their entire disks encrypted with SafeBoot.  Windows XP on this particular machine has borked itself after a motherboard replacement (I guess it doesn't know how to react to a changed mobo serial and just load the existing installed drivers for the identical piece of hardware it had before).

So now I need to nuke WinXP and reinstall.  But I need to back up the user's data beforehand.  Unfortunately, part of Windows' epic bork involves not loading any network drivers and being unable to control USB hubs.  Therefore, I can't back up the data to a USB drive, nor can I back it up to a flash drive.  I don't have any CDs or DVDs with me to test disc burning, but I also don't think there's any disc burning software on the machine, so it will probably be a futile effort when I try tomorrow.

So I thought I would try booting to a live Ubuntu (I'm using Karmic) from a flash drive.  I can boot just fine, and all hardware works just fine in Ubuntu, unlike in borked WinXP.  But I can't mount the drive that contains the data I need to back up because that disk is encrypted in its entirety by SafeBoot.

gparted sees the file system on the disk as "unknown".  I have tried mounting it as NTFS to no avail, and even when I give it the force option (which I know isn't really designed for this type of situation, but I thought I'd try) , I get a negative response from mount.  For example:

```
mount -t ntfs -o force /dev/sda2 /media/windows

NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

The disk does have two partitions; one holds Windows while the other holds the Dell recovery partition.  I may attempt an OS recovery using this method tomorrow, but I'm really afraid that it's an image, not an installer, and I may inadvertently lose the user's data.  It's far more preferable to mount the partition and back the data up to the network or at least to a USB drive where I know the data lives somewhere off the device I'm about to format.

I know the problem is because SafeBoot has /dev/sda2 encrypted.  It makes perfect sense.  That's what SafeBoot is designed to do.  I have credentials to decrypt the device (which amounts to activating a very low-level driver that dynamically decrypts data as required), so is there any way to activate that driver in Ubuntu?  Can I mount that device in any way, provided I have the appropriate creds to unlock the driver?

Any help or ideas would be much appreciated.  Thanks in advance.

---

