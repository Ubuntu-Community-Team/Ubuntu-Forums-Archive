---
title: "NTFS Hard Drive fstab issue"
date: 2010-05-06
forum: General Help
---

### Post by false_chicken on 2010-05-06
I have a NTFS hard drive in my fstab like this:

/dev/sdc1      /media/More_Storge ntfs-3g    default  0   0

And it has worked for a few days. But just a few minutes ago I started up and got a message while booting saying there was an error mounting it and if I wanted to skip mounting or do something manually. So I said skip and tried running "sudo mount -a"
and it gave me this:

NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

I am confused because it worked for a few days until about five minutes ago when I started up. I can still click on the drive in nautilus and it will mount and I can see all my files. Any suggestions? Thanks.

EDIT: I figured out the issue. For some reason the disk changed from sdc1 to sdb1. Anyone know what would cause that?

---

### Post by John Bean on 2010-05-06
I don't like the sound of that. If you have access to Windows (why else use NTFS?) I'd strongly recommend using chkdsk on a Windows machine to find and/or repair the NTFS filesystem before attempting to write to it. It's probably a good idea to back it up first, just in case.

---

### Post by mcduck on 2010-05-06
> **false_chicken said:**
> 
EDIT: I figured out the issue. For some reason the disk changed from sdc1 to sdb1. Anyone know what would cause that?
Most common reason is that you have a removable drive plugged in. Although some motherboards are known to detect hard drives pretty much every time in different order.

Anyway, this is the reason why it's recommended to use UUID (or label) instead of the device name when mounting drives. "/dev/sdc1" would point to first partition of third detected drive, whichever drive that ight be at the time, while a specific UUID points to a specific partition regardless of how the drives are detected.

---

### Post by nitstorm on 2010-05-06
+1 mcduck

```
sudo blkid
```
Note the UUID of the drive in question

add it to the fstab

> /dev/sdc1      /media/More_Storge ntfs-3g    default  0   0
replace /dev/sdc1with the uuid  and the line should look like
```
UUID=XXXXX      /media/More_Storge ntfs-3g    default  0   0 ##replace XXXX with the UUID you got from the previous command
```

Proper guides(refer to this before you edit fstab):

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by dino99 on 2010-05-06
force a "fsck" on next reboot:

sudo shutdown -F -r now

---

### Post by false_chicken on 2010-05-06
Thanks for the replies! Will use UUID for now on.

---

