---
title: "error: unknown filesystem grub rescue (WinXP, Win7 and Ubuntu triple boot)"
date: 2010-11-20
forum: General Help
---

### Post by Davewagon on 2010-11-20
Hello Guys,

I'm having a bit of a headache with my PC and my Ubuntu 10.10 installation. I am a compete newbie to Ubuntu and while I'm not completely computer illiterate, I think I may be out of my depth ...

I've just installed Ubuntu 10.10 and have the now famous: 
**error: unknown filesystem grub rescue**

Here's a bit of background:

I have a 500gb hdd which I have partitioned in the following way:

[COLOR=Red]A 50gb (51,200mb) partition which has Windows XP installed[/COLOR], [sda1 I think]
A 50gb (51,200mb) partition which has Windows 7 installed, [sda7 I think]
[COLOR=Blue]A 500mb /boot partition (Ext4) (this is also a primary drive/partition if that makes any difference)
A 10gb (10,240mb) /root partition (Ext4)
A 5gb (5,120mb) Swap area
A 34gb (35,340mb) /home partition (Ext4)[/COLOR]
[these are any of sda2, 3, 5 or 6]

The rest of the drive is unallocated [sda4 I believe]

My idea was to have a nice tidy install of 3 x 50gb partitions for the three operating systems ( I just split the 50gb I sidelined for ubuntu into the 4 partitions above, highlighted blue).

And now I'm stuck at the grub rescue error when ever I turn on the pc.

I installed Ubuntu using a usb stick and have booted from the usb in order to get a bootinfo script log (which is attached below)

I've looked at various threads but am a bit overwhelmed at what I'm reading or trying to achieve.

I don't know whether I'm trying to restore an Ubuntu grub bootloader, a WinXP bootloader or a Win7 bootloader as indicated here: 

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

grub, or grub 2 or whether I have some sort of tasty maggot in my computer :p

