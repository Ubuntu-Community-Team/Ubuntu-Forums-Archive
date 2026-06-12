---
title: "Grub issue : Ubuntu 10.04 and Windows 7"
date: 2010-11-06
forum: General Help
---

### Post by eurekabru on 2010-11-06
I was running Ubuntu 10.04 and decided to create a partition to install Windows 7 in order to play games. I did so and the computer booted straight into Windows. I used this website ([https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)) to reinstate GRUB as the loader but I made a mistake and ended up mounting a wrong folder. Now when I write *sudo update-grub *in Terminal I get this:

bru@bru-laptop:~$ sudo update-grub
[sudo] password for bru: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/sda1/boot
Boot: No such file or directory
done

This is my first problem. How do I remove /media/sda1/boot ?

Second problem is that the laptop boots straight into Ubuntu. I never get a loading menu on start up. And once it does I have the feeling it won't bring up Windows 7 as a choice. Here's the result of Boot Info Script 0.55: 

  ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================
QUOT
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   271,886,335   271,679,488   7 HPFS/NTFS
/dev/sda3         313,202,686   625,141,759   311,939,074   5 Extended
/dev/sda5         313,202,688   612,397,055   299,194,368  83 Linux
/dev/sda6         612,399,104   625,141,759    12,742,656  82 Linux swap / Solaris
/dev/sda4         271,886,832   313,201,727    41,314,896   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        4ADC6A81DC6A6763                       ntfs       System Reserved               
/dev/sda2        1E686D8C686D638D                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        2639AE427383E8FE                       ntfs       Win7                          
/dev/sda5        b6a0fcda-459e-4193-8193-5a37b3dd9db7   ext4                                     
/dev/sda6        f0dcc32c-fa2f-42d2-9ab9-14dc8c0cc72d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/sda1              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/sda2              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /media/CD_ROM            iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f0dcc32c-fa2f-42d2-9ab9-14dc8c0cc72d none            swap    sw              0       0
UUID=4ADC6A81DC6A6763 /media/sda1 ntfs-3g users 0 0
UUID=1E686D8C686D638D /media/sda2 ntfs-3g users 0 0

=================== sda5: Location of files loaded by Grub: ===================


 293.6GB: boot/grub/core.img
 300.2GB: boot/grub/grub.cfg
 293.7GB: boot/initrd.img-2.6.32-21-generic
 266.5GB: boot/initrd.img-2.6.32-25-generic
 293.6GB: boot/vmlinuz-2.6.32-21-generic
 293.7GB: boot/vmlinuz-2.6.32-25-generic
 266.5GB: initrd.img
 293.7GB: initrd.img.old
 293.7GB: vmlinuz
 293.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  bb 03 f9 83 b4 0a d8 d8  91 b9 ce 81 a5 7b 1d 13  |.............{..|
00000010  29 b0 ca a3 57 70 51 fc  48 b0 e7 16 69 4e d7 fd  |)...WpQ.H...iN..|
00000020  c1 f4 1d 4c 8f 81 fa 5c  2d 59 4e 58 d6 d8 5b 50  |...L...\-YNX..[P|
00000030  fd 70 26 d1 3e ff 36 c9  ad ac 59 4f 34 b8 1e 1e  |.p&.>.6...YO4...|
00000040  19 8f 7d ba b8 1a 0e 66  d8 08 7d ed a2 29 a9 cc  |..}....f..}..)..|
00000050  35 99 40 69 45 82 74 d3  34 a0 7d 00 62 0d f7 f3  |5.@iE.t.4.}.b...|
00000060  2e a7 2d ba 19 47 ca 35  18 f6 dd 16 13 d3 60 af  |..-..G.5......`.|
00000070  94 25 08 f8 f6 0a 7d 77  69 bd 0e 68 4a 74 b4 e5  |.%....}wi..hJt..|
00000080  de 99 6c 96 a5 4f b5 2a  d3 a1 3e d6 e1 86 53 c8  |..l..O.*..>...S.|
00000090  ba 4a a8 f2 e7 6a 79 09  e6 40 93 04 5e ff 1c 7d  |.J...jy..@..^..}|
000000a0  b2 74 02 5a 97 41 f3 8f  c9 a8 d7 50 9d 67 9b 34  |.t.Z.A.....P.g.4|
000000b0  25 4a 72 73 e9 11 2b e3  42 c2 49 0e a0 55 89 f3  |%Jrs..+.B.I..U..|
000000c0  17 76 7d 91 99 2e 0b 7a  89 06 ad a9 d9 b9 53 53  |.v}....z......SS|
000000d0  0a eb 94 18 df bc dd 01  27 3d 18 8f 49 e0 d1 7b  |........'=..I..{|
000000e0  b7 ae b3 c1 97 99 6e 50  3d ea 2e 3a 80 14 24 70  |......nP=..:..$p|
000000f0  66 41 da 75 9c c7 91 c0  33 9c 8c b5 4b 7e b5 65  |fA.u....3...K~.e|
00000100  99 a4 ba 58 98 a2 36 45  86 28 b4 ca 38 f5 46 85  |...X..6E.(..8.F.|
00000110  c7 b1 ea e0 c2 ee 61 83  51 ba 76 85 9c 86 19 61  |......a.Q.v....a|
00000120  ed 96 1f cb 50 bd a1 19  ba 9e 5d 65 8b a3 91 36  |....P.....]e...6|
00000130  99 84 14 e0 62 30 d5 d5  c4 7d 1b e9 7f 98 01 5f  |....b0...}....._|
00000140  f3 b0 80 bc 3c 4c 9f c3  2f d2 f5 15 2a c2 66 0a  |....<L../...*.f.|
00000150  93 a0 16 7f 19 d7 d2 98  e1 d8 06 53 1a 48 36 e5  |...........S.H6.|
00000160  02 3d d0 d1 61 cb 69 1a  06 49 76 bb ef de be a7  |.=..a.i..Iv.....|
00000170  30 34 d2 e0 91 a6 1d 1b  e2 7a 6c 0c 44 9e 85 19  |04.......zl.D...|
00000180  55 bb bc d8 68 37 6b fb  df ca 52 06 61 40 5c b2  |U...h7k...R.a@\.|
00000190  12 57 ed a2 40 91 4b a8  a9 08 2a 82 93 6d 60 02  |.W..@.K...*..m`.|
000001a0  47 d8 3d e4 4e 54 90 9c  9e 16 61 c2 7c d2 e6 c1  |G.=.NT....a.|...|
000001b0  e5 a3 1b 62 15 61 0d 22  c2 16 34 ac 26 7a 00 0f  |...b.a."..4.&z..|
000001c0  ff ff 83 0f ff ff 02 00  00 00 00 58 d5 11 00 0f  |...........X....|
000001d0  ff ff 05 0f ff ff e2 5c  d5 11 20 73 c2 00 00 00  |.......\.. s....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```How do i do the fancy embedded text that you can scroll through ?

I'm pretty new to linux... be gentle.
And thanks to anyone trying!

---

### Post by sikander3786 on 2010-11-06
Boot files for Windows 7 are completely missing.

> ```
sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
**Boot files/dirs: /bootmgr /Boot/BCD /boot/grub/core.img**

sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
**Boot files/dirs: /boot/grub/core.img**
```

Have you got a Windows 7 install or recovery disc? You need to boot off that and perform a startup repair 3 times. Yes remember 3 times. Hit Enter at the language screen and press "R" at the Install screen and you'll see the startup recovery option there.

You'll later need to re-install Grub. We can guide you after you get Windows 7 working.

---

### Post by eurekabru on 2010-11-06
> **sikander3786 said:**
> Boot files for Windows 7 are completely missing.



Have you got a Windows 7 install or recovery disc? You need to boot off that and perform a startup repair 3 times. Yes remember 3 times. Hit Enter at the language screen and press "R" at the Install screen and you'll see the startup recovery option there.

You'll later need to re-install Grub. We can guide you after you get Windows 7 working.

Hi! Thanks for helping me.

I rebooted with my windows dvd in and went to Startup repair but it says it does not detect any problems. Should I reinstall Windows from scratch?

---

### Post by sikander3786 on 2010-11-06
> **eurekabru said:**
> Hi! Thank for helping me.

I rebooted with my windows dvd in and went to Startup repair but it says it does not detect any problems. Should I reinstall Windows from scratch?

I don't think if you definitely need a reinstall. I think you have tried the auto repair. Choose Startup Repair as shown in the image below. Once completed, reboot, start over and do it 3 times in all.

---

### Post by eurekabru on 2010-11-06
> **sikander3786 said:**
> I don't think if you definitely need a reinstall. I think you have tried the auto repair. Choose Startup Repair as shown in the image below. Once completed, reboot, start over and do it 3 times in all.

That's the one i picked. Even did it three times just in case.

---

### Post by sikander3786 on 2010-11-06
> **eurekabru said:**
> That's the one i picked. Even did it three times just in case.
You can try doing it from the command prompt if you wish to or just reinstall if you feel comfortable and safe with that.

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

And this one is even better and stronger.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by wilee-nilee on 2010-11-06
> **eurekabru said:**
> Hi! Thanks for helping me.

I rebooted with my windows dvd in and went to Startup repair but it says it does not detect any problems.** Should I reinstall Windows from scratch?**

Yes, you have grub in the boot as well as missing other stuff. Build a ntfs partition with gparted, and install to that partition. You will have to reload grub to the mbr use this link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Ask any questions that you like before proceeding, a install of W7 takes like 20 minutes compared to trying to fix a mucked installation. Personally I wouldn't trust that install.

---

### Post by eurekabru on 2010-11-06
> **wilee-nilee said:**
> Yes, you have grub in the boot as well as missing other stuff. Build a ntfs partition with gparted, and install to that partition. You will have to reload grub to the mbr use this link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")
 
Ask any questions that you like before proceeding, a install of W7 takes like 20 minutes compared to trying to fix a mucked installation. Personally I wouldn't trust that install.
 
 
Alright, took a dinner break and reinstalled Windows 7 after I formatted the partition. First time it rebooted during the install I saw the windows bootloader thing and it had Windows 7 twice and nothing else. It stayed for 2 seconds and loaded Windows. The computer is now booting in Windows automatically.
 
What's my next step? Boot into Ubuntu LiveCD?
 
 
Edit: Currently reading the link. My bad!

---

### Post by wilee-nilee on 2010-11-06
> **eurekabru said:**
> Alright, took a dinner break and reinstalled Windows 7 after I formatted the partition. First time it rebooted during the install I saw the windows bootloader thing and it had Windows 7 twice and nothing else. It stayed for 2 seconds and loaded Windows. The computer is now booting in Windows automatically.
 
What's my next step? Boot into Ubuntu LiveCD?
 
 
Edit: Currently reading the link. My bad!

If you want you can show us the output from this command and we can point you if needed.
```
sudo fdisk -l
```

---

### Post by eurekabru on 2010-11-06
> **wilee-nilee said:**
> If you want you can show us the output from this command and we can point you if needed.
```
sudo fdisk -l
```

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3abc0e94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       16925   135839744    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           19496       38914   155969537    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4           16925       19496    20657448    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           19496       38120   149597184   83  Linux
/dev/sda6           38121       38914     6371328   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by wilee-nilee on 2010-11-06
> **eurekabru said:**
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3abc0e94

 ```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       16925   135839744    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           19496       38914   155969537    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4           16925       19496    20657448    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           19496       38120   149597184   83  Linux
