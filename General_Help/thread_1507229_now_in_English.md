---
title: "now in English"
date: 2010-06-11
forum: General Help
---

### Post by fidelfloris on 2010-06-11
Good afternoon,

I have a dualboot problem.
After upgrading ubuntu to 10.04 my Windows entry in de Grub does not work anymore.
My only option is Ubuntu.

So I made a copy of the ultimate boot cd, now i can boot Windows Vista again.
And I can go to the recovery of Vista.

My problem is that I lose al my data.
Is there a way to repair my Grub, or a way to repair Windows Vista without me loosing al data?

This may be usefull:

sudo fdisk -l

[sudo] password for floris: 

Schijf /dev/sda: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Schijf-ID: 0x067b51a8

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1        1913    15360000   27  [onbekend]
/dev/sda2   *        1913       49791   384579584    7  HPFS/NTFS
/dev/sda3           49791       87372   301873186    7  HPFS/NTFS
/dev/sda4           87373      121601   274944442+   5  Uitgebreid
/dev/sda5           87373      120475   265899816   83  Linux
/dev/sda6          120476      121601     9044563+  82  Linux wisselgeheugen

Schijf /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Schijf-ID: 0x47a16e32

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1               1       61773   496190598+   7  HPFS/NTFS
/dev/sdb2           61774      121601   480568410    5  Uitgebreid
/dev/sdb5           61774      120475   471523783+  83  Linux
/dev/sdb6          120476      121601     9044563+  82  Linux wisselgeheugen


Has someone got a solution for me?

Greetings Fidel

---

### Post by TeoBigusGeekus on 2010-06-11
Much better now!
Try [this.]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7")

---

### Post by fidelfloris on 2010-06-11
> **TeoBigusGeekus said:**
> Much better now!
Try [this.]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7")

  	 	 	 	 	 	  -desktop:~$ sudo -i [sudo] password for:  root@floris-desktop:~#  root@floris-desktop:~# sudo -i root@floris-desktop:~# mount /dev/sda7 /mnt mount: apparaat /dev/sda7 bestaat niet root@floris-desktop:~# mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition /dev/sda6 ziet er uit als wisselgeheugen -- niet aangekoppeld mount: u moet een bestandssysteemsoort aangeven root@floris-desktop:~# grub-install --root-directory=/mnt/ /dev/sda Installation finished. No error reported. root@floris-desktop:~# sudo grub-install /dev/sda Installation finished. No error reported. root@floris-desktop:~# sudo os-prober /dev/sda1:Windows Vista (loader):Windows:chain /dev/sda2:Windows Recovery Environment (loader):Windows1:chain /dev/sdb5:Ubuntu 9.10 (9.10):Ubuntu:linux root@floris-desktop:~# sudo update-grub Generating grub.cfg ... Found linux image: /boot/vmlinuz-2.6.32-22-generic-pae Found initrd image: /boot/initrd.img-2.6.32-22-generic-pae Found linux image: /boot/vmlinuz-2.6.31-22-generic-pae Found initrd image: /boot/initrd.img-2.6.31-22-generic-pae Found memtest86+ image: /boot/memtest86+.bin Found Windows Vista (loader) on /dev/sda1 Found Windows Recovery Environment (loader) on /dev/sda2 Found Ubuntu 9.10 (9.10) on /dev/sdb5 done root@floris-desktop:~#  this was the result!

but it didnt work.

have you got an other solution?

greetings Fidel

---

