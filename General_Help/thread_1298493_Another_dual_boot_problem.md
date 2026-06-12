---
title: "Another dual boot problem"
date: 2009-10-22
forum: General Help
---

### Post by tx836519 on 2009-10-22
I have a server that boots Ubuntu Hardy Heron by default from the 22GB SCSI HD.  I can set the first IDE HD in the bios as the first boot device and it will boot into DR-DOS with no problem.  Running fdisk from Ubuntu, I get:

ken@MyServer:~$ sudo fdisk -l
[sudo] password for ken: 

Disk /dev/sda: 23.2 GB, 23205193728 bytes
255 heads, 63 sectors/track, 2821 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e9a1080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2529    20314161   83  Linux
/dev/sda2            2530        2821     2345490   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20fc20fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              14       14593   117113850    f  W95 Ext'd (LBA)
/dev/sdb2   *           1          13      104391    6  FAT16
/dev/sdb5              14       14593   117113818+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000764b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdc5               2       12750   102406311    7  HPFS/NTFS
/dev/sdc6           12751       30401   141781626   83  Linux
ken@MyServer:~$ 

I want to set up an 'other operating system' boot in grub to boot DR-DOS shown above on /dev/sdb2.

I edited /boot/grub/menu.lst as follows:

ken@MyServer:/boot/grub$ cat menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

# ---- deleted notes
## ## End Default Options ##

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=01e12d36-891f-4fa0-b895-53f2f533a245 ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=01e12d36-891f-4fa0-b895-53f2f533a245 ro single
initrd		/boot/initrd.img-2.6.24-25-generic

# ---- deleted for brevity

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate items below from the Debian
# ones.
title	Other operating systems:
root

# This entry manually entered.
title	DR-Dos
root	(hd1,2)  # I've also tried (hd1,0)
map	(hd0) (hd1)
map	(hd1) (hd0)
chainloader +1

ken@MyServer:/boot/grub$ 

When DR-DOS is selected, it says starting up and just hangs.

I have run Linux on this box several times over the years.  The earlier versions referred to the SCSI disk as SDA and the first IDE drive as HDA.  Ubuntu doesn't seem the care about the drive type and just lists them in the bios order SDA#, SDB#, SDC#...

What am I missing here?  -- ken

---

### Post by plucky on 2009-10-23
> What am I missing here?


Shouldn't /dev/sdb2 = hd(1,1)
and       /dev/sdb1 = hd(1,0)

I assume you created an extended partition to get it to be /dev/sdb1 and then shrunk it down and created a primary Fat16 partition is the reason it is /dev/sdb2.

Good Luck

---

