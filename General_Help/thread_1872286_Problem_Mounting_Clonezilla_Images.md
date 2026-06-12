---
title: "Problem Mounting Clonezilla Images"
date: 2011-10-30
forum: General Help
---

### Post by sardaukar123 on 2011-10-30
> **nutria007 said:**
> finally it worked!

```
sudo ntfs-3g /path/to/hda2.img /mnt
```

Hi,

I got as far as partclone.restore.
As described by nutria007 mount refuses to work:
> Failed to read last sector (2886023167): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/loop2': Invalid argument
The device '/dev/loop2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
In my case ntfs-3g is not working either:
> ntfs_mst_post_read_fixup: magic: 0xb644b444  size: 1024  usa_ofs: 22003  usa_count: 30397: Invalid argument
Record 0 has no FILE magic (0xb644b444)
Failed to load $MFT: Input/output error
Failed to mount '/media/af6f7061-c4bf-41dc-a66a-6746aca61768/hd1.img': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.The hexdump of the first 1024 bytes in the image file are (maybe this helps...) in the attachment.
Thank you for any support

---

### Post by oldos2er on 2011-10-30
Post moved to its own thread.

---

