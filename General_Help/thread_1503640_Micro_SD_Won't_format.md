---
title: "Micro SD Won't format"
date: 2010-06-07
forum: General Help
---

### Post by james.exe on 2010-06-07
I've been trying to format my micro sd, but for some reason I can't get windows or linux to do so. I can still view the files on it through windows 7, but I get the following error whenever I try to browse the files in ubuntu.
```
Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x454c4946  size: 1024  usa_ofs: 48  usa_count: 65: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x454c4946  size: 1024  usa_ofs: 48  usa_count: 1: Invalid argument
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```
Does anyone know of any way I can save my micro?

---