/dev/sda6           38121       38914     6371328   82  Linux swap / Solaris
```

Partition table entries are not in disk order

It looks as though you didn't prebuild the partitions I hope Ubuntu is still there the output says it is. So boot the live cd and in the terminal run these two commands then reboot into Ubuntu, and run the update grub command in the link.
```
sudo mount /dev/sda5 /mnt
```
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by eurekabru on 2010-11-06
> **wilee-nilee said:**
> It looks as though you didn't prebuild the partitions I hope Ubuntu is still there the output says it is. So boot the live cd and in the terminal run these two commands then reboot into Ubuntu, and run the update grub command in the link.
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/**sdXa**
```


I seem to be at the same point i was earlier today. Those are the commands i screwed up  earlier and I managed to boot into Ubuntu with a bit of trial and error.

---

### Post by wilee-nilee on 2010-11-06
> **eurekabru said:**
> Is sdXa a mistake ? 

I seem to be at the same point i was earlier today. Those are the commands i screwed up  earlier and I managed to boot into Ubuntu with a bit of trial and error.

Yes and thanks for noticing I sent a pm as soon as I looked, I was being really careful, and still missed it. it is correct now. The X=a the hard drive, I just copy and paste the commands from that link and put in the correct letters and numbers.

---

### Post by eurekabru on 2010-11-06
> **wilee-nilee said:**
> Yes and thanks for noticing I sent a pm as soon as I looked, I was being really careful, and still missed it. it is correct now. The X=a the hard drive, I just copy and paste the commands from that link and put in the correct letters and numbers.

Did the two commands.
In the link at number 6 it says Reboot. Do I reboot to the LiveCd to update the Grub?

---

### Post by wilee-nilee on 2010-11-06
> **eurekabru said:**
> Did the two commands.
In the link at number 6 it says Reboot. Do I reboot to the LiveCd to update the Grub?

No to the Ubuntu install.
6 Reboot
7 Refresh the GRUB 2 menu with sudo update-grub

The sudo update-grub is run in the Ubuntu you installed; that your rebooting into. This just makes sure that the HD is read and anything missing is added to the grub menu.

---

### Post by eurekabru on 2010-11-06
> **wilee-nilee said:**
> No to the Ubuntu install.
6 Reboot
7 Refresh the GRUB 2 menu with sudo update-grub

The sudo update-grub is run in the Ubuntu you installed; that your rebooting into. This just makes sure that the HD is read and anything missing is added to the grub menu.

```
bru@bru-laptop:~$ sudo update-grub
[sudo] password for bru: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
**ls: cannot access /media/sda1/boot**
Boot: No such file or directory
done

```

This happened earlier today because i mounted to sda1 instead of sda. (I might have mounted to sda2 as well)

From what I pasted it is still not detecting Windows 7 ?

---

### Post by wilee-nilee on 2010-11-06
Post the boot script again.

Here is what I think happened you left sda1 in place and just reinstalled sda2. If you built the partition ahead of time the correct files from sda1 the boot partition would have all been in one partition and probably are. You have grub in sda1 you never want grub in the MS anywhere.

---

### Post by eurekabru on 2010-11-06
> **wilee-nilee said:**
> Post the boot script again.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   271,886,335   271,679,488   7 HPFS/NTFS
/dev/sda3         313,202,686   625,141,759   311,939,074   5 Extended
/dev/sda5         313,202,688   612,397,055   299,194,368  83 Linux
/dev/sda6         612,399,104   625,141,759    12,742,656  82 Linux swap / Solaris
/dev/sda4         271,886,832   313,201,727    41,314,896   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        4ADC6A81DC6A6763                       ntfs       System Reserved               
/dev/sda2        1E686D8C686D638D                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        2DDE2D1D7CF3C804                       ntfs       Win7                          
/dev/sda5        b6a0fcda-459e-4193-8193-5a37b3dd9db7   ext4                                     
/dev/sda6        f0dcc32c-fa2f-42d2-9ab9-14dc8c0cc72d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/sda1              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/sda2              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /media/Ubuntu 10.04 LTS i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f0dcc32c-fa2f-42d2-9ab9-14dc8c0cc72d none            swap    sw              0       0
UUID=4ADC6A81DC6A6763 /media/sda1 ntfs-3g users 0 0
UUID=1E686D8C686D638D /media/sda2 ntfs-3g users 0 0

