---
title: "Partition Help"
date: 2010-05-03
forum: General Help
---

### Post by Lovecannon on 2010-05-03
Well, Ive been dual booting Windows and Ubuntu for a long time now, and I recently upgraded to 10.04 LTS, and when I reinstalled grub, i accidentally overwrote the Windows PBR, and I cant seem to find my recovery disk, so I said screw it and Ive decided to just stick with Ubuntu. I just finished migrating important files to the Ubuntu drive, and I would like to wipe WIndows off my first HD, but that is also where grubs MBR is stored, if I wipe /dev/sda1 will it also remove GRUB?

---

### Post by srs5694 on 2010-05-03
First, some terminology issues: The Master Boot Record (MBR) is the first partition on the entire hard disk. As such, it's not part of any partition and it does not belong to GRUB (although part of GRUB may be installed to the MBR).

Second, GRUB is not normally installed, in whole or in part, to the Windows partition, although it sounds like accidentally doing so may have caused your problems. If so, then creating a new filesystem on that partition will indeed render your system unbootable. To avoid this problem, I recommend you do one of two things:


[list]
[*]Install GRUB to the MBR. You can do this by typing "sudo grub-install /dev/sda" in a command prompt window. Thereafter, GRUB will not be dependent on the Windows partition, so you can create a new filesystem on it or otherwise recycle it.
[*]Create a new filesystem on or otherwise recycle the Windows partition and then re-install GRUB to that partition by typing "sudo grub-install /dev/sda1" (changing /dev/sda1 to whatever is appropriate for this partition). This will only be effective if you create a suitable filesystem on that partition, such as ext3fs; GRUB could be damaged by certain uses of the partition.
[/list]


Either approach will work. Each has advantages and disadvantages. Storing GRUB in the MBR exposes it to the danger of damage from other OSes; but putting it in a partition makes it reliant on whatever boot loader is in the MBR (presumably the standard Windows boot loader at the moment).

---

### Post by Lovecannon on 2010-05-03
> **srs5694 said:**
> First, some terminology issues: The Master Boot Record (MBR) is the first partition on the entire hard disk. As such, it's not part of any partition and it does not belong to GRUB (although part of GRUB may be installed to the MBR).

Second, GRUB is not normally installed, in whole or in part, to the Windows partition, although it sounds like accidentally doing so may have caused your problems. If so, then creating a new filesystem on that partition will indeed render your system unbootable. To avoid this problem, I recommend you do one of two things:


[list]
[*]Install GRUB to the MBR. You can do this by typing "sudo grub-install /dev/sda" in a command prompt window. Thereafter, GRUB will not be dependent on the Windows partition, so you can create a new filesystem on it or otherwise recycle it.
[*]Create a new filesystem on or otherwise recycle the Windows partition and then re-install GRUB to that partition by typing "sudo grub-install /dev/sda1" (changing /dev/sda1 to whatever is appropriate for this partition). This will only be effective if you create a suitable filesystem on that partition, such as ext3fs; GRUB could be damaged by certain uses of the partition.
[/list]


Either approach will work. Each has advantages and disadvantages. Storing GRUB in the MBR exposes it to the danger of damage from other OSes; but putting it in a partition makes it reliant on whatever boot loader is in the MBR (presumably the standard Windows boot loader at the moment).

No. Its installed on the MBR, but I also accidentally installed it on the Windows partitions PBR, thereby rendering the Windows bootloader useless, and since I dont have a Windows recovery disk (and I just wanna stick to Ubuntu), I just wanted to ensure that wiping the Windows partition wouldnt erase the MBR.

---

