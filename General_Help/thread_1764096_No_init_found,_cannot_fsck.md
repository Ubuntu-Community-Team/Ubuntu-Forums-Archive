---
title: "No init found, cannot fsck"
date: 2011-05-21
forum: General Help
---

### Post by jcoglan on 2011-05-21
I have a Dell Mini 12 running what I think is Ubuntu 10.10 Netbook Remix. It won't boot all of a sudden, saying 'No init found'. I've been through [http://ubuntuforums.org/showthread.php?t=1728611](http://ubuntuforums.org/showthread.php?t=1728611), which is VERY close to my problem but I cannot get Disk Utility to work when running off my Live USB. Asking it to check the hard drive results in it telling me the filesystem is 'not clean'.

What's my next move?

---

### Post by jcoglan on 2011-05-21
I should also mention that gparted is refusing to check the drive, saying:

e2fsck -f -y -v /dev/sda1
Filesystem mounted or opened exclusively by another program?

The filesystem is not mounted, but gparted's 'Unmount' command is greyed out. umount says it's not mounted. /dev/sda1 does not appear in the output of lsof.

Please help as I lose a valuable test machine with a lot of dev work on it if it's dead.

---

### Post by Rubi1200 on 2011-05-21
Is Ubuntu the only operating system on the machine?

What, to the bust of your knowledge, might have caused this? 
Common causes include hard shutdowns, battery failure, failed updates/upgrades etc.

Have you tried booting into recovery mode or an older kernel?

What effect does turning off swap have on the LiveUSB as far as trying to unmount the damaged partition? 
Right-click > Swapoff

What does the output of the following command show?

```
lsof | grep sdXY 
```
where XY represents the partition e.g. sda1

Sorry for all the questions, but we need as much information as possible to try and help you resolve this.

---

