---
title: "Recovery from a damaged HDD"
date: 2011-10-02
forum: General Help
---

### Post by z61P on 2011-10-02
Background: see the thread [[COLOR=#000000]/dev/disk/by-uuid/xxxx does not exist[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844853") [http://ubuntuforums.org/showthread.php?t=1844853](http://ubuntuforums.org/showthread.php?t=1844853)
 
In summary, I can no longer boot from the HDD discussed in the thread above. However, I can mount it, and from what I can tell so far, the contents of the / directory are intact. 
 
Therefore, it seems to me that I should be able to copy all or part of the root partition to a new/replacement HDD, and move forward without all of the effort required to re-configure a system from scratch. 
 
Unfortunately, my initial attempt at this did not seem to help. Here's what I did: 
 
1. Install Ubuntu 10.04.3 on a new HDD to get a good boot partition written to the new HDD. I tested the integrity of the new HDD by booting the system from it. 
 
2. Re-booting from a bootable Ubuntu CD, I used gparted to copy the root (sda) partition from the original, unbootable HDD to the new HDD. 
 
The copy operation was successful, but the system will not boot from the new HDD. I reach (what I think is) the grub menu from which I must select a kernel to boot from. Choosing the latest kernel then yields a couple lines on the console to the effect that fsck has pronounced sda1 "clean" (fsck from util-linux-ng 2.17.2 ... whatever that is?), and then the process just stops... i.e. no boot, no initramfs prompt - nothing. 
 
The log from an attempt at boot repair (from the bootable CD) is at: [http://paste.ubuntu.com/701206/](http://paste.ubuntu.com/701206/) 
 
I don't understand the detailed interactions between the boot partition, and the root partition during the boot process. However, I'd hazard a guess that there is some part of the root partition that is defective, and this is why copying the entire partition to the new HDD did not cure the problem. Can anyone suggest an approach that may avoid copying the "bad data" to the new partition, and thereby allow me to boot the new HDD while avoiding a complete system re-configuration? 
 
Thanks,
z

---

