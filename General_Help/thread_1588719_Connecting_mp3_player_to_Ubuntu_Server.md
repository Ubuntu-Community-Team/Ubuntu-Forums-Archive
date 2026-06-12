---
title: "Connecting mp3 player to Ubuntu Server"
date: 2010-10-05
forum: General Help
---

### Post by clskier on 2010-10-05
I have set up an Ubuntu Server for use as a file and print server in my house.  I now want to also use it as a charging/syncing station for all my various mp3 players and cameras around the house.  I started with what I thought would be the easiest; A Sansa Fuze set to MSC mode.  I expected to plug it into the USB port, mount it as a drive, and use Rsync to move files back and forth on a nightly basis.  When I plug it in and sudo command "fdisk -l" I get the following:

[I]Disk /dev/sdc: 4077 MB, 4077912064 bytes
126 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 7812 * 512 = 3999744 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?       99608      245731   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(99607, 97, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(245730, 44, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       21594      269422   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(21593, 80, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(269421, 14, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      239361      487188   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(239360, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(487187, 77, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?      369391      369398       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(369390, 104, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(369397, 117, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order[/I]

Do I need to reformat the disk or something?

Thanks

---

