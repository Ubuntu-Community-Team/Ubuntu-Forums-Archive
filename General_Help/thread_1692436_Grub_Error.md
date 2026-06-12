---
title: "Grub Error"
date: 2011-02-21
forum: General Help
---

### Post by neonboy on 2011-02-21
Sorry guys, I was playing with grub configuration and now when i try to boot

it gives me just grub command line.

There is a way to start a generic or recovery mode from there ?


Thanks in advance.

---

### Post by Rubi1200 on 2011-02-21
Hi and welcome to the forums :-)

We need more information:

1. what configuration did you change?

2. what version Ubuntu are you using?

3. do you see a grub prompt or grub rescue prompt (there is a difference)?

Try and be clear about what you did so we can help you sort this out.

For help with booting from the prompt, see here:
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Thanks.

---

### Post by neonboy on 2011-02-21
Hi Ruby, your're so kind to listen..

Grub on start gives me an error about color of splash image.

Then I couldn't find any kernel to boot, only the command line.

The problem is with an ubuntu netbook ed. 10.10,

it gives no clues about rescue, so i think is simply the grub prompt.

I've tried to fix it from live usb..

Now I'm going to purge grub and reinstall, following the guide you give me.

I'll let you know..


Appreciate your help, thanks again.

---

### Post by Rubi1200 on 2011-02-21
No problem about the help. You might want to consider posting the results of the boot info script first before purging and reinstalling grub.

Also, if you made changes to the 05_debian_theme file, post the contents here so we can take a look at that too.

Let us know what other help you need.

---

### Post by neonboy on 2011-02-21
Fine I was just backuping a little so i still didn't start operation on grub.

Exactly how did i get the results from a boot info script? Sorry I'm a bit profane..


Cheers

---

### Post by oldfred on 2011-02-21
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by neonboy on 2011-02-22
Ok Doctors, that's my results.txt hope my baby laptop is fine

