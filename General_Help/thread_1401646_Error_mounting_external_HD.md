---
title: "Error mounting external HD"
date: 2010-02-08
forum: General Help
---

### Post by sombrancelha on 2010-02-08
Hello,

Today my external HD drive stopped being mounted correctly. When I plug it in the USB port, I get the following error message:

```

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

Other USB pendrives are working on my computer and this HD worked correctly on a Windows XP computer.
I am unsure on which of the proceedures suggested to take and how to perform them.

---

### Post by Claus7 on 2010-02-08
Hello,

I have almost the same problem after more or less a year of usage without any problem at all. And it seems that things are getting worse. Are you able at least to transfer some of your data to another disk? I'm looking on the issue to see what I 'll get, yet I think that the disk wants to give us some bad news if we do not act quickly.

I'll try to transfer my data and see what I can get...
edit:[http://ubuntuforums.org/showthread.php?t=1398800&highlight=input+output+error](http://ubuntuforums.org/showthread.php?t=1398800&highlight=input+output+error)
this might give you some insight

Regards!

---

### Post by sombrancelha on 2010-02-08
Thanks.

I installed ntfsprogs and ran ntfsfix. It now mounts the drive, but after a few seconds it stops responding. I'm currently trying to fix it with chkdsk on Windows.

---

