---
title: "Can't mount location"
date: 2011-08-05
forum: General Help
---

### Post by JamieEP on 2011-08-05
Windows recently decided to hang before it booted, so I'm using an Ubuntu livedisk to access some files. It tells me it's unable to mount

```
UNABLE TO MOUNT LOCATION
Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```I tried sudo fdisk -l, and here's the output

```
Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

Has anyone got any ideas?

Many thanks.

---

### Post by syntr on 2011-08-05
Well, I think that the message you're getting is very descriptive. Your partition likely got corrupted when Windows went down unexpectedly. You're going to want to boot a Windows recovery DVD and run 

```
chkdsk /f
```

---

