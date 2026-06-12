---
title: "mdadm device or resource is busy"
date: 2009-12-02
forum: General Help
---

### Post by piusvelte on 2009-12-02
*I abandoned this approach*

Hi,

I'm trying to move to a software RAID1, will up and running. I followed [this simple guide]("http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-lvm-system-incl-grub-configuration-debian-lenny").

I started running from a single drive, using the defaults from the server installation:
```

/dev/sdb1 ext3
/dev/sdb2 Extended
/dev/sdb5 swap

```

I copied my partition table over to the second drive (/dev/sda), created the raid1 using sda and missing, updated grub, and am running off of the degraded raid1. I changed the partition type on /dev/sdb1 to "fd" add ran:
```

mdadm --add /dev/md0 /dev/sdb1

```
The response was:
```

mdadm: Device or resource is busy

```

I tried...
```

lsof |grep sdb

```
...nothing.

I checked mount, but sdb wasn't listed.

I tried swapoff /dev/sdb5.

I tried umounted /dev/sdb1 through gparted, but it said it couldn't find the mountpoint.

I tried uninstalling mdraid, but it's not installed.

Here's the current list from fdisk:
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009df38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19174   154015123+  fd  Linux raid autodetect
/dev/sda2           19175       19929     6064537+   5  Extended
/dev/sda5           19175       19929     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9ddd9dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19174   154015123+  fd  Linux raid autodetect
/dev/sdb2           19175       19929     6064537+   5  Extended
/dev/sdb5           19175       19929     6064506   82  Linux swap / Solaris

```

Yes, the new drive is 250G, and the drive that I started from is 160G, so I'm wasting space.

I've read about people trying to fix this from a live cd, but making things worse. I imagine that I'd want to create the array on the live cd, using the missing option again, mount it, chroot to it, and try to add /dev/sda. Is that correct?

What else can I try?

Thank you!

---

