---
title: "Installing Maverick while keeping existing bootloader"
date: 2010-10-11
forum: General Help
---

### Post by saverio.miroddi on 2010-10-11
I have a machine with Lucid installed, with grub on a boot partition, and another bootloader on the MBR.
What happens if I install Maverick? Is it going to overwrite the bootloader on the MBR? Or does it automatically update the one on the boot partition?

Thanks!
Saverio

---

### Post by oldfred on 2010-10-11
You cannot share /boot partitions. You need to create partitions in advance and use manual install to choose / (root). You  also should not share /home.

In the install at the partition screen the advanced button has been replaced by a combo box on where to install grub. I did not check that no install was a choice but you could just install to the partition.

---

