---
title: "Howto revive Ext HD"
date: 2011-06-23
forum: General Help
---

### Post by OldManRiver on 2011-06-23
All,

I have a SeaGate .5T external HD that I use for backups, downloads, etc.  As you know SeaGate drivers are pre-formatted to NTFS.

Well in the middle of downloads, the downloading U box did a reset, not sure why, but now the ext HD gives the message:> Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
Since I've converted to all U boxes how do I run the equivalent of "chkdsk /f" on this NTFS drive?

Thanks!

OMR

---

### Post by OldManRiver on 2011-06-28
All,

Though I got no response and still want to know how to do this in Ubuntu, I got it hooked to a win box and fixed it.

Thanks!

OMR

---

