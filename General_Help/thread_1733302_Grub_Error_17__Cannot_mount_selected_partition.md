---
title: "Grub: Error 17  Cannot mount selected partition"
date: 2011-04-19
forum: General Help
---

### Post by mandi1989 on 2011-04-19
Hey, first post here, I've tried everything to solve this, been browsing  the forums for the last 2 days and no solution has worked.

So I got a new netbook (Samsung n150 dated 03/2011) it had ubuntu 10.10  installed but I already use ubuntu on my macbook
so I'm trying out  knoppix, I booted it from usb and ran the HD  installer, it gets  through all that and then installs grub ok, but when  I reboot I get  "Error 17: Cannot mount selected partition"

Things I already tried:
*Grub setup (grub, root (hd0,1), setup (hd0), quit) and every variation.
*I tried removing the usb and setting the HDD back to first boot in the bios and
then changing the menu.lst accordingly, still I get error 17.

Below is the information just after boot with the usb still plugged in and set as first boot in bios.

fdisk -l
```

[COLOR=Red]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
  
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1052257   82  Linux swap / Solaris
/dev/sda2   *         132       30401   243143775   83  Linux
  
  [COLOR=Lime]Disk /dev/sdb: 2062 MB, 2062024704 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x285b5c9e
    
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         250     2008093+   c  W95 FAT32 (LBA)[/COLOR][/COLOR]
```[COLOR=Red]Red[/COLOR] = HDD
[COLOR=Lime]Green[/COLOR] = USB

menu.lst from  /media/sda2/boot/grub

```
default 0
timeout 30
color cyan/blue white/blue

title Knoppix
root (hd0,1)
kernel /boot/vmlinuz root=/dev/sda2 rootwait lang=us apm=power-off nomce libata.force=noncq tz=localtime loglevel=1  rw
```(The above menu.lst gets error 15 cannot find file until I unplug the usb and change to (hd0) to boot from HDD)

Please help me, really want to get this working. Thanks in advance.

--Mandi

---

### Post by kiyop on 2011-04-19
I suggest you to run boot info script by booting with Ubuntu Live CD.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
and paste the whole result between [ code] and [/code] in this forum "Reply" and submit.

I do not know if Grub legacy can deal with large disk and/or ext4, or if some misconfiguration is the reason of problem or not.

---

### Post by mandi1989 on 2011-04-19
Done here is  the output

