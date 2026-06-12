---
title: "how to make 2nd hdd mount"
date: 2009-12-29
forum: General Help
---

### Post by spiky001 on 2009-12-29
I have just put a 2nd hdd in format to fat but it dosn't show up how do i mount it?

---

### Post by Mka on 2009-12-29
Paste the output of "sudo fdisk -l" and that of "sudo cat /etc/fstab".

---

### Post by spiky001 on 2009-12-29
> spiky@server:~$ fdisk -l
spiky@server:~$ sudo fdisk -l
[sudo] password for spiky: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa177a177

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ccf06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1027     8249346    c  W95 FAT32 (LBA)
spiky@server:~$ sudo mount/dev/sdb1
sudo: mount/dev/sdb1: command not found
spiky@server:~$


> spiky@server:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7cdbc951-0b87-45bb-893e-9b138a0d223f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bfb22859-83e6-4128-b3a2-78072414936a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
spiky@server:~$ 


hope this helps

---

### Post by spiky001 on 2009-12-29
I managed what i wanted using disk utility thks any way

---

