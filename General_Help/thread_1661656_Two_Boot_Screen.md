---
title: "Two Boot Screen"
date: 2011-01-07
forum: General Help
---

### Post by mac4rfree on 2011-01-07
Hi Guys,

I am currently running Win7 in one partition and Ubuntu 10.10 in another partition. Earlier, it was directly booting into Win7 .
So, I added an entry for Ubuntu in MBR using EasyBCD.

Now, When i boot, it first ask me to select Win7 or Ubuntu 10.10(name i have given in EasyBCD).
After selection of Ubuntu, it again goes to another boot screen (the default Grub2 screen), where again i have to select Ubuntu with kernel name ..

In one of my friends laptop, i have seen there is only one boot screen without the first screen...

Can somebody guide me as what i did wrong..

Thanks for your help in advance..
Magesh

---

### Post by mac4rfree on 2011-01-07
Just to give some more information.. find my output of the Boot screen.
> 
   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 172241936 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   167,766,794   167,766,732   7 HPFS/NTFS
/dev/sda2         327,708,670   625,121,279   297,412,610   f W95 Ext d (LBA)
/dev/sda5         331,613,793   625,121,279   293,507,487   7 HPFS/NTFS
/dev/sda6         327,708,672   331,612,159     3,903,488  82 Linux swap / Solaris
/dev/sda3         167,768,064   327,706,623   159,938,560  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2019 MB, 2019557376 bytes
19 heads, 18 sectors/track, 11533 cylinders, total 3944448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192     3,944,447     3,936,256   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B01E99FA1E99BA34                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        e63d174c-5dab-4cd7-8729-57820a142ea8   ext4                                     
/dev/sda5        0E302F6A302F57CB                       ntfs                                     
/dev/sda6        53fc5384-e24b-455f-8f4f-a16f5a74bc7a   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0A8E-B714                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/0E302F6A302F57CB  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/B01E99FA1E99BA34  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/e63d174c-5dab-4cd7-8729-57820a142ea8 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e63d174c-5dab-4cd7-8729-57820a142ea8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e63d174c-5dab-4cd7-8729-57820a142ea8 ro single 
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b01e99fa1e99ba34
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=e63d174c-5dab-4cd7-8729-57820a142ea8 /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  88.1GB: boot/grub/core.img
 137.5GB: boot/grub/grub.cfg
  86.8GB: boot/initrd.img-2.6.35-22-generic
  88.1GB: boot/vmlinuz-2.6.35-22-generic
  86.8GB: initrd.img
  88.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  97 f5 7e ee a5 b5 82 ea  b7 34 88 3b 37 02 35 89  |..~......4.;7.5.|