Boot Info Script 0.55    ```
dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2063 MB, 2063073280 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4029440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             62     4,027,519     4,027,458   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   482,256,895   482,254,848  83 Linux
/dev/sdb2         482,258,942   488,396,799     6,137,858   5 Extended
/dev/sdb5         482,258,944   488,396,799     6,137,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       c2743de5-29cb-4d3f-bbfd-60c1e1387fb4   ext3                                     
/dev/sda1        F005-F2E2                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        b76ffa61-cbf0-4afa-b4fe-a156261dfc2e   ext3                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        3161d838-5986-4413-a582-5c52bead75b2   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/b76ffa61-cbf0-4afa-b4fe-a156261dfc2e ext3       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b76ffa61-cbf0-4afa-b4fe-a156261dfc2e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x600x16
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b76ffa61-cbf0-4afa-b4fe-a156261dfc2e
set locale_dir=($root)/boot/grub/locale
set lang=it
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b76ffa61-cbf0-4afa-b4fe-a156261dfc2e
insmod jpeg
if background_image /boot/grub/Bonsaisplash.jpg ; then
  set color_normal=gray/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# Commented out by Dropbox
# /dev/sda1       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3161d838-5986-4413-a582-5c52bead75b2 none            swap    sw              0       0
/dev/sda1 / ext3 errors=remount-ro,user_xattr 0 1

=================== sdb1: Location of files loaded by Grub: ===================


 193.6GB: boot/grub/core.img
 193.6GB: boot/grub/grub.cfg
 193.6GB: boot/initrd.img-2.6.35-22-generic
 193.6GB: boot/initrd.img-2.6.35-25-generic
 193.6GB: boot/vmlinuz-2.6.35-22-generic
 193.6GB: boot/vmlinuz-2.6.35-25-generic
 193.6GB: initrd.img
 193.6GB: initrd.img.old
 193.6GB: vmlinuz
 193.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 40 00 00 00 00 00  |........>.@.....|
00000020  42 74 3d 00 58 0f 00 00  00 00 00 00 02 00 00 00  |Bt=.X...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 e2 f2 05 f0 20  20 20 20 20 20 20 20 20  |..)....         |
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
00000100  7d 00 66 b8 b0 c6 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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

Unknown BootLoader  on sdb2

00000000  30 b5 eb c4 e7 b5 bb 2f  25 e7 69 1b 1f 0d d2 fc  |0....../%.i.....|
00000010  21 9f db c7 5a 45 b3 23  3f 4a c6 fb d2 de ff 42  |!...ZE.#?J.....B|
00000020  b5 d9 77 f5 bd 49 74 6c  49 bd 9a 58 6d f7 f0 96  |..w..ItlI..Xm...|
00000030  02 6d 7f 55 4d a1 2b 3e  f8 77 f0 7f 82 82 b8 f2  |.m.UM.+>.w......|
00000040  ff 3d ea 66 de 21 28 9c  09 2c 20 e5 3c af 1e ef  |.=.f.!(.., .<...|
00000050  13 6c f0 f8 27 45 e3 98  4a 2c 69 61 e3 03 c6 e1  |.l..'E..J,ia....|
00000060  bc b3 51 1a 40 3b ca e6  03 c1 d7 45 05 5a db 8b  |..Q.@;.....E.Z..|
00000070  73 6e e5 2c 65 52 57 e4  93 02 ac 0b 93 58 d1 76  |sn.,eRW......X.v|
00000080  58 5d bc 08 bf 20 1d 8f  33 74 3f a9 97 a7 94 65  |X]... ..3t?....e|
00000090  3b 66 a2 c6 69 34 c8 d3  11 68 50 91 df 04 75 e7  |;f..i4...hP...u.|
000000a0  21 ea 3e e2 40 ab 59 8c  75 1e bf 00 f9 b0 0e d2  |!.>.@.Y.u.......|
000000b0  e7 9f a1 1c de 6d 1c 35  e1 75 2b c3 08 16 49 26  |.....m.5.u+...I&|
000000c0  a8 56 32 b1 ef 84 bf e3  be 3e f4 1e bc 0c b8 cf  |.V2......>......|
000000d0  6c dd 36 4d e3 0a 33 95  64 0d 2f 54 95 1c 56 25  |l.6M..3.d./T..V%|
000000e0  78 31 00 3a 58 fc 04 8e  de 0f d8 01 dd dd 0e 7c  |x1.:X..........||
000000f0  56 db c0 65 02 88 9b 6c  3a 27 1c 05 1e 22 1d dd  |V..e...l:'..."..|
00000100  2e 96 00 ef 3b 97 dd b0  2f 9f 8a 7e 9c 62 6a e9  |....;.../..~.bj.|
00000110  0a 24 1b 36 43 cf 75 e5  e1 4b cf 02 ca fa 8a 91  |.$.6C.u..K......|
00000120  17 b3 8e cc 28 06 db 9b  6e 9e 81 06 9a ac ef 02  |....(...n.......|
00000130  8d a0 d9 72 2f ec 16 f8  3f 01 69 01 af 4a de 76  |...r/...?.i..J.v|
00000140  d6 ef 92 2b 52 86 44 36  38 89 05 70 ba 99 29 05  |...+R.D68..p..).|
00000150  b0 69 d3 a9 ed 29 f8 59  e7 a2 89 65 b1 f8 0f 09  |.i...).Y...e....|
00000160  27 ac b5 23 67 17 ec 16  9f 14 d4 86 a1 bc d9 a4  |'..#g...........|
00000170  a9 b0 74 33 a3 e6 25 19  50 39 10 88 4f ff d1 28  |..t3..%.P9..O..(|
00000180  8f 76 c2 da 45 d3 42 6a  29 4d 78 ff d7 ed 04 97  |.v..E.Bj)Mx.....|
00000190  4d 7c 2e de 17 17 25 98  f5 d3 34 a9 e5 eb fc 7d  |M|....%...4....}|
000001a0  46 2c f8 39 28 a7 21 03  08 10 e4 85 80 49 12 a7  |F,.9(.!......I..|
000001b0  34 6a 9e c9 50 11 25 27  20 27 d8 bb bf 2e 00 fe  |4j..P.%' '......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 5d 00 00 00  |............]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```
I'm happy for this great support, with Ubuntu you've got not only an enlightenment OS

but you inherited an enlightenment comunity too.

---

### Post by neonboy on 2011-02-22
comparing to my well working machine, i think that the proplem is within the last lines..

