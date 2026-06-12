---
title: "Unable to mount TI106033W0C (Bad sectors)"
date: 2011-11-09
forum: General Help
---

### Post by Name0 on 2011-11-09
I can't get this drive to boot in windows or ubuntu im using the live cd because its the most i can do to fix stuff like this. I can't find a way to fix this problem! i keep trying to run chkdsk and i did on windows recovery disk and it said unable to read every sector it fixed some and got to 11% and froze.

Some help would be great :)

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by Name0 on 2011-11-09
Bump..

No idea?

---

