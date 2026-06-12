---
title: "grub restoring from encrypted volume"
date: 2011-04-23
forum: General Help
---

### Post by pedja_portugalac on 2011-04-23
I was testing daily image of Natty which has overwritten my original grub and doesn't recognise main system, encrypted 10.04LTS, on separate disk. So long I have tried to reinstall grub using alternate CD, Live CD, following instruction from ubuntu documentation page and even this one: [http://pzolee.blogs.balabit.com/2010/07/grub-helyreallitas-titkositott-es-lvm-particiok-eseten/](http://pzolee.blogs.balabit.com/2010/07/grub-helyreallitas-titkositott-es-lvm-particiok-eseten/) but without success. When I try to install grub it states
> root@ubuntu:/# grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

> root@ubuntu:/home/ubuntu# vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "pinguinrocks" using metadata type lvm2
root@ubuntu:/home/ubuntu# vgchange -ay
  2 logical volume(s) in volume group "pinguinrocks" now active
root@ubuntu:/home/ubuntu# lvscan
  ACTIVE            '/dev/pinguinrocks/root' [922.62 GiB] inherit
  ACTIVE            '/dev/pinguinrocks/swap_1' [8.65 GiB] inherit
root@ubuntu:/home/ubuntu# ls /dev/mapper/
control  encrypted-volume  pinguinrocks-root  pinguinrocks-swap_1
root@ubuntu:/home/ubuntu# mount /dev/mapper/pinguinrocks-root /mnt/system/
root@ubuntu:/home/ubuntu# mount /dev/sdb2 /mnt/system/boot/
mount: you must specify the filesystem type
root@ubuntu:/home/ubuntu# mount -t ext4 /dev/sdb2 /mnt/system/boot/
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:/home/ubuntu# mount /dev/sdb5 /mnt/system/boot/
mount: unknown filesystem type 'crypto_LUKS'
root@ubuntu:/home/ubuntu# vgchange -ay
  2 logical volume(s) in volume group "pinguinrocks" now active
root@ubuntu:/home/ubuntu# mount /dev/sdb5 /mnt/system/boot/
mount: unknown filesystem type 'crypto_LUKS'
root@ubuntu:/home/ubuntu# mount /dev/sdb2 /mnt/system/boot/
mount: you must specify the filesystem type
root@ubuntu:/home/ubuntu# mount /dev/dm-0 /mnt/system/boot/
mount: unknown filesystem type 'LVM2_member'

I am really lost. The disk with my main system is encrypted 1000GB /dev/sdb/
> root@ubuntu:/home/ubuntu# fdisk -l /dev/sdb

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000b9d89

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              32      121602   976510977    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdb5              32      121602   976510976   83  Linux

Partitions are
> root@ubuntu:/home/ubuntu# parted -l
Model: ATA WDC WD3200BEVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   171GB  170GB   primary   ntfs
 3      171GB   320GB  150GB   extended
 5      171GB   316GB  145GB   logical   ext4
 6      316GB   320GB  4292MB  logical   linux-swap(v1)


Model: ATA TOSHIBA MK1059GS (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2
 2      257MB   1000GB  1000GB  extended
 5      257MB   1000GB  1000GB  logical


Model:  USB DISK 2.0 (scsi)
Disk /dev/sdc: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  4007MB  4007MB  primary  fat32        boot, lba


Error: /dev/mapper/pinguinrocks-swap_1: unrecognised disk label           

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/pinguinrocks-root: 991GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  991GB  991GB  ext4


Error: /dev/mapper/encrypted-volume: unrecognised disk label 

Any help will be appreciated VERY-VERY MUCH. :(

---

### Post by dino99 on 2011-04-23
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/757631](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/757631)

i've no experience with such config but you can watch the grub link below

---

### Post by pedja_portugalac on 2011-04-23
> **dino99 said:**
> [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/757631](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/757631)

i've no experience with such config but you can watch the grub link below

Thank you. I hope you'll never have to deal with something like this. :(

---

### Post by pedja_portugalac on 2011-04-24
I think I have solved grub problem. :)

I've worked from the Maverick 10.10 on sda partition but using live CD should do the same. This is the output of commands:
> 
1 sudo apt-get install lvm2 cryptsetup
2 sudo modprobe dm-crypt
3 sudo cryptsetup luksOpen /dev/sdb5 crypt1

Then I have successfully mounted the disk using nautilus GUI (simply clicking on disk in places) and last step from terminal:
> sudo update-grub

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
  Found duplicate PV ujMJTqwc2y4jubwXsZEAiARxvWL4oX68: using /dev/dm-3 not /dev/dm-0
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 10.04.2 LTS (10.04) on /dev/mapper/pinguinrocks-root
done
 
Finally I can see my lovely Ubuntu 10.04.2 LTS. :D 
Now I have to reboot.

WORKS

Ones I was inside I have reinstalled and reupdated grub so that Ubuntu 10.04 LTS become first choice of my OS's.
> sudo grub-install /dev/sda
Installation finished. No error reported.

sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 10.10 (10.10) on /dev/sda5
done
  
I am happy again. Ubuntu - I'm loving it. :D

---

