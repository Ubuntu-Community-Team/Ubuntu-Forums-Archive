---
title: "Error mounting volume"
date: 2012-03-06
forum: General Help
---

### Post by MichaelGld on 2012-03-06
After upgrading from 10.04 to 11.04, my external Firewire drive is not working. When I try to mount it, I get the following error:

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

```I am not running RAID. The drive is located at /dev/sdc1.
Any help would be greatly appreciated.

---

### Post by Gremlinzzz on 2012-03-06
"Error mounting: mount exited with exit code 13"

[http://ubuntuforums.org/showthread.php?t=1616666](http://ubuntuforums.org/showthread.php?t=1616666)

---

### Post by MichaelGld on 2012-03-07
> **Gremlinzzz said:**
> "Error mounting: mount exited with exit code 13"

[http://ubuntuforums.org/showthread.php?t=1616666](http://ubuntuforums.org/showthread.php?t=1616666)


That worked. Thanks for the help.

---

