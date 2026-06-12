---
title: "Will not boot from SSD, just USB drive. Custom system"
date: 2012-06-27
forum: General Help
---

### Post by selfDistruct on 2012-06-27
Ok guys, I was using the IRC channel witch was loads of help. But this last part seams to be having some issues getting done. So im going to explain a little and see what I get. I appreciate your patience as i know enough to know i know very little, which is why im here

Pc:

Gigabyte GA-K8N-SLI
1 gb ram
AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ × 2 
gforce 7800  gtx
ocz ssd agility 3 120gb (brand new SSD, no files installed before this.)

The issue is i have used the USB boot method, im on it now. connects fine, runs great.. off the USB drive. it will not boot from SSD, i have checked the bios list settings made changes to the order, but still nothing. Uninstalled and reinstalled ubuntu though the USB. **When i attempt to boot from SSD it gives me a DMI verifying hang issue**. The system sees the ssd, knows the size, i see ubuntu's files in it. edit,save, no issues. But it will not boot. 

This is an old system built by my late father, 5 plus years old. I have no other hdd to use other then this one ssd. Any help would be greatly appreciated.

As i said i know relativly little, so bear with me! 

Thanks in advance!

---

### Post by selfDistruct on 2012-06-28
After searching I have found 

 [http://ubuntuforums.org/showthread.php?t=1973947](http://ubuntuforums.org/showthread.php?t=1973947)

I will post suggested commands. And quotes in the thread.

oldfred ""When you install Ubuntu with the auto install options, the grub2 boot loader is normally installed to sda. Some computers make the flash drive sda by default so you may have installed grub to the flash drive."""=

sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002fa8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   232345599   116171776   83  Linux
/dev/sda2       232347646   234440703     1046529    5  Extended
/dev/sda5       232347648   234440703     1046528   82  Linux swap / Solaris

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


When i use sudo grub-install /dev/sda or sdb

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
ubuntu@ubuntu:~$ sudo grub-install /dev/sdb
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

I enter in this...

sudo debconf-show grub-pc

  grub2/kfreebsd_cmdline:
  grub2/linux_cmdline:
  grub-pc/install_devices_failed: false
  grub-pc/chainload_from_menu.lst: true
  grub-pc/postrm_purge_boot_grub: false
  grub2/kfreebsd_cmdline_default: quiet
  grub2/linux_cmdline_default: quiet splash
  grub-pc/hidden_timeout: true
  grub-pc/install_devices:
  grub-pc/partition_description:
  grub2/device_map_regenerated:
  grub-pc/kopt_extracted: false
  grub-pc/disk_description:
  grub-pc/install_devices_empty: false
  grub-pc/timeout: 10
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/install_devices_disks_changed:
  grub-pc/mixed_legacy_and_grub2: true



Any thing would help. Thanks,

---

### Post by Lyfang on 2012-06-28
Did you unmount the devices?

WARNING! Caution, don't try on production machines without fear of dealing with problems.

Launch the Linux Live USB flash drive (created with e.g. UNetbootin) & open the Terminal:

```
sudo fdisk -l
sudo mount /dev/sdaX /mnt
```
(e.g. sudo mount /dev/sda1 /mnt)
```
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
sudo update-grub
sudo reboot
```

---

### Post by selfDistruct on 2012-06-28
Ok fallowed. But still getting that mount issue. They only place i know to unmount other then what you just showed me is in Disk Utility tool.

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.

sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.


sudo umount /mnt
umount: /mnt: not mounted

sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).


Thanks alot for the help.

---

