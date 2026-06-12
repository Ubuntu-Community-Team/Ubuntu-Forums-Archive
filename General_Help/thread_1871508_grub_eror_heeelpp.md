---
title: "grub eror heeelpp"
date: 2011-10-29
forum: General Help
---

### Post by cihad on 2011-10-29
I am using win 7 and I complately transfer myself to l'nux but I d'dnt uninstall win 7 firs I install ubuntu 11.4 I was good with it after that linux 11.10 come and I instal that but it didnt work correctly in my system and I instal linux 11.4 lts but again it didnt work correcty and I install linux 11.4 normal but that time I have problem with grub it does not work it gaves eror now I cant enter any of my os even win 7 
I am writing this post from live cd linux 
what can i do 
I have asus laptop I am using 1 hdd 
I tried somthing but it gave these answers
ubuntu@ubuntu:~$ sudosudo mount /dev/sda7 /mnt  
sudosudo: command not found
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt  
mount: /dev/sda6 already mounted or /mnt busy
mount: according to mtab, /dev/sda6 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt /dev/sda
Unrecognized option `--boot-directory=/mnt'

ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt /dev/sda
Unrecognized option `--boot-directory=/mnt'
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

---

### Post by raja.genupula on 2011-10-29
Look at my signature for grub recovery . I am sure that gonna help you.

---

### Post by cihad on 2011-10-29
ubuntu@ubuntu:~$ sudo upgrade-from-grub-legacy

core.img doestn't exist, trying to create it.

/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ sudo blkid
/dev/sda5: UUID="e92d50e4-54f8-4621-a424-f14902d08a7e" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="Sistem AyrM-DM-1ldM-DM-1" UUID="FC064ECE064E899A" TYPE="ntfs" 
/dev/sda2: UUID="E4A46D3AA46D107A" TYPE="ntfs" 
/dev/sda4: UUID="FADE5117DE50CE0F" TYPE="ntfs" 
/dev/sda6: UUID="7b741725-73e7-44f7-9153-0d65149bd1d3" TYPE="ext4" 
/dev/sda7: UUID="791344c8-0998-43eb-9dc2-8d04557e2c24" TYPE="ext4" 
/dev/sda8: UUID="561f078c-6c4d-4e66-9f5f-0e91052f2a13" TYPE="ext4" 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f222a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       12749   102297600    7  HPFS/NTFS
/dev/sda3           12749       25497   102397953    5  Extended
/dev/sda4           25497       60802   283584512    7  HPFS/NTFS
/dev/sda5           12749       12992     1951744   82  Linux swap / Solaris
/dev/sda6           12992       16639    29295616   83  Linux
/dev/sda7           16639       16651       96256   83  Linux
/dev/sda8           16651       25497    71051264   83  Linux
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
mount: /dev/sda7 already mounted or /mnt busy
mount: according to mtab, /dev/sda7 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
mount: /dev/sda7 already mounted or /mnt busy
mount: according to mtab, /dev/sda7 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt/boot
mount: mount point /mnt/boot does not exist
ubuntu@ubuntu:~$ 
 

some one can halp me what is wrong with my boot

---

### Post by raja.genupula on 2011-10-29
[http://ubuntuforums.org/archive/index.php/t-264624.html](http://ubuntuforums.org/archive/index.php/t-264624.html)

---

