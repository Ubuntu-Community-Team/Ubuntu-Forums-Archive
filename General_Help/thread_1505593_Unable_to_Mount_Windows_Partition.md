---
title: "Unable to Mount Windows Partition"
date: 2010-06-09
forum: General Help
---

### Post by UnknownDiety on 2010-06-09
```
ntfs_attr_pread_i: ntfs_pread failed:  Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS  is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID  hardware. In the first case run chkdsk /f on Windows
then reboot  into Windows twice. The usage of the /f parameter is very
important!  If the device is a SoftRAID/FakeRAID then first activate
it and mount  a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1).  Please see the 'dmraid' documentation
for more details.
```

Everytime I try to mount it; I get that error.

I ran the chkdsk /f

It said, "Windows hasn't found any problems." or something to that effect.

Anybody can help me to fix this?

---