=================== sda5: Location of files loaded by Grub: ===================


 293.6GB: boot/grub/core.img
 298.9GB: boot/grub/grub.cfg
 293.7GB: boot/initrd.img-2.6.32-21-generic
 266.5GB: boot/initrd.img-2.6.32-25-generic
 293.6GB: boot/vmlinuz-2.6.32-21-generic
 293.7GB: boot/vmlinuz-2.6.32-25-generic
 266.5GB: initrd.img
 293.7GB: initrd.img.old
 293.7GB: vmlinuz
 293.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  bb 03 f9 83 b4 0a d8 d8  91 b9 ce 81 a5 7b 1d 13  |.............{..|
00000010  29 b0 ca a3 57 70 51 fc  48 b0 e7 16 69 4e d7 fd  |)...WpQ.H...iN..|
00000020  c1 f4 1d 4c 8f 81 fa 5c  2d 59 4e 58 d6 d8 5b 50  |...L...\-YNX..[P|
00000030  fd 70 26 d1 3e ff 36 c9  ad ac 59 4f 34 b8 1e 1e  |.p&.>.6...YO4...|
00000040  19 8f 7d ba b8 1a 0e 66  d8 08 7d ed a2 29 a9 cc  |..}....f..}..)..|
00000050  35 99 40 69 45 82 74 d3  34 a0 7d 00 62 0d f7 f3  |5.@iE.t.4.}.b...|
00000060  2e a7 2d ba 19 47 ca 35  18 f6 dd 16 13 d3 60 af  |..-..G.5......`.|
00000070  94 25 08 f8 f6 0a 7d 77  69 bd 0e 68 4a 74 b4 e5  |.%....}wi..hJt..|
00000080  de 99 6c 96 a5 4f b5 2a  d3 a1 3e d6 e1 86 53 c8  |..l..O.*..>...S.|
00000090  ba 4a a8 f2 e7 6a 79 09  e6 40 93 04 5e ff 1c 7d  |.J...jy..@..^..}|
000000a0  b2 74 02 5a 97 41 f3 8f  c9 a8 d7 50 9d 67 9b 34  |.t.Z.A.....P.g.4|
000000b0  25 4a 72 73 e9 11 2b e3  42 c2 49 0e a0 55 89 f3  |%Jrs..+.B.I..U..|
000000c0  17 76 7d 91 99 2e 0b 7a  89 06 ad a9 d9 b9 53 53  |.v}....z......SS|
000000d0  0a eb 94 18 df bc dd 01  27 3d 18 8f 49 e0 d1 7b  |........'=..I..{|
000000e0  b7 ae b3 c1 97 99 6e 50  3d ea 2e 3a 80 14 24 70  |......nP=..:..$p|
000000f0  66 41 da 75 9c c7 91 c0  33 9c 8c b5 4b 7e b5 65  |fA.u....3...K~.e|
00000100  99 a4 ba 58 98 a2 36 45  86 28 b4 ca 38 f5 46 85  |...X..6E.(..8.F.|
00000110  c7 b1 ea e0 c2 ee 61 83  51 ba 76 85 9c 86 19 61  |......a.Q.v....a|
00000120  ed 96 1f cb 50 bd a1 19  ba 9e 5d 65 8b a3 91 36  |....P.....]e...6|
00000130  99 84 14 e0 62 30 d5 d5  c4 7d 1b e9 7f 98 01 5f  |....b0...}....._|
00000140  f3 b0 80 bc 3c 4c 9f c3  2f d2 f5 15 2a c2 66 0a  |....<L../...*.f.|
00000150  93 a0 16 7f 19 d7 d2 98  e1 d8 06 53 1a 48 36 e5  |...........S.H6.|
00000160  02 3d d0 d1 61 cb 69 1a  06 49 76 bb ef de be a7  |.=..a.i..Iv.....|
00000170  30 34 d2 e0 91 a6 1d 1b  e2 7a 6c 0c 44 9e 85 19  |04.......zl.D...|
00000180  55 bb bc d8 68 37 6b fb  df ca 52 06 61 40 5c b2  |U...h7k...R.a@\.|
00000190  12 57 ed a2 40 91 4b a8  a9 08 2a 82 93 6d 60 02  |.W..@.K...*..m`.|
000001a0  47 d8 3d e4 4e 54 90 9c  9e 16 61 c2 7c d2 e6 c1  |G.=.NT....a.|...|
000001b0  e5 a3 1b 62 15 61 0d 22  c2 16 34 ac 26 7a 00 0f  |...b.a."..4.&z..|
000001c0  ff ff 83 0f ff ff 02 00  00 00 00 58 d5 11 00 0f  |...........X....|
000001d0  ff ff 05 0f ff ff e2 5c  d5 11 20 73 c2 00 00 00  |.......\.. s....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-11-06
Here is the deal if you want this to work and you have nothing to lose on W7.

Boot the live cd of Ubuntu open gparted and it looks from the script that sda1 sda2 and sda4 are all inline on the HD delete all three if this is the case. Then make the area unallocated into a ntfs partition. Boot the W7 cd and install to that partition you built.

This is exactly my original advice, I guess it is best to check what has actually been done.

Post a screenshot of gparted from the live cd and I can gimp it up if needed. Gimp is a graphic tool similar to photoshop probably.

I guess it might help me to know do you want windows in the whole area that it covers now, the install can probably be repaired quite easily. This would mean that the sda1 and sda2 partitions are dead weight, and the area they take up really is where W7 should be, at the front of the disc.

---

### Post by eurekabru on 2010-11-06
> **wilee-nilee said:**
> Boot the live cd of Ubuntu open gparted **and it looks from the script that sda1 sda2 and sda4 are all inline on the HD delete all three if gthis is the case.** Then make the area left into a ntfs partition. Boot the W7 cd and install to that partition you built.

This is exactly my original advice, I guess it is best to check what has actually been done.

Post a screenshot of gparted from the live cd and I can gimp it up if needed. Gimp is a graphic tool similar to photoshop probably.

I'm not sure what the bolded part means. 

What I did earlier in this thread was delete the Win7 partition. Format it to NTFS and installed Win7 to it again. Isn't that what you are/were saying ?

Will the gparted result be different on the LiveCd from what i have in my current Ubuntu session?

---

### Post by wilee-nilee on 2010-11-06
> **eurekabru said:**
> I'm not sure what the bolded part means. 

What I did earlier in this thread was delete the Win7 partition. Format it to NTFS and installed Win7 to it again. Isn't that what you are/were saying ?

Will the gparted result be different on the LiveCd from what i have in my current Ubuntu session?

You can use the gparted from the install sorry. Take a screen shot and post it.

---

### Post by eurekabru on 2010-11-06
> **wilee-nilee said:**
> You can use the gparted from the install sorry. Take a screen shot and post it.

Sorry about the delay. Compiz has apparently disabled my printscreen... 

