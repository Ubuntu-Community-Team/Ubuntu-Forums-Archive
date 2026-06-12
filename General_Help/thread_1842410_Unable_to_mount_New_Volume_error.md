---
title: "Unable to mount New Volume error"
date: 2011-09-11
forum: General Help
---

### Post by 8ER on 2011-09-11
hi im running ubuntu 11.04

once i plug my external usb hard drive i get the following error:
> 
Unable to mount New Volume

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
what should i do?

---

### Post by hydruid on 2011-09-11
Ubuntu is unable to mount the usb drive because it needs to be cleaned or it is bad.

Open Disk Utility (System->Administration->Disk Utility)

Try the "Check Filesystem" option first, if that doesn't work, try "Format Drive"

**WARNING: formating the usb stick will erase all data on it**

---