```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 
    188767563 of the same hard drive for the stage2 file. A stage2 file is at 
    this location on /dev/sda. Stage2 looks on partition #2 for 
    /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 6.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst /grldr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1     2,104,514     2,104,514  82 Linux swap / Solaris
/dev/sda2    *      2,104,515   488,392,064   486,287,550  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4041 MB, 4041211392 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7892991 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,887,914     7,887,852   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              iso9660    Ubuntu 10.10 i386             
/dev/loop1                                              squashfs                                 
/dev/sda1        ac2e73fa-0c0a-4c96-9757-9f0c43cc759b   swap                                     
/dev/sda2        4209f65a-c2cc-4bd2-8946-ef2c173d4665   reiserfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        04F3-219D                              vfat       XBOOT                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /isodevice               vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/4209f65a-c2cc-4bd2-8946-ef2c173d4665 reiserfs   (rw,nosuid,nodev,uhelper=udisks)


=========================== sda2/boot/grub/menu.lst: ===========================

default 0
timeout 30
color cyan/blue white/blue

title KNOPPIX
root (hd0)
kernel /boot/vmlinuz root=/dev/sda2 rootwait lang=us apm=power-off nomce libata.force=noncq tz=localtime loglevel=1  rw

=============================== sda2/etc/fstab: ===============================

# DEFAULT BASE FSTAB, UNCONFIGURED
proc       /proc         proc       noauto             0 0
sysfs      /sys          sysfs      noauto             0 0
/dev/sda2 / reiserfs relatime 0 0
/dev/sda1 none swap defaults 0 0
# Added by KNOPPIX
/dev/sdb1 /media/sdb1 vfat noauto,users,exec,umask=000,shortname=winnt 0 0

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2
    ??GB: boot/vmlinuz-2.6.37

================================ sdb1/menu.lst: ================================


color magenta/white white/magenta black/white black/white 


### MENU END
title Linux
configfile /boot/grub4dos/linux.lst
### MENU END


### MENU START
title Help!\n
ls /images/help.iso || find --set-root /images/help.iso
map --heads=0 --sectors-per-track=0 /images/help.iso (0xff) || map --heads=0 --sectors-per-track=0 --mem /images/help.iso (0xff)
map --hook
chainloader (0xff)
### MENU END

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: menu.lst
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 f2 03  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  ec 5b 78 00 07 1e 00 00  00 00 00 00 02 00 00 00  |.[x.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 9d 21 f3 04 4e  4f 20 4e 41 4d 45 20 20  |..).!..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 a0  49 00 00 66 ba 00 00 00  |..E}.f..I..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by kiyop on 2011-04-19
I am not familiar with reiserfs. I have never used reiserfs.
Your knoppix installer might have installed grub legacy on MBR of /dev/sda.
Indeed, grub legacy may support reiserfs.
/boot/grub/reiserfs_stage1_5 may support.
GRUB2 definitely supports reiserfs.
I suggest you to boot with Ubuntu live CD and chroot into installed Debian and install grub2.
```
sudo mount -t reiserfs /dev/sda2 /mnt -o rw
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash
apt-get update
apt-get install grub-pc
grub-install /dev/sda
grub-mkdevicemap
update-grub
exit
sudo umount -l /mnt/proc
sudo umount -l /mnt/sys
sudo umount -l /mnt/dev
sudo umount -l /mnt
exit
```Shutdown and remove LiveCD and restart.

If I were you, I would not have used reiserfs, but used ext4 filesystem.

You had better wait somebody who knows reiserfs better than I reply.

---

### Post by mandi1989 on 2011-04-19
Well that got me a little closer to boot, grub now sees my knoppix as the debian it is and trys to boot but halts with the following error.

```
[COLOR=Red]Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)[/COLOR]
```

---

### Post by kiyop on 2011-04-19
Now, kernel could be run by grub2, but kernel cannot mount /dev/sda2 perhaps.
You should search if the kernel and initramfs have proper module or something which enables mounting /dev/sda2 (reiserfs).

Anyway, please run boot info script again and post the result.

I am not sure how to know which kernel modules are incorporated into kernel or initramfs of knoppix.

With ubuntu, "lsmod" or "modprobe" command or "more /etc/initramfs-tools/modules" show the information on modules.

There is information on modules used in initramfs of knoppix on the following link:
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10694662](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10694662)
I am not sure whether the information on the above link is correct or not.

What is the version of Knoppix (or where did you download iso file of Knoppix)?

---

### Post by psusi on 2011-04-19
I would suggest you reinstall using ext4 instead of reiserfs.  It has not been supported really since it was merged into the kernel, when its creator moved on to working on reiser4, which never got finished because he is now in prison for murdering his wife.

---

### Post by mandi1989 on 2011-04-20
Well here is the script result again, I've been booting from the grub entry "Debian GNU/Linux, kernel 2.6.37" 

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 
    188767955 of the same hard drive for the stage2 file. A stage2 file is at 
    this location on /dev/sda. Stage2 looks on partition #2 for 
    /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 6.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst /grldr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1     2,104,514     2,104,514  82 Linux swap / Solaris
/dev/sda2    *      2,104,515   488,392,064   486,287,550  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4041 MB, 4041211392 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7892991 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,887,914     7,887,852   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              iso9660    Ubuntu 10.10 i386             
/dev/loop1                                              squashfs                                 
/dev/sda1        ac2e73fa-0c0a-4c96-9757-9f0c43cc759b   swap                                     
/dev/sda2        4209f65a-c2cc-4bd2-8946-ef2c173d4665   reiserfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        04F3-219D                              vfat       XBOOT                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /isodevice               vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)


=========================== sda2/boot/grub/menu.lst: ===========================

default 0
timeout 30
color cyan/blue white/blue

title KNOPPIX
root (hd0)
kernel /boot/vmlinuz root=/dev/sda2 rootwait lang=us apm=power-off nomce libata.force=noncq tz=localtime loglevel=1  rw
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4209f65a-c2cc-4bd2-8946-ef2c173d4665 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Debian GNU/Linux, kernel 2.6.37
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.37 root=UUID=4209f65a-c2cc-4bd2-8946-ef2c173d4665 ro 

title        Debian GNU/Linux, kernel 2.6.37 (single-user mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.37 root=UUID=4209f65a-c2cc-4bd2-8946-ef2c173d4665 ro single

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda2/etc/fstab: ===============================

# DEFAULT BASE FSTAB, UNCONFIGURED
proc       /proc         proc       noauto             0 0
sysfs      /sys          sysfs      noauto             0 0
/dev/sda2 / reiserfs relatime 0 0
/dev/sda1 none swap defaults 0 0
# Added by KNOPPIX
/dev/sdb1 /media/sdb1 vfat noauto,users,exec,umask=000,shortname=winnt 0 0

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2
    ??GB: boot/vmlinuz-2.6.37

================================ sdb1/menu.lst: ================================


color magenta/white white/magenta black/white black/white 


### MENU END
title Linux
configfile /boot/grub4dos/linux.lst
### MENU END


### MENU START
title Help!\n
ls /images/help.iso || find --set-root /images/help.iso
map --heads=0 --sectors-per-track=0 /images/help.iso (0xff) || map --heads=0 --sectors-per-track=0 --mem /images/help.iso (0xff)
map --hook
chainloader (0xff)
### MENU END

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: menu.lst
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 f2 03  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  ec 5b 78 00 07 1e 00 00  00 00 00 00 02 00 00 00  |.[x.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 9d 21 f3 04 4e  4f 20 4e 41 4d 45 20 20  |..).!..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 a0  49 00 00 66 ba 00 00 00  |..E}.f..I..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```[FONT=Tahoma][FONT=Verdana]As for the bit you say about the kernel you kind of lost me, I'm fairly new to all this,
I understand the hdd partition types and after this I do think the next step will be to
reformat to ext4 if we can't get it working on [/FONT][/FONT][FONT=Verdana]reiserfs[/FONT][FONT=Tahoma][FONT=Verdana] the only reason I went with
reiserfs is becasue it the knoppix default.

