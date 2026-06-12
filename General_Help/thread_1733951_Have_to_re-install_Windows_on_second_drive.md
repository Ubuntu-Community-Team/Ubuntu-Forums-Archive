---
title: "Have to re-install Windows on second drive"
date: 2011-04-19
forum: General Help
---

### Post by Autodave on 2011-04-19
Currently running Ubuntu 10.10 off of hard drive.  I want to install a second hard drive and install Vista onto that drive from backup discs.  I know how to install the drives: what I need to know is what order (if any) to install second drive (master or slave) and then, after installing Vista on the new drive, to get GRUB to recognize it.

Thanks in advance.

---

### Post by oldfred on 2011-04-19
You mention master/slave, so are these older IDE/PATA drives? Do you have to set master/slave with jumpers on drive or can you change boot order with BIOS. New SATA drives only change boot order with BIOS and some BIOS that are both SATA/PATA can change boot order of IDE drives.

If the older master, then only the master will boot. I would still install windows and make it the master drive as windows works best if it is drive 0. Then install or use your Ubuntu install and install grub to the Ubuntu drive's MBR. If you can select that in BIOS change BIOS. If not leave grub in Ubuntu drive in case you have to convert it to master, but you will have to install grub to the windows drive sda to get grub to boot. Grub will let you boot both windows & Ubuntu, but windows will not.

---

### Post by Autodave on 2011-04-19
> **oldfred said:**
> You mention master/slave, so are these older IDE/PATA drives? Do you have to set master/slave with jumpers on drive or can you change boot order with BIOS. New SATA drives only change boot order with BIOS and some BIOS that are both SATA/PATA can change boot order of IDE drives.

If the older master, then only the master will boot. I would still install windows and make it the master drive as windows works best if it is drive 0. Then install or use your Ubuntu install and install grub to the Ubuntu drive's MBR. If you can select that in BIOS change BIOS. If not leave grub in Ubuntu drive in case you have to convert it to master, but you will have to install grub to the windows drive sda to get grub to boot. Grub will let you boot both windows & Ubuntu, but windows will not.


Thanks!

---

