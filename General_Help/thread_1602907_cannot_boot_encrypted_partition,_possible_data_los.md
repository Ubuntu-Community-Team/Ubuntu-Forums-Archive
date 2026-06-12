---
title: "cannot boot encrypted partition, possible data loss"
date: 2010-10-22
forum: General Help
---

### Post by fishooter on 2010-10-22
Hello,

I have ubuntu 10.04 and while I boot the system, it outputs something like: "fsck: unrecoverable error". Through live cd, I am not even able to mount the /home dir, which is encrypted:

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda9,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```so I ran dmesg:

```
ubuntu@ubuntu:~$ dmesg | tail -20
[   86.459993] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[   92.550244] Skipping EDID probe due to cached edid
[   93.020242] Skipping EDID probe due to cached edid
[   93.490062] Skipping EDID probe due to cached edid
[   93.966500] Skipping EDID probe due to cached edid
[  138.480271] Skipping EDID probe due to cached edid
[  138.950272] Skipping EDID probe due to cached edid
[  141.240241] Skipping EDID probe due to cached edid
[  141.712739] Skipping EDID probe due to cached edid
[  142.190238] Skipping EDID probe due to cached edid
[  142.453086] Skipping EDID probe due to cached edid
[  142.930357] Skipping EDID probe due to cached edid
[  143.412849] Skipping EDID probe due to cached edid
[  143.942750] Skipping EDID probe due to cached edid
[  151.840063] Skipping EDID probe due to cached edid
[  152.360089] Skipping EDID probe due to cached edid
[ 1086.550313] Skipping EDID probe due to cached edid
[ 1766.736966] cfg80211: Found new beacon on frequency: 5240 MHz (Ch 48) on phy0
[ 2365.050066] Skipping EDID probe due to cached edid
[ 2526.805261] JFS: nTxBlock = 8192, nTxLock = 65536

```Any idea what to do next?

Thanks a lot

---