As for the knoppix version its the latest 6.4.4 downloaded from a mirror listed on their
official site, I've tried other isos too as well as version 6.4.2 to see see it that helped 
at all but didn't, thanks for the help guys what next to see if we can get this booting on 
on the current reiserfs install?

[COLOR=Magenta]PS:[/COLOR] That link you gave [/FONT][/FONT][kiyop]("http://ubuntuforums.org/member.php?u=1246530") just links to a new reply in this thread.....

---

### Post by kiyop on 2011-04-20
> **mandi1989 said:**
> 
```
title KNOPPIX
root (hd0)
kernel /boot/vmlinuz root=/dev/sda2 rootwait lang=us apm=power-off nomce libata.force=noncq tz=localtime loglevel=1  rw

```
Maybe above setting is generated by Knoppix, isn't it?

Did you write above setting?
If not, kernel option "root=/dev/sda2 rootwait lang=us apm=power-off nomce libata.force=noncq tz=localtime loglevel=1  rw" may be effective.

> **mandi1989 said:**
> ```
/dev/sda1 none swap defaults 0 0
```
I am not familiar with Knoppix.
In Ubuntu, mount option for swap is not "defaults", but "sw".

> **mandi1989 said:**
> PS: That link you gave kiyop just links to a new reply in this thread.....
Excuse my mistake.
Correct one is:
[http://brooknet.no-ip.com/~lex/public/eeepc_af/]("http://brooknet.no-ip.com/%7Elex/public/eeepc_af/")

And I think you may be able to get better answer in Knoppix Forum.
[http://www.knoppix.net/forum/](http://www.knoppix.net/forum/)

This is Ubuntu Forum. I am not familiar with Knoppix.

---

### Post by mandi1989 on 2011-04-20
That was generated by knoppix when it was first installed, editing to your suggestion just gets "Error 1: Filename must be either an absolute pathname or blocklist"

Couldn't boot with those options either, I'm going to try reformatting to ext4 and see how that goes, I'll update when done, if no look I'll see what people over at knoppix forums have to say too.

[COLOR=Red]EDIT:[/COLOR] The knoppix 0wn bash script (installer on the live cd) states that the prerequisites for install are a 1GB linux-swap and a 3GB+ reiserFS partition, if it does not find this it will halt install Know of an way to force it to install to another file system? Editing the bash script maybe?

Script attached.

---

### Post by kiyop on 2011-04-20
> **mandi1989 said:**
> That was generated by knoppix when it was first installed, editing to your suggestion just gets "Error 1: Filename must be either an absolute pathname or blocklist"

Couldn't boot with those options either, I'm going to try reformatting to ext4 and see how that goes, I'll update when done, if no look I'll see what people over at knoppix forums have to say too.

[COLOR=Red]EDIT:[/COLOR] The knoppix 0wn bash script (installer on the live cd) states that the prerequisites for install are a 1GB linux-swap and a 3GB+ reiserFS partition, if it does not find this it will halt install Know of an way to force it to install to another file system? Editing the bash script maybe?

Script attached.
Thanks for your reply.

"Filename..." error indicates you gave wrong kernel file name. Is there /boot/vmlinuz or /boot/vmlinuz-2.6.37 in /dev/sda2?

I think you know Knoppix better than I now.
I again suggest you to post a question in Knoppix Forum.
Otherwise please wait until somebody who knows Knoppix well submit post in this **Ubuntu** forum.

It is a pity that I cannot solve your problem.
:(

---

### Post by mandi1989 on 2011-04-20
/boot/vmlinuz-2.6.37 is in /dev/sda2, just heading to work now, I posted over at knoppix hopefully someone there can shed a little more light on the situation,  I'll keep this post updated for reference and becasue I've learnt a few things while tinkering around haha.

Thanks for the help and insight you've given so far.

---