00000010  9e 0c f2 b1 be b2 75 36  65 75 5c cc 7c e7 3d cc  |......u6eu\.|.=.|
00000020  a1 8d fb 36 30 9d b7 dc  f0 36 ee 0d e7 53 f7 7c  |...60....6...S.||
00000030  c2 a9 d2 37 63 7d 5f eb  38 36 88 b2 97 fb 87 c4  |...7c}_.86......|
00000040  b5 ba 7c d8 92 9d 4e a5  fe 32 ac c0 c7 c4 2d a5  |..|...N..2....-.|
00000050  8f ba ca db 65 a2 4e c6  07 6a 00 ef 24 78 9d 3c  |....e.N..j..$x.<|
00000060  d6 bf d6 2f ac f9 18 8f  c3 c5 e9 f5 b5 f7 e5 0d  |.../............|
00000070  cd 0f fa 2d 64 4c 98 23  9f 8a e2 07 49 f4 7e ab  |...-dL.#....I.~.|
00000080  3b 2d c3 73 ee bd 90 79  21 95 93 5b 7f 19 f9 2d  |;-.s...y!..[...-|
00000090  ae a7 73 3a 67 54 e8 bd  46 f9 6d 03 19 ac 73 a0  |..s:gT..F.m...s.|
000000a0  9d ae 0d 77 22 24 7d 34  94 dc ff 00 16 f9 2e cc  |...w"$}4........|
000000b0  bf aa dc f6 6c 73 ee 6b  8b 7f 74 9d e4 8f 91 4d  |....ls.k..t....M|
000000c0  fe 30 f3 69 c4 cd e9 2f  b5 d0 2b b8 d8 ee 49 0c  |.0.i.../..+...I.|
000000d0  06 bd 60 7c 13 7f 8b 4b  c6 45 dd 51 f1 b4 be e6  |..`|...K.E.Q....|
000000e0  bf 69 d0 8d c6 c3 a8 47  fa ff 00 55 76 65 f4 71  |.i.....G...Uve.q|
000000f0  63 5a e0 72 76 90 e0 08  2d 25 93 20 f2 92 9c de  |cZ.rv...-%. ....|
00000100  87 d7 b1 7a 8f d6 bb 32  2a 71 2c ba 9f 4d 84 82  |...z...2*q,..M..|
00000110  25 cd 0d 3f 8e d3 ca 07  d6 5c ec be ad d7 30 45  |%..?.....\....0E|
00000120  38 ae a2 c6 12 da 8e 40  80 f7 03 3b 88 6c e8 de  |8......@...;.l..|
00000130  44 13 2b 4f a7 b2 ba 3e  b7 dc d6 57 b1 bf 67 da  |D.+O...>...W..g.|
00000140  d0 1b b5 b2 03 0f b4 01  0a 7f 5b 2c 6d 3f 58 7a  |..........[,m?Xz|
00000150  3b 9e 40 12 44 9f 12 60  7e 29 29 6f ad dd 43 3b  |;.@.D..`~))o..C;|
00000160  17 a3 1c 4c ac 77 5d 6b  eb 1e a5 d5 80 31 d9 0e  |...L.w]k.....1..|
00000170  91 e7 3a 0d 36 81 3c 15  1f ab f6 75 6e 9b d0 ec  |..:.6.<....un...|
00000180  c8 73 e9 15 37 13 d4 a0  34 12 e6 96 82 e9 70 20  |.s..7...4.....p |
00000190  0d 7b ea 75 5b 9f 5e 7f  e4 4c cf ea 0f fa a0 a8  |.{.u[.^..L......|
000001a0  63 5a db 7e a9 4b 1d 20  61 39 ba 78 b5 a5 ae 1f  |cZ.~.K. a9.x....|
000001b0  22 92 9c 9e 9d f5 d3 ab  35 98 39 59 6c a8 00 01  |".......5.9Yl...|
000001c0  c1 ff 07 fe ff ff 63 96  3b 00 9f 91 7e 11 00 fe  |......c.;...~...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 90 3b 00 00 00  |............;...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 06 02  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 00 00  |........?.... ..|
00000020  00 10 3c 00 fd 0e 00 00  00 00 00 00 02 00 00 00  |..<.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 14 b7 8e 0a 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 08 20 00 00  66 ba 00 00 00 00 bb 00  |}.f.. ..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
I think my GRUB is installed in sd3.. is that the problem??? iam noob to linux so jus guessing somewhere i read it should be installed in sda...???
Can somebody guide me to move it to sda or wherever it needs to be....

Thanks...

---

### Post by tredegar on 2011-01-07
Your bootinfo script seems to be dated 15 Feb 2010, when ubuntu 10.10 was not released. Perhaps that is the date of the software, not the date you ran it? I am assuming the output from that script is current.

You seem to be using two bootloaders, easyBCD and grub.
You only need grub.

This is what you need to do. Pay very careful attention to all typing before you press Return!

Boot to ubuntu.
In a terminal:
```
sudo grub-install /dev/sda
sudo nano /etc/default/grub
```
Use **nano** to make sure the first lines in that file are set to look like this (or your boot menu may be hidden):
```
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=4
```
Save ("Write Out") the file, Exit nano.
Now update grub:
```
sudo update-grub
```
Reboot, and all should be well.

If not, please see [here]("http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html")

---

### Post by mac4rfree on 2011-01-07
Ok.. i  am going to try dis.. and keep all posted.. Btw thanks for helping me out.. Fingers crossed.. :)

---

### Post by mac4rfree on 2011-01-07
Viola!!! that worked like charm... Thanx mate!!!!

---

### Post by mac4rfree on 2011-01-07
Viola!!! that worked like charm... Thanx mate!!!!

---

### Post by mac4rfree on 2011-01-07
Viola!!! That Worked like a charm and fixed the issue!!! THanks mate u made my day!!!

---

### Post by mac4rfree on 2011-01-07
Viola!!! That Worked like a charm and fixed the issue!!! THanks mate u made my day!!!

---

