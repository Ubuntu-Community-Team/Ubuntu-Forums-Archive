---
title: "help with clonezilla bootable USB key instructions"
date: 2009-10-03
forum: General Help
---

### Post by jcoles on 2009-10-03
[FONT="Arial"]I followed clonezilla's instructions for creating a bootable USB key, but it is not bootable. 
I am running Ubuntu 8.10 and used the alternative build of clonezilla that is supposed to be based on Ubuntu. 
Here's the output from running makeboot, with some comments/questions:[/FONT]
[FONT="Courier new"]
jcoles@thispc:/media/clonezilla/utils/linux$ sudo ./makeboot.sh /dev/sdb1
This command will install MBR and syslinux bootloader on this machine
--------------------------------------------
Machine: HP Compaq dc5750 Small Form Factor:

Disk /dev/sdb: 132 MB, 132251136 bytes
255 heads, 63 sectors/track, 16 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f1117c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          16      128488+   b  W95 FAT32
--------------------------------------------
Are you sure you want to continue?
[y/n] y
OK! Let's do it!
--------------------------------------------[/FONT]

[FONT="Arial"]So far, so good.
[/FONT]
[FONT="Courier new"]Do you want to install mbr on /dev/sdb on this machine "HP Compaq dc5750 Small Form Factor" ?
[y/n] y[/FONT]

[FONT="Arial"]Should I have answered Yes? This sounds like part of making a disk bootable.[/FONT]

[FONT="Courier new"]OK! Let's do it!
Running: cat ../mbr/mbr.bin > /dev/sdb
--------------------------------------------

Do you want to install the SYSLINUX bootloader on /dev/sdb1 on this machine "HP Compaq dc5750 Small Form Factor" ?
[y/n] y
OK! Let's do it![/FONT]

[FONT="Arial"]Again, should I have answered Yes?[/FONT]

[FONT="Courier new"]We need a filesystem supporting Unix file mode for syslinux. Copying syslinux from FAT to /tmp/...
`syslinux' -> `/tmp/syslinux.W14006/syslinux'
Running: /tmp/syslinux.W14006/syslinux -f /dev/sdb1 
done![/FONT]

[FONT="Arial"]Why is it using a weird temporary syslinux from the hard drive instead of the syslinux provided with clonezilla on the USB stick? Has something gone wrong?[/FONT]

[FONT="Courier new"]//NOTE// If your USB flash drive fails to boot (maybe buggy BIOS), try to use "syslinux -fs /dev/sdb1", i.e. running with "-s".[/FONT]

[FONT="Arial"]When the USB key turned out to not be bootable, I tried running the recommended command, but it made no difference.

Any ideas why this didn't work? I would really like to find a reliable method to create bootable disks.[/FONT]

---

### Post by jcoles on 2009-10-03
As it turns out, the disk is bootable, but I had to get my Aspire One netbook to recognize it in the usual operating system, then restart with the key still in place. Attaching the key with the unit switched off and then starting didn't work. The boot device menu showed only the internal hard disk.

---