Here is the screenshot : [http://img441.imageshack.us/img441/2330/gpartedeurekabru.png](http://img441.imageshack.us/img441/2330/gpartedeurekabru.png)

---

### Post by wilee-nilee on 2010-11-06
So I have circled what needs to be removed
[ATTACH]174824[/ATTACH] **click on the picture to see it**
they are in line left to right. If you remove them and make one ntfs partition in there place with gparted and then install W7 to that one partition, you should be set. You will have to reload grub again, from a live cd after installing W7.

The original partitions were never removed and they are screwed up sda1 and sda2. sda4 could be repaired but to be honest just doing it the way I describe here will give you W7 in that whole area if that is what you want.

You could make a smaller partition then (the area left empty) after deleting those 3 partitions, if you wanted to have another ntfs partition in there which would show as a D in the system.

The main thing here is that most of all sda1 and sda 2 are dead wieght and screwing up the situation sda4 is repairable but why bother when you can delete all three build the ntfs and install and enjoy.

---

### Post by eurekabru on 2010-11-06
> **wilee-nilee said:**
> So I have circled what needs to be removed
[ATTACH]174824[/ATTACH] **click on the picture to see it**
they are in line left to right. If you remove them and make one ntfs partition in there place with gparted and then install W7 to that one partition, you should be set. You will have to reload grub again, from a live cd after installing W7.

The original partitions were never removed and they are screwed up sda1 and sda2. sda4 could be repaired but to be honest just doing it the way I describe here will give you W7 in that whole area if that is what you want.

You could make a smaller partition then (the area left empty) after deleting those 3 partitions, if you wanted to have another ntfs partition in there which would show as a D in the system.

The main thing here is that most of all sda1 and sda 2 are dead wieght and screwing up the situation sda4 is repairable but why bother when you can delete all three build the ntfs and install and enjoy.

This makes sense. 

I'm backing up some files and shall get rid of those three partitions. How do I go about creating a boot partition and a partition to use for ''storage'' purposes. I don't want to end up creating a partition that's gonna screw up things once more. 130gb is just too big for Windows...

---

### Post by wilee-nilee on 2010-11-06
> **eurekabru said:**
> This makes sense. 

I'm backing up some files and shall get rid of those three partitions. How do I go about creating a boot partition and a partition to use for ''storage'' purposes. I don't want to end up creating a partition that's gonna screw up things once more. 130gb is just too big for Windows...

Actually if you make one ntfs partiton for the main install of W7 first the size you want then install to it the boot partition will not be needed everything goes to the main OS. Here is a picture of my dual boot.
[ATTACH]174826[/ATTACH]
You will notice only one W7 that is all I need, but the files that were in your bootloader partition are put in the main OS when you install to a single partition rather then letting the W7 installer build the partitions. This is actually better in that a single HD can only have 4 primary partitions, so having one just 1 for 100mib of booting is what I would call kookie engineering. This is a standard install method nothing Linux centric going on here other then a user knowing how to get the most from the single HD.

So build that ntfs with gparted the size you want in that open space, make sure it is large enough you have about 150 gigs to work with, I would go with a minimum of 30-40 gigs you have to decide. Then install W7 to that new partition still leaving the blank space left alone after you made the ntfs for the install.

I would get W7 installed, make sure it works reload grub to the mbr then you can go ahead and make that empty space how you like. You will have room for 2 primary partitions, but it sounds like you just want a ntfs that can be seen from W7 or Ubuntu for media...etc.

I am suspect you can build all the ntfs partitions you want before doing the W7 install, as long as you install to the correct one, but I rather error on the side of caution here.

I have to wonder here to that your W7 originally went south on you, make sure you scan all that you have saved with some good AV programs. There are a bunch of free ones that are pretty good, but really the user is the weakest link usually.

---

### Post by eurekabru on 2010-11-07
> **wilee-nilee said:**
> Actually if you make one ntfs partiton for the main install of W7 first the size you want then install to it the boot partition will not be needed everything goes to the main OS. Here is a picture of my dual boot.
[ATTACH]174826[/ATTACH]
You will notice only one W7 that is all I need, but the files that were in your bootloader partition are put in the main OS when you install to a single partition rather then letting the W7 installer build the partitions. This is actually better in that a single HD can only have 4 primary partitions, so having one just 1 for 100mib of booting is what I would call kookie engineering. This is a standard install method nothing Linux centric going on here other then a user knowing how to get the most from the single HD.

So build that ntfs with gparted the size you want in that open space, make sure it is large enough you have about 150 gigs to work with, I would go with a minimum of 30-40 gigs you have to decide. Then install W7 to that new partition still leaving the blank space left alone after you made the ntfs for the install.

I would get W7 installed, make sure it works reload grub to the mbr then you can go ahead and make that empty space how you like. You will have room for 2 primary partitions, but it sounds like you just want a ntfs that can be seen from W7 or Ubuntu for media...etc.

I am suspect you can build all the ntfs partitions you want before doing the W7 install, as long as you install to the correct one, but I rather error on the side of caution here.

I have to wonder here to that your W7 originally went south on you, make sure you scan all that you have saved with some good AV programs. There are a bunch of free ones that are pretty good, but really the user is the weakest link usually.

Here's my new gparted screenshot after I've install Win7 on it. [http://img812.imageshack.us/img812/2361/screenshotae.png](http://img812.imageshack.us/img812/2361/screenshotae.png)

As well as the boot info script results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    63,344,294    63,344,232   7 HPFS/NTFS
/dev/sda2         313,202,686   625,141,759   311,939,074   5 Extended
/dev/sda5         313,202,688   612,397,799   299,195,112  83 Linux
/dev/sda6         612,399,104   625,141,759    12,742,656  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        086554FC05B7D283                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b6a0fcda-459e-4193-8193-5a37b3dd9db7   ext4                                     
/dev/sda6        f0dcc32c-fa2f-42d2-9ab9-14dc8c0cc72d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/b6a0fcda-459e-4193-8193-5a37b3dd9db7 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/086554FC05B7D283  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f0dcc32c-fa2f-42d2-9ab9-14dc8c0cc72d none            swap    sw              0       0
UUID=4ADC6A81DC6A6763 /media/sda1 ntfs-3g users 0 0
UUID=1E686D8C686D638D /media/sda2 ntfs-3g users 0 0

=================== sda5: Location of files loaded by Grub: ===================


 293.6GB: boot/grub/core.img
 298.9GB: boot/grub/grub.cfg
 293.7GB: boot/initrd.img-2.6.32-21-generic
 266.5GB: boot/initrd.img-2.6.32-25-generic
 293.6GB: boot/vmlinuz-2.6.32-21-generic
 293.7GB: boot/vmlinuz-2.6.32-25-generic
 266.5GB: initrd.img
 293.7GB: initrd.img.old
 293.7GB: vmlinuz
 293.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  bb 03 f9 83 b4 0a d8 d8  91 b9 ce 81 a5 7b 1d 13  |.............{..|
00000010  29 b0 ca a3 57 70 51 fc  48 b0 e7 16 69 4e d7 fd  |)...WpQ.H...iN..|
00000020  c1 f4 1d 4c 8f 81 fa 5c  2d 59 4e 58 d6 d8 5b 50  |...L...\-YNX..[P|
00000030  fd 70 26 d1 3e ff 36 c9  ad ac 59 4f 34 b8 1e 1e  |.p&.>.6...YO4...|
00000040  19 8f 7d ba b8 1a 0e 66  d8 08 7d ed a2 29 a9 cc  |..}....f..}..)..|
00000050  35 99 40 69 45 82 74 d3  34 a0 7d 00 62 0d f7 f3  |5.@iE.t.4.}.b...|
00000060  2e a7 2d ba 19 47 ca 35  18 f6 dd 16 13 d3 60 af  |..-..G.5......`.|
00000070  94 25 08 f8 f6 0a 7d 77  69 bd 0e 68 4a 74 b4 e5  |.%....}wi..hJt..|
00000080  de 99 6c 96 a5 4f b5 2a  d3 a1 3e d6 e1 86 53 c8  |..l..O.*..>...S.|
00000090  ba 4a a8 f2 e7 6a 79 09  e6 40 93 04 5e ff 1c 7d  |.J...jy..@..^..}|
000000a0  b2 74 02 5a 97 41 f3 8f  c9 a8 d7 50 9d 67 9b 34  |.t.Z.A.....P.g.4|
000000b0  25 4a 72 73 e9 11 2b e3  42 c2 49 0e a0 55 89 f3  |%Jrs..+.B.I..U..|
000000c0  17 76 7d 91 99 2e 0b 7a  89 06 ad a9 d9 b9 53 53  |.v}....z......SS|
000000d0  0a eb 94 18 df bc dd 01  27 3d 18 8f 49 e0 d1 7b  |........'=..I..{|
000000e0  b7 ae b3 c1 97 99 6e 50  3d ea 2e 3a 80 14 24 70  |......nP=..:..$p|
000000f0  66 41 da 75 9c c7 91 c0  33 9c 8c b5 4b 7e b5 65  |fA.u....3...K~.e|
00000100  99 a4 ba 58 98 a2 36 45  86 28 b4 ca 38 f5 46 85  |...X..6E.(..8.F.|
00000110  c7 b1 ea e0 c2 ee 61 83  51 ba 76 85 9c 86 19 61  |......a.Q.v....a|
00000120  ed 96 1f cb 50 bd a1 19  ba 9e 5d 65 8b a3 91 36  |....P.....]e...6|
00000130  99 84 14 e0 62 30 d5 d5  c4 7d 1b e9 7f 98 01 5f  |....b0...}....._|
00000140  f3 b0 80 bc 3c 4c 9f c3  2f d2 f5 15 2a c2 66 0a  |....<L../...*.f.|
00000150  93 a0 16 7f 19 d7 d2 98  e1 d8 06 53 1a 48 36 e5  |...........S.H6.|
00000160  02 3d d0 d1 61 cb 69 1a  06 49 76 bb ef de be a7  |.=..a.i..Iv.....|
00000170  30 34 d2 e0 91 a6 1d 1b  e2 7a 6c 0c 44 9e 85 19  |04.......zl.D...|
00000180  55 bb bc d8 68 37 6b fb  df ca 52 06 61 40 5c b2  |U...h7k...R.a@\.|
00000190  12 57 ed a2 40 91 4b a8  a9 08 2a 82 93 6d 60 02  |.W..@.K...*..m`.|
000001a0  47 d8 3d e4 4e 54 90 9c  9e 16 61 c2 7c d2 e6 c1  |G.=.NT....a.|...|
000001b0  e5 a3 1b 62 15 61 0d 22  c2 16 34 ac 26 7a 00 0f  |...b.a."..4.&z..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 e8 5a d5 11 00 fe  |...........Z....|
000001d0  ff ff 05 fe ff ff ea 5a  d5 11 18 75 c2 00 00 00  |.......Z...u....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```What should my next step be? Redo these steps?

---

### Post by drs305 on 2010-11-07
> **eurekabru said:**
> What should my next step be? Redo these steps?

If all you want to do now is install Grub 2, boot the LiveCD, mount sda5 and install Grub. It should pick up your Windows installation and display  it in the Grub menu at boot.

Boot the LiveCD, open a terminal, and run these commands. Note you do NOT include the partition number in the second command (sda NOT sda5):
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Once you have booted via the Grub menu, you might run the following to make sure grub.cfg is updated:
```
sudo update-grub
```

---

### Post by wilee-nilee on 2010-11-07
I would follow drs305's commands, they are correct and this mod if you look in their signature knowns all about grub for sure and reading the script.

Let us know how it ends up. The gparted shot looks good you have W7 in one partition small enough to work, and lots of free space that can contain two more primary partitions if you want to make two more, for storing stuff.

Also if you have a external drive the backup system for W7 is very good, you can back up a image of the whole partition do it now while fresh and then all you have to do is use the image in the future to reset anything gone wrong. to get to backup and restore just type it in the start in W7 and then well I think you know what to do.;)

---

### Post by eurekabru on 2010-11-07
Alright I now have the grub loader with Win7 as well as my linux options and memtest.

My problem now is that when ubuntu is loading I get a message saying:

[B][I]The disk drive for /media/sda1 is not ready yet or not present. Continue to wait; or press S to Skip mounting or M for manual recovery. 

Skipping brings up the same message for sda2 and mounting brings me up to a root command line.[/I][/B] 


I'm pretty sure this is because I got the partitions wrong when I first tried to reinstate grub. I did it for both sda1 and sda2...  

How do I get ubuntu to stop trying to mount sda1 and sda2 at startup ?

---

### Post by sikander3786 on 2010-11-07
I think it is a problem with your /etc/fstab. Please post the output of

```
cat etc/fstab
```

```
sudo blkid
```

---

### Post by eurekabru on 2010-11-07
> **sikander3786 said:**
> I think it is a problem with your /etc/fstab. Please post the output of

```
cat etc/fstab
``````
sudo blkid
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f0dcc32c-fa2f-42d2-9ab9-14dc8c0cc72d none            swap    sw              0       0
UUID=4ADC6A81DC6A6763 /media/sda1 ntfs-3g users 0 0
UUID=1E686D8C686D638D /media/sda2 ntfs-3g users 0 0

