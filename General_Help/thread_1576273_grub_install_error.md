---
title: "grub install error"
date: 2010-09-17
forum: General Help
---

### Post by c30tehran on 2010-09-17
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13        5737    45978624    7  HPFS/NTFS
/dev/sdb3            5738        9709    31905090   83  Linux
/dev/sdb4            9710        9964     2048287+  82  Linux swap / Solaris

====================================================
root@ubuntu:~# mkdir /mnt/dev
root@ubuntu:~# mount --bind /dev /mnt/dev
root@ubuntu:~# mount /dev/sdb3 /mnt
root@ubuntu:~# chroot /mnt

root@ubuntu:/# grub-install /dev/sdb
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

root@ubuntu:/# grub-install --recheck /dev/sdb
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.


```

---

### Post by andrewthomas on 2010-09-18
No chroot is necessary.  
Boot from a live CD
```
sudo fdisk -l  # to make sure that the partitions are correct
sudo mount /dev/sdb3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
```
**reboot** and remove CD
sudo update-grub

for more info 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by c30tehran on 2010-09-21
thank you

---

### Post by WorMzy on 2010-09-21
For what it's worth, you were doing the chroot wrong.

```
sudo mount /dev/sdb3 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt

```

If you mount to /mnt/dev first, when you mount your partition to /mnt, /mnt/dev will become empty again because you've mounted the partition's /dev folder over the top.

---

### Post by psychok7 on 2010-10-10
i installed ubuntu 10.10 on my netbook and i am tryin to update grub with a live cd after some changes i had to make because of some workarounds but its not working so i am trying to reinstall grub but i got this warning..what should i 

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x64fd67bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2436    19565568   83  Linux
/dev/sda3            2437       19457   136721152    5  Extended
/dev/sda5            2437       19177   134472051   83  Linux
/dev/sda6           19178       19457     2249068+  82  Linux swap / Solaris

Disk /dev/sdb: 4007 MB, 4007657472 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e89a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     3913161    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo umount /dev/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.


---

