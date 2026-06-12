---
title: "Ubuntu 10.10 infinite loop reboot"
date: 2010-11-27
forum: General Help
---

### Post by chiquinho78 on 2010-11-27
Hi, guys.

I'm newbie to Ubuntu and I'd like some support with a problem that seems to be frequent (at least, for what I have read here so far).

I've downloaded Ubuntu 10.10 Desktop Edition (64 bits), and I'm trying to run it on my HP8710w with Windows XP SP3, and a HP Recovery Partition. After installing from the Live CD, I was able to restart, select Ubuntu on the GRUB menu and run Ubuntu without any problem. But then, if I restart again and go into Windows XP, the next time I restart, it keeps rebooting in an infinite loop, and the GRUB menu doesn't even appear.

So now, if I want to run Windows, I have to reinstall Ubuntu from the CD again.

After searching on the forums, I found out that disabling some services like hpqwmiex.exe and PCAngel.exe could fix the problem. But this wasn't my case.

So I proceeded with the[_ boot info script_]("http://bootinfoscript.sourceforge.net/"), with the hope you can help me

[HTML]
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   248,554,750   248,554,688   7 HPFS/NTFS
/dev/sda2         372,836,520   390,716,864    17,880,345   7 HPFS/NTFS
/dev/sda3         248,555,518   372,836,351   124,280,834   5 Extended
/dev/sda5         248,555,520   254,554,111     5,998,592  82 Linux swap / Solaris
/dev/sda6         254,556,160   372,836,351   118,280,192  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        432468FB63EEF59D                       ntfs                                     
/dev/sda2        FAFC5F30FC5EE703                       ntfs       HP_RECOVERY                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        b748468d-0849-4bd9-86a9-ef0aae5d1e61   swap                                     
/dev/sda6        f3cccd2e-6543-499a-9934-9a0f51b8b38d   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set f3cccd2e-6543-499a-9934-9a0f51b8b38d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set f3cccd2e-6543-499a-9934-9a0f51b8b38d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set f3cccd2e-6543-499a-9934-9a0f51b8b38d
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f3cccd2e-6543-499a-9934-9a0f51b8b38d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set f3cccd2e-6543-499a-9934-9a0f51b8b38d
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f3cccd2e-6543-499a-9934-9a0f51b8b38d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set f3cccd2e-6543-499a-9934-9a0f51b8b38d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set f3cccd2e-6543-499a-9934-9a0f51b8b38d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 432468fb63eef59d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set fafc5f30fc5ee703
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=f3cccd2e-6543-499a-9934-9a0f51b8b38d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b748468d-0849-4bd9-86a9-ef0aae5d1e61 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 158.4GB: boot/grub/core.img
 139.0GB: boot/grub/grub.cfg
 131.0GB: boot/initrd.img-2.6.35-22-generic
 158.4GB: boot/vmlinuz-2.6.35-22-generic
 131.0GB: initrd.img
 158.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  d4 a0 53 d4 a0 53 d2 a1  51 d2 a1 51 d2 a1 51 d2  |..S..S..Q..Q..Q.|