```

```
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="086554FC05B7D283" TYPE="ntfs" 
/dev/sda5: UUID="b6a0fcda-459e-4193-8193-5a37b3dd9db7" TYPE="ext4" 
/dev/sda6: UUID="f0dcc32c-fa2f-42d2-9ab9-14dc8c0cc72d" TYPE="swap" 

```

---

### Post by wilee-nilee on 2010-11-07
> **eurekabru said:**
> Alright I now have the grub loader with Win7 as well as my linux options and memtest.

My problem now is that when ubuntu is loading I get a message saying:

[B][I]The disk drive for /media/sda1 is not ready yet or not present. Continue to wait; or press S to Skip mounting or M for manual recovery. 

Skipping brings up the same message for sda2 and mounting brings me up to a root command line.[/I][/B] 
 

I'm pretty sure this is because I got the partitions wrong when I first tried to reinstate grub. I did it for both sda1 and sda2...  

How do I get ubuntu to stop trying to mount sda1 and sda2 at startup ?

If you come back still having problems post the bootscript as well. ;) Any changes done and not working generally will garner this request.

---

### Post by eurekabru on 2010-11-07
> **wilee-nilee said:**
> If you come back still having problems post the bootscript as well. ;) Any changes done and not working generally will garner this request.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    63,344,294    63,344,232   7 HPFS/NTFS
/dev/sda2         313,202,686   625,141,759   311,939,074   5 Extended
/dev/sda5         313,202,688   612,397,799   299,195,112  83 Linux
/dev/sda6         612,399,104   625,141,759    12,742,656  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        086554FC05B7D283                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b6a0fcda-459e-4193-8193-5a37b3dd9db7   ext4                                     
/dev/sda6        f0dcc32c-fa2f-42d2-9ab9-14dc8c0cc72d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Ubuntu 10.04 LTS i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6a0fcda-459e-4193-8193-5a37b3dd9db7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 086554fc05b7d283
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b6a0fcda-459e-4193-8193-5a37b3dd9db7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f0dcc32c-fa2f-42d2-9ab9-14dc8c0cc72d none            swap    sw              0       0
UUID=4ADC6A81DC6A6763 /media/sda1 ntfs-3g users 0 0
UUID=1E686D8C686D638D /media/sda2 ntfs-3g users 0 0

=================== sda5: Location of files loaded by Grub: ===================


 293.6GB: boot/grub/core.img
 299.0GB: boot/grub/grub.cfg
 293.7GB: boot/initrd.img-2.6.32-21-generic
 266.5GB: boot/initrd.img-2.6.32-25-generic
 293.6GB: boot/vmlinuz-2.6.32-21-generic
 293.7GB: boot/vmlinuz-2.6.32-25-generic
 266.5GB: initrd.img
 293.7GB: initrd.img.old
 293.7GB: vmlinuz
 293.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  bb 03 f9 83 b4 0a d8 d8  91 b9 ce 81 a5 7b 1d 13  |.............{..|
00000010  29 b0 ca a3 57 70 51 fc  48 b0 e7 16 69 4e d7 fd  |)...WpQ.H...iN..|
00000020  c1 f4 1d 4c 8f 81 fa 5c  2d 59 4e 58 d6 d8 5b 50  |...L...\-YNX..[P|
00000030  fd 70 26 d1 3e ff 36 c9  ad ac 59 4f 34 b8 1e 1e  |.p&.>.6...YO4...|
00000040  19 8f 7d ba b8 1a 0e 66  d8 08 7d ed a2 29 a9 cc  |..}....f..}..)..|
00000050  35 99 40 69 45 82 74 d3  34 a0 7d 00 62 0d f7 f3  |5.@iE.t.4.}.b...|
00000060  2e a7 2d ba 19 47 ca 35  18 f6 dd 16 13 d3 60 af  |..-..G.5......`.|
00000070  94 25 08 f8 f6 0a 7d 77  69 bd 0e 68 4a 74 b4 e5  |.%....}wi..hJt..|
00000080  de 99 6c 96 a5 4f b5 2a  d3 a1 3e d6 e1 86 53 c8  |..l..O.*..>...S.|
00000090  ba 4a a8 f2 e7 6a 79 09  e6 40 93 04 5e ff 1c 7d  |.J...jy..@..^..}|
000000a0  b2 74 02 5a 97 41 f3 8f  c9 a8 d7 50 9d 67 9b 34  |.t.Z.A.....P.g.4|
000000b0  25 4a 72 73 e9 11 2b e3  42 c2 49 0e a0 55 89 f3  |%Jrs..+.B.I..U..|
000000c0  17 76 7d 91 99 2e 0b 7a  89 06 ad a9 d9 b9 53 53  |.v}....z......SS|
000000d0  0a eb 94 18 df bc dd 01  27 3d 18 8f 49 e0 d1 7b  |........'=..I..{|
000000e0  b7 ae b3 c1 97 99 6e 50  3d ea 2e 3a 80 14 24 70  |......nP=..:..$p|
000000f0  66 41 da 75 9c c7 91 c0  33 9c 8c b5 4b 7e b5 65  |fA.u....3...K~.e|
00000100  99 a4 ba 58 98 a2 36 45  86 28 b4 ca 38 f5 46 85  |...X..6E.(..8.F.|
00000110  c7 b1 ea e0 c2 ee 61 83  51 ba 76 85 9c 86 19 61  |......a.Q.v....a|
00000120  ed 96 1f cb 50 bd a1 19  ba 9e 5d 65 8b a3 91 36  |....P.....]e...6|
00000130  99 84 14 e0 62 30 d5 d5  c4 7d 1b e9 7f 98 01 5f  |....b0...}....._|
00000140  f3 b0 80 bc 3c 4c 9f c3  2f d2 f5 15 2a c2 66 0a  |....<L../...*.f.|
00000150  93 a0 16 7f 19 d7 d2 98  e1 d8 06 53 1a 48 36 e5  |...........S.H6.|
00000160  02 3d d0 d1 61 cb 69 1a  06 49 76 bb ef de be a7  |.=..a.i..Iv.....|
00000170  30 34 d2 e0 91 a6 1d 1b  e2 7a 6c 0c 44 9e 85 19  |04.......zl.D...|
00000180  55 bb bc d8 68 37 6b fb  df ca 52 06 61 40 5c b2  |U...h7k...R.a@\.|
00000190  12 57 ed a2 40 91 4b a8  a9 08 2a 82 93 6d 60 02  |.W..@.K...*..m`.|
000001a0  47 d8 3d e4 4e 54 90 9c  9e 16 61 c2 7c d2 e6 c1  |G.=.NT....a.|...|
000001b0  e5 a3 1b 62 15 61 0d 22  c2 16 34 ac 26 7a 00 0f  |...b.a."..4.&z..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 e8 5a d5 11 00 fe  |...........Z....|
000001d0  ff ff 05 fe ff ff ea 5a  d5 11 18 75 c2 00 00 00  |.......Z...u....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by sikander3786 on 2010-11-07
UUID of sda1 doesn't match the one in fstab and sda2 is not present at all. You have got only 1 primary partition. You need to edit /etc/fstab and update the entries there. But first, wait for wilee-nilee's suggestion here if he also finds something offensive in the bootinfoscript.

---

### Post by wilee-nilee on 2010-11-07
> **sikander3786 said:**
> UUID of sda1 doesn't match the one in fstab and sda2 is not present at all. You have got only 1 primary partition. You need to edit /etc/fstab and update the entries there. But first, wait for wilee-nilee's suggestion here if he also finds something offensive in the bootinfoscript.

Good eye on the fstab I'm not familiar with any way of fixing this, Other then reloading grub again as drs305 commands did. I have to get to some important study so good luck.;)

---

### Post by eurekabru on 2010-11-07
> **wilee-nilee said:**
> Good eye on the fstab I'm not familiar with any way of fixing this, Other then reloading grub again as drs305 commands did. I have to get to some important study so good luck.;)

> **sikander3786 said:**
> UUID of sda1 doesn't match the one in fstab  and sda2 is not present at all. You have got only 1 primary partition.  You need to edit /etc/fstab and update the entries there. But first,  wait for wilee-nilee's suggestion here if he also finds something  offensive in the bootinfoscript.

Thanks for the help wilee-nilee. I really appreciate you taking the time to help me.

sikander3786: How do I go about replacing the UUID. Which numbers are the good ones? Can I do it with gedit /etc/fstab/ ?

---

### Post by sikander3786 on 2010-11-07
Ok. Edit /etc/fstab by

```
sudo nano /etc/fstab
```

Delete the UUID of sda1 and replace it with the one you got from blkid i.e, 086554FC05B7D283 so your entry for sda1 looks like

```
UUID=086554FC05B7D283 /media/sda1 ntfs-3g users 0 0
```

Delete the entire entry for sda2 as it is not present at all, save and reboot to see if it worked.

Edit: You can also use gedit if you are able to boot to the desktop. It would be easier than nano but you need to edit by gksudo instead of sudo

```
gksudo gedit /etc/fstab
```

---

### Post by eurekabru on 2010-11-07
> **sikander3786 said:**
> Ok. Edit /etc/fstab by

```
sudo nano /etc/fstab
```Delete the UUID of sda1 and replace it with the one you got from blkid i.e, 086554FC05B7D283 so your entry for sda1 looks like

```
UUID=086554FC05B7D283 /media/sda1 ntfs-3g users 0 0
```Delete the entire entry for sda2 as it is not present at all, save and reboot to see if it worked.

Edit: You can also use gedit if you are able to boot to the desktop. It would be easier than nano but you need to edit by gksudo instead of sudo

```
gksudo gedit /etc/fstab
```

This worked.
On first reboot I got this message [I][B]: (process:335): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

[/B][/I]Couldn't do anything so I had to force a reboot. 
Everything booted just fine this time. I rebooted a third time to make sure and it is still loading fine. Let's hope it was a one time thing.

Thanks to everyone! You guys are so helpful. :P
You can mark this as [solved]!

---

### Post by sikander3786 on 2010-11-07
You are more than Welcome :-) Glad to know, It worked!

You need to mark it solved yourself. Use Thread Tools (link in red color) near the top of the page.

---

### Post by wilee-nilee on 2010-11-07
Yipee this is the best news I have heard today, at times it certainly takes several of us to figure this stuff out, kudos to sikander3786 for being there when we all need them. ;)

---