I desperatley need to get access to my Windows software, and think for the time being I will remove Ubuntu until I get more time to really read into it (If we can get it working, then great, I'll keep it)

Any and all help is greatly appreciated

Many Thanks, 
David

Here is my bootinfo script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,872,319   104,872,257   7 HPFS/NTFS
/dev/sda2         314,601,472   315,578,367       976,896  83 Linux
/dev/sda3         315,578,368   325,578,751    10,000,384  82 Linux swap / Solaris
/dev/sda4         104,873,983   298,776,869   193,902,887   f W95 Ext d (LBA)
/dev/sda5         104,873,984   124,872,703    19,998,720  83 Linux
/dev/sda6         124,874,752   193,896,447    69,021,696  83 Linux
/dev/sda7         193,904,613   298,776,869   104,872,257   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3E5C2C8E5C2C434F                       ntfs       Windows XP                    
/dev/sda2        c6b7238d-d36c-46a5-b112-d42ed043045c   ext4                                     
/dev/sda3        c4d53c8e-6238-4b15-9722-53c3a350bd2c   swap                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        0fa20bbb-1800-4b8b-b600-cdccc9c0a13b   ext4                                     
/dev/sda6        27586bc5-2296-4939-a485-ddb09bc0bc35   ext4                                     
/dev/sda7        01CB83404410AC00                       ntfs       Windows 7                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B805-6D32                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT

============================= sda2/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 0fa20bbb-1800-4b8b-b600-cdccc9c0a13b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set c6b7238d-d36c-46a5-b112-d42ed043045c
set locale_dir=($root)/grub/locale
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
    search --no-floppy --fs-uuid --set c6b7238d-d36c-46a5-b112-d42ed043045c
    linux    /vmlinuz-2.6.35-22-generic root=UUID=0fa20bbb-1800-4b8b-b600-cdccc9c0a13b ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set c6b7238d-d36c-46a5-b112-d42ed043045c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=0fa20bbb-1800-4b8b-b600-cdccc9c0a13b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set c6b7238d-d36c-46a5-b112-d42ed043045c
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set c6b7238d-d36c-46a5-b112-d42ed043045c
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e5c2c8e5c2c434f
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

=================== sda2: Location of files loaded by Grub: ===================


 161.3GB: grub/core.img
 161.3GB: grub/grub.cfg
 161.1GB: initrd.img-2.6.35-22-generic
 161.0GB: vmlinuz-2.6.35-22-generic

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=c6b7238d-d36c-46a5-b112-d42ed043045c /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=27586bc5-2296-4939-a485-ddb09bc0bc35 /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=c4d53c8e-6238-4b15-9722-53c3a350bd2c none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  e4 59 cc 94 55 6c 8e 7b  28 47 fa f7 6c 4e 0f d5  |.Y..Ul.{(G..lN..|
00000010  3e c8 9b 7c 06 88 44 ed  7e 8b a6 9e 6d e8 cf fe  |>..|..D.~...m...|
00000020  0d 0c 9e 3e e9 17 4b 31  1d db de d6 03 4a cc 31  |...>..K1.....J.1|
00000030  d2 ad 09 36 d2 9d 9e 5b  4f 6a f6 7e 1e a4 b5 38  |...6...[Oj.~...8|
00000040  b7 3a a4 46 a7 f7 af 62  9f 15 f5 ce e1 24 29 93  |.:.F...b.....$).|
00000050  5f 5c 5b a4 ad 44 ba 33  ae 28 f1 0f 6b 57 76 1d  |_\[..D.3.(..kWv.|
00000060  7b 42 61 97 f2 3a 16 07  12 4b ea 56 20 74 84 5c  |{Ba..:...K.V t.\|
00000070  0b e0 84 d0 c5 4f bd ec  ef 76 9b 0d 2c d8 4b 42  |.....O...v..,.KB|
00000080  0e a7 d6 94 44 5e 8a ac  90 c7 86 21 85 de b3 03  |....D^.....!....|
00000090  a6 53 19 62 fe a1 61 26  dd e4 87 aa 47 3b b2 64  |.S.b..a&....G;.d|
000000a0  f1 35 53 34 f8 49 66 06  be 44 ed 3c c0 e4 2e d2  |.5S4.If..D.<....|
000000b0  81 fc 29 da 03 39 e2 7a  aa d4 3b 6f 52 a3 85 9a  |..)..9.z..;oR...|
000000c0  a8 4a 9f a8 c6 b1 54 02  90 82 d9 ff c3 f1 55 7c  |.J....T.......U||
000000d0  78 f9 62 12 8e 66 5a 2e  ff c5 e7 45 c5 7b 9f c0  |x.b..fZ....E.{..|
000000e0  1d df 2b fd 2e 76 66 44  73 b6 73 29 5c b0 3d aa  |..+..vfDs.s)\.=.|
000000f0  9b 65 40 55 ce 8c 1d 8a  e2 54 e5 59 64 db c2 94  |.e@U.....T.Yd...|
00000100  01 40 be a6 1c af d3 56  b9 02 b6 35 80 ba c7 19  |.@.....V...5....|
00000110  f2 b5 a0 dd b1 a0 92 e9  18 6c ff 35 da d3 f3 a1  |.........l.5....|
00000120  d0 63 26 ee b8 ac 92 22  b8 50 3c c5 d3 4e 1e 1a  |.c&....".P<..N..|
00000130  c1 d8 a3 72 d3 1e 05 20  0f 73 09 4f f2 a8 6e f7  |...r... .s.O..n.|
00000140  1b a0 6e dc 49 b0 77 ab  56 18 24 0f 78 36 ab d3  |..n.I.w.V.$.x6..|
00000150  71 de b0 92 e8 c7 a3 e0  f0 ed f9 9c 24 9d d8 1c  |q...........$...|
00000160  ec fe 38 69 50 7a d7 33  38 65 17 df be e8 ae 07  |..8iPz.38e......|
00000170  26 00 0e c1 d0 89 4d da  3e 01 e4 04 68 df 4f a5  |&.....M.>...h.O.|
00000180  d9 12 31 7b 4b 06 68 7a  c6 56 79 4f 8b a0 ef 00  |..1{K.hz.VyO....|
00000190  eb 42 6b c6 ae 86 a4 4f  b9 73 38 dc e4 ed f7 01  |.Bk....O.s8.....|
000001a0  91 ec 72 9f 7d f0 36 0c  9d c1 3f 19 40 bb a4 f2  |..r.}.6...?.@...|
000001b0  15 be 72 1a 47 b8 2b cc  ac e1 cb 39 b5 28 00 fe  |..r.G.+....9.(..|
000001c0  ff ff 83 fe ff ff 01 00  00 00 00 28 31 01 00 fe  |...........(1...|
000001d0  ff ff 05 fe ff ff c2 2f  31 01 3f 30 1d 04 00 00  |......./1.?0....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 20 00  |.X.SYSLINUX..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 26 00 00 00  |........?...&...|
00000020  c2 9f 77 00 bd 03 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 32 6d 05 b8 4e  4f 20 4e 41 4d 45 20 20  |..)2m..NO NAME  |
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
00000100  7d 00 66 b8 9a dc 55 00  66 ba 00 00 00 00 bb 00  |}.f...U.f.......|
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



```

---

### Post by Davewagon on 2010-11-20
Or if someone could interpret my bootinfo script to see if there are any glaring issues/mistakes,

If not, I'll try to reinstall Grub2 using this guide:

[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Many Thanks, 
David

---

### Post by Quackers on 2010-11-20
Grub is looking in partition 3 for its boot files but they are actually in partition 5, which is where Ubuntu is installed. There may be a couple more problems as well but we can address those later.
As your Ubuntu installation is new you could re-install Ubuntu, presumably without too much hassle??? This would be one option. 
Also whilst re-installing I would not use a separate /boot partition (yours is wrong anyway as it appears to be also the swap partition) as this only complicates matters.

---

### Post by jerome_rajan on 2010-11-28
At The Grub Rescue > prompt, try doing the following. It worked for me.
Got the info from Ubuntu's Grub2 documentation





1. **ls** 
    2. **set prefix=(hdX,Y)/boot/grub**
(X,Y) denotes the number of the partition where Ubuntu is installed. You'll get it from ls. Or if you have no clue, then boot in using a Live CD and do "sudo fdisk -l"

  
    3*. **set root=(hdX,Y)** 
    4. **set** 
    5. **ls /boot** 
    6. **insmod /boot/grub/linux.mod** 
    7*. **linux /vmlinuz root=/dev/sd*XY* ro** 
    8. **initrd /initrd.img** 
    9. **boot**

---

### Post by jerome_rajan on 2010-11-28
I'm sure you'd be able to boot in. Just mention the partition numbers correctly and you'll be good to go. After booting into Ubuntu, re-install Grub2 

sudo grub-install /dev/sdX 
X is the name of the parition, not the number. For eg. if Ubuntu is on sda6, then X=a :D

Cheers!! Lemme know if it works

---

### Post by Spyderkid on 2010-11-28
Could I suggest using windows 7 with xp mode installed so it may un-complicate things or not.

---

### Post by Quackers on 2010-11-28
The OP has a host of problems.
He has Windows XP boot files mixed up with Vista/7 boot files in sda1.
He has 2 of the Ubuntu grub boot files in sda2, but no operating system in there.
Grub is installed in the mbr of sda and looks in partition 3 for boot files. But partition 3 is a swap partition.
sda5 has Ubuntu installed in it but only one of the necessary boot files.
sda7 is labelled as a Windows XP type boot sector, but has Windows 7 installed in it - along with W7 boot files.

That's quite an impressive list of problems imo.
I have no doubt that it is fixable but I would advise a speedier remedy.
Re-install the lot :-)

---

