---
title: "serious problem with 5.10 installer"
date: 2006-04-17
forum: General Help
---

### Post by yoshi314 on 2006-04-17
i encountered this when trying to install 5.10 on older pc. 

specifically 
p2 celeron 366mhz (motherboard settings : 6,5x66mhz)
256mb ram (3x dimm/100mhz : 128+64+64)
drives: seagate 4gb + fujitsu 13gb + seagate 4gb + liteon cdrw 52x
* the last drive seems not to support ultra dma, pio only :/
riva tnt agp card
sound blaster awe64 isa card
motherboard : gigabyte 6bxc
3com ethernet card (pci)

i wanted to put ubuntu on the slow non-dma seagate disk. installer hangs the system when formatting the drive. the computer simply stops responding (the drive stops at about 96% of formatting and i cannot even switch consoles. computer does not respond at all). 

i tried using nolapic noapic parameters for boot, and i also tried disabling dma for that drive in a second console via hdparm at the very beginning of the installation. 

after reboot however it appears that the partitions are ready (they are created and properly formatted). however i could not find a way to skip formatting partitions on that particular system (installer always insisted on formatting them again) and i cannot proceed further with installation.

the funny thing is - mandriva 2006 did not have any trouble formatting and partitioning that drive. so i reckon this could be some installer/install cd kernel problem.

---

### Post by bscbrit on 2006-04-17
If you have a windows (yes - windows) boot disk, try using fdisk to remove and recreate the partitions.  It also does a surface check of the disk to mark unusable sectors.  There may be linux utilities that do this but none of those that I have used make it obvious.

But your problem seems to be related to your disk.  If you still have Mandrake/mandriva, partition and format it with that, then stop the installation, and use the same partitions for your ubuntu install.

---

