---
title: "/etc/fstab does not show DVD drives"
date: 2011-06-19
forum: General Help
---

### Post by iEthan on 2011-06-19
I'm trying to follow this tutorial for setting up DVD Decrypter under WINE: [http://ubuntuforums.org/showthread.php?t=27369](http://ubuntuforums.org/showthread.php?t=27369)

I run /etc/fstab, but I cannot see a DVD drive, I only see this.

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=97a88fb7-5066-4f3c-b1bf-43f06e44cc09 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda6 during installation
UUID=f9f8bbb6-cd88-41ed-bb38-48086b4fb546 none            swap    sw              0       0

```

How do I make it see the drive?

---

### Post by nomko on 2011-06-19
Not needed to show CD/DVD drives in fstab.

As example, this is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=84b9ede3-f8e2-42bf-81a5-5e55d757caaa /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=b7fc1fa0-aab1-486b-b6c9-dd31b62805c5 none            swap    sw              0       0

# 1 gigabyte HDD
UUID=9b41fcd5-9f84-4ee7-a8c6-bd6f2efd49fe     /media/NNTPGrab     ext3     defaults,relatime     0     2
```

---

### Post by mc4man on 2011-06-19
Forget those instructions - just install DVDD, (when asked if it should ck. for updates say no.  - macrovision now owns it

First time you run it it won't locate your drive(s) - just open - Tools > Settings > I/O and change to the first choice as seen in screen.
Your drive(s) will be found fine then

Ex. from DVDD log
> I 09:59:52 DVD Decrypter Version 3.5.4.0 started!
I 09:59:52 Microsoft Windows XP Professional (5.1, Build 2600 : Service Pack 3)
I 09:59:52 Initialising SPTI...
I 09:59:52 Searching for SCSI / ATAPI devices...
W 09:59:52 No devices detected!
W 10:00:14 I/O Interface has been changed!
I 10:00:14 Shutting down SPTI...
I 10:00:14 Initialising ASPI...
I 10:00:14 Searching for SCSI / ATAPI devices...
I 10:00:14 Found 1 DVD-ROM and 1 DVD±RW!


---

### Post by iEthan on 2011-06-19
> **mc4man said:**
> Forget those instructions - just install DVDD, (when asked if it should ck. for updates say no.  - macrovision now owns it

First time you run it it won't locate your drive(s) - just open - Tools > Settings > I/O and change to the first choice as seen in screen.
Your drive(s) will be found fine then

Ex. from DVDD log

Ah, now it's working! Thanks a lo!

---

