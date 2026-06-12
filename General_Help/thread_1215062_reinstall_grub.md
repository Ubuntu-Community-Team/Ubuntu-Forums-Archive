---
title: "reinstall grub"
date: 2009-07-16
forum: General Help
---

### Post by davidtuti on 2009-07-16
Hi,

I try to reinstall grub because I've reinstalled windows to can choose betwen windows and kubutu but I can't. 
My ext4 patition is in /dev/sdb3

I do:

rub> root (hd1,2)
 Filesystem type is xfs, partition type 0x83

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

I don't know what I do wrong!?
Any help?
Thanks and sorry for my english!

---

### Post by lisati on 2009-07-16
Have a look here, it might provide a few ideas: [http://ubuntuforums.org/showthread.php?t=1210839](http://ubuntuforums.org/showthread.php?t=1210839)

Edit: from [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)
> Restoring GRUB

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar. Ideally use Ubuntu 8.04 or higher as this has NTFS write support and makes life a bit easier; this isn't necessary, just handy.

2. Open a Terminal. Open a root terminal (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines. Note that you should have mounted the partition which has your Linux system before typing this command. (e.g. In Knoppix Live CD partitions are shown on the desktop but they're not mounted until you double-click on them or mount them manually)

5. Type "root (hd0,3)" note the space between root and (hd0,3).

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. At this stage you can either restart the system and install your own bootloader, or you can continue and tell the Windows bootloader where to find GRUB which will handle booting Linux. 


---

### Post by davidtuti on 2009-07-16
it doesn't work me!
I do:

mdir /kk
mount /dev/sdb3 /kk
grub

grub> find /boot/grub/stage1

hd1,2

grub> root (hd1,2)
grub> setup (hd1,2)
grub> quit

But when I reboot loads directly windows!
Any help?
Thanks!

---

### Post by lindsay7 on 2009-07-16
try one more time


Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by davidtuti on 2009-07-16
Nothing!

```


Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x0f000f00

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       35033   255802995    f  W95 Ext'd (LBA)
/dev/sda3           35034       38914    31168651   83  Linux
/dev/sda5            3188       35033   255802963+   7  HPFS/NTFS

Disco /dev/sdb: 320.0 GB, 320072933376 bytes
81 cabezas, 63 sectores/pista, 122504 cilindros
Unidades = cilindros de 5103 * 512 = 2612736 bytes
Identificador de disco: 0x19a719a7

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *       42239      122504   204798699    f  W95 Ext'd (LBA)
/dev/sdb2   *           2       30199    77050165+   7  HPFS/NTFS
/dev/sdb3           30200       40916    27344425+  83  Linux
/dev/sdb4           40917       42238     3373083   82  Linux swap / Solaris
/dev/sdb5           42239      122504   204798667+   7  HPFS/NTFS

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x00009ac5

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1               1       95406   766348663+   7  HPFS/NTFS
/dev/sdc2           95669      103369    61858282+  83  Linux

ubuntu@ubuntu:~$ sudo grub
grub> find /boot/grub/stage1

Error 15: File not found

grub> quit





```

Any help?

---

### Post by davidtuti on 2009-07-16
I execute the script boot_info_script032.sh and the result is:


============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operación no soportada
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operación no soportada
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb3 and 
                       looks at sector 154379673 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: tipo de sistema de ficheros 'ext4' desconocido

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: tipo de sistema de ficheros 'ext4' desconocido

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x0f000f00

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,199,154    51,199,092   7 HPFS/NTFS
/dev/sda2          51,199,155   562,805,144   511,605,990   f W95 Ext d (LBA)
/dev/sda5          51,199,218   562,805,144   511,605,927   7 HPFS/NTFS
/dev/sda3         562,805,145   625,142,446    62,337,302  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 320.0 GB, 320072933376 bytes
81 cabezas, 63 sectores/pista, 122504 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x19a719a7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *    215,540,514   625,137,911   409,597,398   f W95 Ext d (LBA)
/dev/sdb5         215,540,577   625,137,911   409,597,335   7 HPFS/NTFS
/dev/sdb2    *          5,166   154,105,496   154,100,331   7 HPFS/NTFS
/dev/sdb3         154,105,497   208,794,347    54,688,851  83 Linux
/dev/sdb4         208,794,348   215,540,513     6,746,166  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x00009ac5

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,532,697,389 1,532,697,327   7 HPFS/NTFS
/dev/sdc2       1,536,906,420 1,660,622,984   123,716,565  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="ACB00A7FB00A506E" TYPE="ntfs" 
/dev/sda3: UUID="8c35fada-1f64-43bb-bafb-45f16c003750" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="B0545E55545E1E82" LABEL="INSTALACIONES" TYPE="ntfs" 
/dev/sdb2: UUID="A44467E74467BAA6" LABEL="VIRTUALIZAC" TYPE="ntfs" 
/dev/sdb3: UUID="a7030800-12a4-4b04-8f2f-68ad2fda3484" TYPE="ext4" 
/dev/sdb4: TYPE="swap" UUID="b4bf6a80-cfa9-4ad8-bf96-b0b703e5cdaf" 
/dev/sdb5: UUID="98747D54747D35DA" LABEL="DESCARGAS" TYPE="ntfs" 
/dev/sdc1: UUID="6E60FC1860FBE52D" LABEL="EXTERNO" TYPE="ntfs" 
/dev/sdc2: UUID="cece2654-adc1-45d6-ba32-1b6fc2047e25" TYPE="ext4" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/EXTERNO type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

---

### Post by davidtuti on 2009-07-17
Please any help?
Many thanks!

---

