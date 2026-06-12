---
title: "Promblem - Mounting Extunal Hard Drive"
date: 2011-02-18
forum: General Help
---

### Post by B.Wilko on 2011-02-18
I have been using my Extunal 160gb hard drive for a while, as I've got an Dell Insperion 910 mini, and the hard drive on it is only 8gb. The problem started yesterday, I was using my Ex Hard Drive and then all of a sudden it stopped working then I hard it spinning like they do, and then it pops up with the following problem.

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Is there anyway to fix it with out wiping the data off it, I have got use of Windows XP if needed but I do like using it any longer as I've had many problems with windows, mainly be BSOD and Virus that you can't get rid of. So thats why I'm using ubuntu now.

So can anyone help me with this problem, but I NEED THE DATA!!

---

### Post by jerrrys on 2011-02-20
i think i would first try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and see if partitions are a issue

---

