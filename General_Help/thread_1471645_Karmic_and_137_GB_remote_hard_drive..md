---
title: "Karmic and 137 GB remote hard drive."
date: 2010-05-03
forum: General Help
---

### Post by Dyffo on 2010-05-03
I am running Karmic and have a 137GB remote Hard Drive that I use for storing Video files. This has stopped working for some reason - displaying the error as shown below. Any ideas on how to resolve this - it won't work on Windows either.


Error mounting: mount exited with exit code 13: Inode is corrupt (5): Input/output error
Failed to mount '/dev/sdf1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.****

---

### Post by mikewhatever on 2010-05-03
Hard drives have a life span. I begins, and then it ends, nothing you can do about it. Have you tried formatting it in Windows?

---

### Post by Dyffo on 2010-05-04
> **mikewhatever said:**
> Hard drives have a life span. I begins, and then it ends, nothing you can do about it. Have you tried formatting it in Windows?

Nothing wrong with the Hard Drive - I have a corrupt file hidden in there - I know which one it is but can't get to it. I have tried to understand the dmraid documentation  but am totally confused .

---

### Post by Dyffo on 2010-05-04
Solved - I reformatted the drive in Ubuntu using the Disc Utils. Fortunately I had a back up of All Videos so lost nothing.

---

