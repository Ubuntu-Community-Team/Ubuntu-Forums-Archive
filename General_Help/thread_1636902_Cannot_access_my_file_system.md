---
title: "Cannot access my file system"
date: 2010-12-03
forum: General Help
---

### Post by IceblueGen3 on 2010-12-03
I come to you guys in desperation once again.

I was running some programs on Thursday and also installing something via the software center when I started getting strange errors. Then I kept getting told that the file system was read only (when I tried to save my work in the applications and while installing software). I clicked the restart button and got a blank popup (no restart or cancel buttons). So I press the power button and it shutsdown but quicker than usual. Power is back up and it goes to busybox.

Ok so I think this is easy to fix, just boot off CD open gparted and perform a check on the filesystem. It happened before and this solved it. But when I opened gparted and tried to check the disk I get:[INDENT]GParted 0.6.2
 Libparted 2.3
    Check and repair file system (ext4) on /dev/sda5  00:00:00    ( ERROR )
calibrate /dev/sda5  00:00:00    ( SUCCESS )
path: /dev/sda5
start: 2048
end: 162150399
size: 162148352 (77.32 GiB)
check file system on /dev/sda5 for errors and (if possible) fix them  00:00:00    ( ERROR )             e2fsck -f -y -v /dev/sda5
Filesystem mounted or opened exclusively by another program?
      e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda5
            ========================================

[/INDENT]The disk is not mounted or in use at all. I even placed it in an external enclosure and tried to check it from their but get the same error.
If I run the disk utility and click the "check filesystem" option it says "File system is NOT clean".

I've tried fsck and it also says it is in use. So what do I do now?

The drive is partitioned in 3:
1. Ext4 file system which I cannot access (contains my installation and documents, etc)
2. Swap Space
3. NTFS partition

The NTFS partition is fully functional and can be mounted and accessed without errors. The Ext4 does not even mount.

Can somebody please assist with this. Everything I need is on this drive. Thanks

---

### Post by dcstar on 2010-12-04
> **IceblueGen3 said:**
> 
.........
Ok so I think this is easy to fix, just boot off CD open gparted and perform a check on the filesystem. It happened before and this solved it. But when I opened gparted and tried to check the disk I get:[INDENT]GParted 0.6.2
 Libparted 2.3
    Check and repair file system (ext4) on /dev/sda5  00:00:00    ( ERROR )
calibrate /dev/sda5  00:00:00    ( SUCCESS )
path: /dev/sda5
start: 2048
end: 162150399
size: 162148352 (77.32 GiB)
check file system on /dev/sda5 for errors and (if possible) fix them  00:00:00    ( ERROR )             e2fsck -f -y -v /dev/sda5
Filesystem mounted or opened exclusively by another program?
      e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda5
.........
Do this in a terminal using the Live CD:
```
sudo umount /dev/sda5
sudo e2fsck -f -y -v /dev/sda5
```

---

### Post by IceblueGen3 on 2010-12-04
> **dcstar said:**
> Do this in a terminal using the Live CD:
```
sudo umount /dev/sda5
sudo e2fsck -f -y -v /dev/sda5
```

I get:
```

ubuntu@ubuntu:~$ sudo umount /dev/sda5
umount: /dev/sda5: not mounted
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda5
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
```

---

### Post by IceblueGen3 on 2010-12-04
Ok problem solved.

I created an additional partition and planned to try to image the drive across, but during the process also noticed that there was no "boot" flag set on the original partition and I set it. I couldn't get the partition to copy across but when restarted the PC everything was working again.

Still strange I couldn't get access to the drive before this was set.

Thanks though.

---

