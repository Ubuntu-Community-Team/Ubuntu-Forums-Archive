---
title: "Mount HFS+ on Ubuntu 6 Server Ed"
date: 2010-01-17
forum: General Help
---

### Post by napcae on 2010-01-17
Hey everybody!

I want to mount my hfs+ external harddrive..But it seems to be quite difficult..

I already added hfs and hfsplus to /etc/modules

After ```
sudo mount -t hfsplus -r /dev/sda /mnt/mac
```I just got

```
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```dmesg | tail shows

```
[  119.771566] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[  119.784541] sda: Write Protect is off
[  119.784561] sda: Mode Sense: 38 00 00 00
[  119.784572] sda: assuming drive cache: write through
[  119.786886]  sda: sda1
[  120.172094] sd 2:0:0:0: Attached scsi disk sda
[  120.277615] sd 2:0:0:0: Attached scsi generic sg0 type 0
[  574.934701] hfs: can't find a HFS filesystem on dev sda.
[  771.258256] hfs: unable to find HFS+ superblock
[  778.347846] hfs: unable to find HFS+ superblock

```
Hope somebody can help me..:D

---

