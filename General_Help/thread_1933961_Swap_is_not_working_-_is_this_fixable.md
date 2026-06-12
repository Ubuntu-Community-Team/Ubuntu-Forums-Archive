---
title: "Swap is not working - is this fixable?"
date: 2012-03-01
forum: General Help
---

### Post by ericus on 2012-03-01
Hi all! I've recently installed Ubuntu 11.10 on my Zenbook UX31, with encrypted /home during the install. From what I understand, that also encrypts /tmp and /swap.

It all worked just fine 'til recently when swap just won't mount. Upon boot  it says something like "The device /dev/mapper/cryptswap1 is not ready or present", just flashes by.

I've spent the night googling but unfortunately without success. Here is some output that might be of interest when solving this issue:

This is **/etc/fstab**. I have tried both lines without progress.
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=08ef2fb6-e268-443a-985d-b8a448e31a71 /               ext4    noatime,discard,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
#UUID=e2fefba8-1df5-43c4-9ac9-5922f0efd4f4 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

**sudo swapon -s** show no swap, so let's try to bring it to life:

**sudo swapon -a**
```
swapon: /dev/mapper/cryptswap1: stat failed: No such file or directory
```
Same error as above also occurs with the other fstab line (the on with the UUID).

**free -m**
```
             total       used       free     shared    buffers     cached
Mem:          3856        937       2918          0         29        492
-/+ buffers/cache:        415       3441
Swap:            0          0          0
```

**fdisk -l**
```
Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000db8f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   241881087   120939520   83  Linux
/dev/sda2       241883134   250068991     4092929    5  Extended
/dev/sda5       241883136   250068991     4092928   82  Linux swap / Solaris
```
Strange, fdisk can see the swap partition.

ls -l /dev/mapper
```
total 0
crw------- 1 root root 10, 236 2012-03-01 13:58 control
```

**In gparted it looks like this:**
[http://dl.dropbox.com/u/4375930/gparted.png](http://dl.dropbox.com/u/4375930/gparted.png)
I would guess that is shows up like that because it's encrypted and not mounted, right?

**cat /var/log/dmesg |grep swap** shows nothing at all.

**cryptsetup status cryptswap1**
```
/dev/mapper/cryptswap1 is inactive.
```

A simple solution would be to just erase it and create a new /swap -- but that would make my encrypted /home worthless.

Any ideas how to fix this? Just ask if you need more outputs or anything.
Thanks in advance,
Eric

---

### Post by Khayyam on 2012-03-01
Eric ...

This should be [opened as a bug](https://help.ubuntu.com/community/ReportingBugs) as this exact same problem was reported on this forum only a few days ago.

The device mapping needs to happen early in the boot process, and be allowed time to do so, so that prior to mounting anything these device mappings are available. Ubuntu, if its like Debian in this regard, uses 'sysv init' and AFAIK there is no way to have one init script depend() on another before it does its business.

On some other distributions these device mappings (specifically encrypted partitions) are setup by prompting the user for the passphrase, and this happens before checkfs or localmount are set to run. I imagine that user home dirs on Ubuntu are created as loopback devices which can be initiated at login, but swap would need to mapped prior to localmount, and it seems this isn't happening, at least not consistantly.

I'm somewhat guessing that this is the issue, but it seems consistant with what I know about dm-crypt and sysv init.

As for attempting to swapon, you can't, not until the dm-crypt swap has been mapped. I'm not sure if Ubuntu uses 'dm-crypt luks' (probably), or how the passphrase is generated, or if swap is wiped and re-created on each boot, so I'm not sure I can help in mapping it post-boot. The following would generally be the method:

```
cryptsetup luksOpen /dev/sdb5 cryptswap1
```

If it is a 'dm-crypt luks' device it would prompt you for the passphrase (which of course you don't have), if the bootprocess failed to (re-)create it then this may also fail .. so really I can't see how it can be worked around. Ubuntu needs to provide a more consistant method for doing these things, and so I can only suggest you file a bug report.

HTH in some way ... khay

---

