---
title: "lvm partition disappeared"
date: 2010-09-06
forum: General Help
---

### Post by mkaut on 2010-09-06
Hello,

how do I recreate an LVM raid 1 partition, without destroying data on the discs?

The full story: I have a 650GB data partition which is a raid 1 array with ext3. Two days ago, the system (Ubuntu 9.04) started to refuse to write to it, claiming no space left on device - even if there is ca. 102GB free left, if the disk is 85% full (according to df)! Interestingly, removing a couple of GB did not help, after reboot the disk was again full..
I did the "tune2fs -m 0" trick and then forced file check on next reboot by "sudo touch /forcefsck" .. and the result is that the raid partition is gone :-( I have the two physical drives /dev/sd*, unmounted, but the /dev/md1 is no longer there. What can I do to re-create it, without losing the data?

Btw: I realized that I ran tune2fs on the physical partitions /dev/sd* - was I supposed to run it on /dev/md1?

Thanks a lot in advance.

Regards,
Michal

---

### Post by mkaut on 2010-09-06
Looks like it works now, it only needed a restart without file check.
(Though if I restart with "sudo touch /forcefsck", the partition again disappears and appears after the next restart .. weird)

But I still have not solved the original problem with missing space on the disk, so please help me there: ubuntuforums.org/showthread.php?t=1569175

Thanks

Michal

---

