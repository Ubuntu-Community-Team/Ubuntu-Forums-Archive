---
title: "uable to mount USB-Stick"
date: 2010-10-27
forum: General Help
---

### Post by nearlymagicman on 2010-10-27
When i plugged my USB-Stick in i got the following message:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Well, i would try to follow the steps but sadly those involve windows and that is a problem, i don't use windows anymore. Killed my last Windows yesterday.
So how can i fix the problem? Won't be to bad if i have to format the stick for a quick solution but i don't now how to access the stick at all.

It is a 4GB Flashdrive of transcend

thanks for your help

---

### Post by Verbeck on 2010-10-27
can you force mount it?
```

sudo mkdir /media/flashdrive 
sudo mount /dev/sdb1 /media/flashdrive -o force
```

---

### Post by nearlymagicman on 2010-10-27
no i couldn't even do that, but now a neighbor helped me out, he still uses windows und so i could backup the stick and format it, but i am still confused how this could happen, i didn't do anything but plugging it in.

---