```
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 40 00 00 00 00 00  |........>.@.....|
00000020  42 74 3d 00 58 0f 00 00  00 00 00 00 02 00 00 00  |Bt=.X...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 e2 f2 05 f0 20  20 20 20 20 20 20 20 20  |..)....         |
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
00000100  7d 00 66 b8 b0 c6 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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

Unknown BootLoader  on sdb2

00000000  30 b5 eb c4 e7 b5 bb 2f  25 e7 69 1b 1f 0d d2 fc  |0....../%.i.....|
00000010  21 9f db c7 5a 45 b3 23  3f 4a c6 fb d2 de ff 42  |!...ZE.#?J.....B|
00000020  b5 d9 77 f5 bd 49 74 6c  49 bd 9a 58 6d f7 f0 96  |..w..ItlI..Xm...|
00000030  02 6d 7f 55 4d a1 2b 3e  f8 77 f0 7f 82 82 b8 f2  |.m.UM.+>.w......|
00000040  ff 3d ea 66 de 21 28 9c  09 2c 20 e5 3c af 1e ef  |.=.f.!(.., .<...|
00000050  13 6c f0 f8 27 45 e3 98  4a 2c 69 61 e3 03 c6 e1  |.l..'E..J,ia....|
00000060  bc b3 51 1a 40 3b ca e6  03 c1 d7 45 05 5a db 8b  |..Q.@;.....E.Z..|
00000070  73 6e e5 2c 65 52 57 e4  93 02 ac 0b 93 58 d1 76  |sn.,eRW......X.v|
00000080  58 5d bc 08 bf 20 1d 8f  33 74 3f a9 97 a7 94 65  |X]... ..3t?....e|
00000090  3b 66 a2 c6 69 34 c8 d3  11 68 50 91 df 04 75 e7  |;f..i4...hP...u.|
000000a0  21 ea 3e e2 40 ab 59 8c  75 1e bf 00 f9 b0 0e d2  |!.>.@.Y.u.......|
000000b0  e7 9f a1 1c de 6d 1c 35  e1 75 2b c3 08 16 49 26  |.....m.5.u+...I&|
000000c0  a8 56 32 b1 ef 84 bf e3  be 3e f4 1e bc 0c b8 cf  |.V2......>......|
000000d0  6c dd 36 4d e3 0a 33 95  64 0d 2f 54 95 1c 56 25  |l.6M..3.d./T..V%|
000000e0  78 31 00 3a 58 fc 04 8e  de 0f d8 01 dd dd 0e 7c  |x1.:X..........||
000000f0  56 db c0 65 02 88 9b 6c  3a 27 1c 05 1e 22 1d dd  |V..e...l:'..."..|
00000100  2e 96 00 ef 3b 97 dd b0  2f 9f 8a 7e 9c 62 6a e9  |....;.../..~.bj.|
00000110  0a 24 1b 36 43 cf 75 e5  e1 4b cf 02 ca fa 8a 91  |.$.6C.u..K......|
00000120  17 b3 8e cc 28 06 db 9b  6e 9e 81 06 9a ac ef 02  |....(...n.......|
00000130  8d a0 d9 72 2f ec 16 f8  3f 01 69 01 af 4a de 76  |...r/...?.i..J.v|
00000140  d6 ef 92 2b 52 86 44 36  38 89 05 70 ba 99 29 05  |...+R.D68..p..).|
00000150  b0 69 d3 a9 ed 29 f8 59  e7 a2 89 65 b1 f8 0f 09  |.i...).Y...e....|
00000160  27 ac b5 23 67 17 ec 16  9f 14 d4 86 a1 bc d9 a4  |'..#g...........|
00000170  a9 b0 74 33 a3 e6 25 19  50 39 10 88 4f ff d1 28  |..t3..%.P9..O..(|
00000180  8f 76 c2 da 45 d3 42 6a  29 4d 78 ff d7 ed 04 97  |.v..E.Bj)Mx.....|
00000190  4d 7c 2e de 17 17 25 98  f5 d3 34 a9 e5 eb fc 7d  |M|....%...4....}|
000001a0  46 2c f8 39 28 a7 21 03  08 10 e4 85 80 49 12 a7  |F,.9(.!......I..|
000001b0  34 6a 9e c9 50 11 25 27  20 27 d8 bb bf 2e 00 fe  |4j..P.%' '......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 5d 00 00 00  |............]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by Quackers on 2011-02-22
I don't see anything wrong with grub.
The unknown bootloader messages are normal. One is for a usb flash drive and the other is normally displayed for an extended partition.
I would recommend that you have a look at section 8 of this guide by drs305 with regard to theming. It seems that the version of grub used has a bearing on how grub splash images/themes are used.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by neonboy on 2011-02-22
Cool, I went for the purge&reinstall from live usb solution and everything went fine..

Thanks to you all, if you'll ever come to Milan,IT I'll owe you a beer :D

---

### Post by Rubi1200 on 2011-02-22
Excellent! Glad you got things sorted out in the end.

And, who knows, we may take you up on that offer of a beer some day :)

---

