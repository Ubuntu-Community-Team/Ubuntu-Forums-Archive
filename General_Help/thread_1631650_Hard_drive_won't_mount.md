---
title: "Hard drive won't mount"
date: 2010-11-26
forum: General Help
---

### Post by JohnElway on 2010-11-26
I just bought an WD external hard drive to back up all the data I have on my computer. After about 30 GB of the data was copied, it suddenly stopped and the following error message popped up:

```

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

The hard drive no longer mounts. Any idea what's happened?

---

### Post by napoleon3665 on 2010-11-26
well, im not 100% sure what happened, but if you still cant get it to mount, i suggest plugging it into a windows machine, let windows recognize it, and then "safely remove it". ive had many external hdd's and flash drives do this to me before and i cant quite figure out why...

---

