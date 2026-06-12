---
title: "Boot from USB run from HD"
date: 2011-05-27
forum: General Help
---

### Post by akh024 on 2011-05-27
My Fujitsu laptop (Yr2009) hard disk (350GB) has some problem. It has no CD ROM and I am using Ubuntu 10.10 from USB. When I go for Install using full space on HD, installation goes well and towards end an error message says "defective media or hard disk" (not exact these words but..). I had similar failures when installing Windows from USB, and Ubuntu 11.04 from USB using separate USBs in each case. So I assume that MBR area of the HD may be damaged may be I am wrong. After failed installation when I explore the HD I can see that required files were copied on the HD but perhaps booting files can not put on the MBR.
I therefore, would like to explore if it is possible to boot Ubuntu from USB but have the installation on HD so that updates and additional programs could be installed. Using Ubuntu from USB has many limitations.

---

### Post by LordNeo on 2011-05-27
If you installed at least some files, you can try these steps in order to fix and reinstall grub.

boot from the USB then open a terminal and type:

$ sudo fdisk -l

this will show you your partitions, check the one where is linux installed.

mount it (change dev/sda1 with your partition)

$ sudo mount /dev/sda1 /mnt

mount the rest of the system

$ sudo mount --bind /dev /mnt/dev
$ sudo mount --bind /dev/pts  /mnt/dev/pts
$ sudo mount --bind /proc /mnt/proc
$ sudo mount --bind /sys  /mnt/sys

the "log in" into that system

$ sudo chroot /mnt

from here on, just install grub or recheck or whatever (change sda with your hd)

# grub-install --recheck /dev/sda

finally, before leave, do:

grub-update (or update-grub, i don't remember)

Source: [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

---

### Post by akh024 on 2011-05-27
I tried to mount sda5 but it says device not found. So i tried  mounting other drives, all failed to load. Something wrong in the HD hardware wise. Therefore, I am trying to explore booting from USB but using the files from HD.

---

### Post by LordNeo on 2011-05-27
Boot from USB and the use the "Disk Utility" and check the harddrive SMART (it's a stuff inside the HD that will tell you if something is going wrong like overheat or damaged clusters)

---

### Post by akh024 on 2011-05-28
I did all the possible tests that are available in the UBUNTU and none has given any indication of defective or imminent failure. 
While in the  disk utility screen I triled to mount the first partition sada1- error message "Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail  or so"
I would like to share the current partition table status
/dev/sda1-ext4-21gb
/dev/sda2-ext2-6gb mounted/media/swap
/dev/sda3-fat32-data mounted/media/data
May be above will show more light to guess what can be done.

---

### Post by akh024 on 2011-05-28
ubuntu@ubuntu:~$ dmesg | tail
[ 2375.504204] sd 7:0:0:0: [sdd] Write Protect is off
[ 2375.504213] sd 7:0:0:0: [sdd] Mode Sense: 23 00 00 00
[ 2375.504220] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[ 2375.507506] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[ 2375.507520]  sdd: sdd1
[ 2375.522977] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[ 2375.522983] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[13259.755119] EXT4-fs (sda1): bad geometry: block count 7325696 exceeds size of device (5120000 blocks)
[13715.492501] EXT4-fs (sda1): bad geometry: block count 7325696 exceeds size of device (5120000 blocks)
[14177.530675] palimpsest[5119]: segfault at 4 ip 0804fb5a sp bf9d9b5c error 4 in palimpsest[8048000+1a000]

What does the bad geometry mean here, HD is physically damaged or ..

---