00000010  a1 51 d2 a1 53 d2 a1 53  d2 a1 53 d1 a0 52 d1 a0  |.Q..S..S..S..R..|
00000020  52 d1 a0 52 d1 a0 52 d1  a0 52 d3 9f 52 d3 9f 52  |R..R..R..R..R..R|
00000030  d3 9f 52 d3 9f 52 d1 a0  52 d2 9e 51 d2 9e 51 d3  |..R..R..R..Q..Q.|
00000040  9f 52 d1 a0 52 d3 9f 52  d2 9e 51 d2 9e 51 d1 9d  |.R..R..R..Q..Q..|
00000050  50 d0 9c 4f d0 9c 4f d0  9c 4f d0 9c 4f cf 9b 4e  |P..O..O..O..O..N|
00000060  d0 9a 4d d0 9a 4d d0 9a  4d d0 9a 4d d0 9a 4d d1  |..M..M..M..M..M.|
00000070  9b 4e d0 9a 4d d0 9b 4b  d1 9c 4c d1 9c 4c cf 9c  |.N..M..K..L..L..|
00000080  4c d3 9b 4c d0 9b 4b be  8a 44 b7 83 41 b4 83 3f  |L..L..K..D..A..?|
00000090  b7 82 43 b6 82 3f c3 92  4e cc 9f 5b c8 9e 59 cc  |..C..?..N..[..Y.|
000000a0  9f 5b cc 9f 5b ca a0 5b  cb 9e 5a bc 8d 49 b6 82  |.[..[..[..Z..I..|
000000b0  3f b8 84 41 b7 83 40 b7  83 40 b7 83 40 b8 83 40  |?..A..@..@..@..@|
000000c0  b6 82 3f c1 90 4c cc 9f  5c cb 9e 5b cb 9e 5b cc  |..?..L..\..[..[.|
000000d0  9f 5c cb 9e 5b cc 9f 5c  bf 8d 4b b6 80 3f b7 83  |.\..[..\..K..?..|
000000e0  41 b6 82 40 b6 80 41 b5  80 41 b9 87 45 cb 9e 5b  |A..@..A..A..E..[|
000000f0  cc 9f 5b cb 9e 5a cc 9f  5b cc 9f 5b cd a0 5c c4  |..[..Z..[..[..\.|
00000100  95 51 b6 82 3f b8 82 41  b7 83 41 b8 82 41 b7 81  |.Q..?..A..A..A..|
00000110  40 b6 82 40 b7 83 41 b5  81 3f be 8e 4c cc 9f 5c  |@..@..A..?..L..\|
00000120  cb 9e 5b cb 9e 5b cc 9f  5c ca 9f 5c cd a0 5d bd  |..[..[..\..\..].|
00000130  89 47 b7 7f 3e b7 81 42  b6 80 41 b6 80 41 b5 81  |.G..>..B..A..A..|
00000140  3f b5 80 41 b5 80 41 c4  94 54 cd a0 5d cb 9e 5b  |?..A..A..T..]..[|
00000150  cc 9c 5a ca 9d 5a cd 9d  5b ca 9a 58 b8 83 44 b5  |..Z..Z..[..X..D.|
00000160  7c 3f b4 7d 40 b3 7d 3e  b4 7e 3f b4 7e 3f b5 7c  ||?.}@.}>.~?.~?.||
00000170  3e b7 7e 40 b3 7d 3e b2  7d 3e c7 95 53 c5 93 51  |>.~@.}>.}>..S..Q|
00000180  b5 81 3f b5 7d 3c ba 80  3f b8 80 3f b7 7f 3e b7  |..?.}<..?..?..>.|
00000190  81 40 b5 7f 3e b8 80 3f  b7 7e 40 b9 7e 40 b8 7f  |.@..>..?.~@.~@..|
000001a0  41 b6 7d 3f b6 7d 3f b6  7d 3f b6 7d 3f b6 7d 3f  |A.}?.}?.}?.}?.}?|
000001b0  b6 7d 3f b6 7d 3f b7 7e  40 b7 7e 40 b7 7e 00 fe  |.}?.}?.~@.~@.~..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 88 5b 00 00 fe  |............[...|
000001d0  ff ff 05 fe ff ff 02 88  5b 00 00 d8 0c 07 00 00  |........[.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
[/HTML]Before going through this procedure of "[Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")", I'd like to know if there's apparently any problem with the logfile posted before.

Thanks in advance.

Regards,
Chiquinho.

---

### Post by oldfred on 2010-11-27
Script looks normal as far as I can tell. 

We have seen issues with certain software normally installed with Win7 from HP or Dell that corrupts grub2 in the MBR. But have not seen that with XP. Are you running something special that would modify MBR. Most XP virus software does not cause issues, perhaps something from Adobe?

You should just be able to reinstall grub2.

#Install MBR from LiveCD, Ubuntu install on sda6 and want grub2 in drive sda's MBR:
#Find linux partition, change sda6 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by chiquinho78 on 2010-11-27
Hi, Oldfred.

Thanks for your fast reply.

I followed what is suggested [here]("http://grub.enbug.org/Grub2LiveCdInstallGuide") , that I think is the same than what you pointed out. After Step 9, I was warned with this:

[HTML]"Sector 33 is already in use by FlexNet; avoiding it.  This software may  cause boot or other problems in future.  Please ask its authors not to  store data in the boot track..."[/HTML]Then, I restarted, logged into Windows and restarted again. And Grub menu appeared, so the problem seems to be fixed. It seems that this FlexNet software writes into the boot sector and can overwrite Grub 2 information. I think that following the steps above I kind of reinstalled Grub avoiding sectors where there is FlexNet information, but that if I continue using Windows and run HP updates, Grub is supposed to be overwritten again... am I right?

I found [here]("http://ubuntuforums.org/showthread.php?t=1620377") a case similar than mine, but I didn't need to remove any HP software in order to access to Grub menu...

How can I uninstall FlexNet, or at least, disable it? It appears to be related with HP update software...

Regards,
Chiquinho.

---

### Post by oldfred on 2010-11-27
I know the grub2 folks were looking for the types of software that was corrupting grub2. They must have added some workarounds.

We just saw another user with flexnet. When I looked it up it was a security feature for (Adobe I think) and writes it data all over the place especially in areas of the hard drive that should be only used for booting. It is as bad as a root virus as it is difficult to remove.

---

