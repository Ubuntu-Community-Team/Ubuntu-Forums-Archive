---
title: "Windows HDD Failed - Trying To Recover Files - Ideas?"
date: 2010-04-26
forum: General Help
---

### Post by Roasted on 2010-04-26
I have an IDE hard drive here that belongs to somebody at work. I'm trying to do what I can to read any data on it and copy it off of the drive. I get this error:

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read vcn 0x1: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Is there anything I can do? I currently have the drive plugged in to a USB bridge to my Ubuntu 9.10 laptop. Any ideas?

---

