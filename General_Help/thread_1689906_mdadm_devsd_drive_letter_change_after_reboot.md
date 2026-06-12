---
title: "mdadm /dev/sd* drive letter change after reboot"
date: 2011-02-17
forum: General Help
---

### Post by Qwerty9119 on 2011-02-17
Hello All,

I am using mdadm V2.6.7.1 on Ubuntu 10.10 maverick. I have /sda as my main os drive and /sd[bcd] as my RAID 5 raid configured as /dev/md0.

I've run into an occasional problem where sometimes after a reboot my drive letters will change and this effectively breaks my raid configuration (drive /sda will become /sdb).

I am able to restart the array but it is degraded.

I have attempted to assemble the array using the UUID information but that still fails with a bad superblock on drive /dev/sdd.

My question mainly boils down to, how do I a) make sure that the drive letters do not change b) or restart the array when the letters were changed?

Any suggestions would be appreciated, as I am sure I am not the only one that has seen this.

Thanks,

Q

---

### Post by newbuntu007 on 2011-06-25
Hey I'm new to linux and encountering the same problem did find a fix?

---

### Post by Qwerty9119 on 2011-06-25
As much as I hate to say it, a few reboots seems to have fixed it. I do not have the same problem anymore.

Sorry couldn't be more helpful,

Q

---

### Post by Skarloc on 2011-08-12
Hi,

me too - I have my OS on an IDE drive, and my RAID on 4 SATA drives. On power-up, the IDE drive is "sda", and the others are "sdb" to "sde".

On reboot, my IDE drive becomes "sdc", and the RAID drives become "sda,b,d" and "e" (I can't tell you if whether it's a complete mix-up of the drives, or whether it's just 2 drives that switch around.

Either way, it's causing problems with ZFS...

---

