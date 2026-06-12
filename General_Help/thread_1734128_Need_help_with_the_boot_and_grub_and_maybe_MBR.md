---
title: "Need help with the boot and grub and maybe MBR"
date: 2011-04-19
forum: General Help
---

### Post by Kharlo on 2011-04-19
Hhi everybody

i just want to organize the boot of my laptop since windows has messed it up. now my laptop is stable and i want to change to grub1, i already did it, because i fell it more robust than grub2, (my windows 7 screwed up the grub 2 in a crash, i dont know why if it was not a win7 reinstall)
but i have some questions and doubts

1-the puppy linux 525, which grub come with that distro? is that the original grub legacy?

2-i have win7 ubuntu 10.04 an dpuppy linux, i want grub 1 where should be installed? in the puppy partition?

3- i see that even a empty partition of the hard disk has a "boot" directory, where the boot should really be?

---

### Post by oldfred on 2011-04-20
Windows creates a 100MB hidden in windows boot/recovery partition. Do not use that for anything else as that is how windows boots.

Some programs with DRM in win7 have interfered with grub2. But with grub legacy you are going to have to manage your menu entries yourself. I used to chain load all my grub entries as that was the easiest for me. You only have one boot with grub and install all others to the partition boot sector and chain to that. I actually converted to a grub only partition with entries to chain boot any partition with an install.

I like grub2 and thinks it works with a lot more newer things and makes setting up dual boot very easy. Some old grub legacies do not work with ext4. Ubuntu updated theirs with 9.04. Each distribution makes minor tweaks for its use, but then may not work to boot another.

---

### Post by Kharlo on 2011-04-20
Thank you oldfred for your answer.

currently, i have the grub that came wit puppy535 (thats why i asked what grub is that since i dont know if that is a normal or genuine grub legacym, since many things in puppy has been change or modified....)

that grub works fine with windows7 aand the puppy, bu tnot with the ubuntu 10, it says error15: file not found, i check the menu.lst and everything seems ok, the ubuntu 10 is on sda5 and it is correctly allocated on menu.lst but still cant boot.

i have more questions ahead but i want to first solve this one since i see that if i post many question in the same copst users tend to go away...

so for now thats what i need to make ubuntu 10 to work 

what you recommend me?  do you want to see my menu.lst?

---

### Post by oldfred on 2011-04-20
Did you use ext4 for Ubuntu? Ubuntu can use old grub legacy also if you really want.

Post this to see entire configuration. It should work from Puppy but I have not tried it. If issues in Puppy use liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Kharlo on 2011-04-20
Please be gently with me.. im a kid using linux for first time... i have  a year using linux but just using it, since i havent had any problem  with it, i have no experience....:confused::wink:

i have ubuntu on ext4 partition.
about the other you says
ok, let me try to understand, you want me to run the app in the link  above to gather informaition abouth my boot? i mean i see you post info  about it but not what you want me to do with it. (sorry, my bad english)

if that, give me a minutes im doing that

---

### Post by Kharlo on 2011-04-20
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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
    Boot sector type:  Unknown
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: can't find /dev/sda1 in /etc/fstab
mount: can't find /dev/sda2 in /etc/fstab
mount: can't find /dev/sda3 in /etc/fstab
mount: /dev/sda7 already mounted or sda7 busy

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   132,102,143   131,895,296   7 HPFS/NTFS
/dev/sda3         132,102,144   143,794,175    11,692,032   7 HPFS/NTFS
/dev/sda4         143,797,876   156,296,384    12,498,509   5 Extended
/dev/sda5         143,797,878   152,199,809     8,401,932  83 Linux
/dev/sda6         152,199,873   154,288,259     2,088,387  82 Linux swap / Solaris
/dev/sda7         154,292,224   156,295,167     2,002,944  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 260 MB, 260046848 bytes
16 heads, 32 sectors/track, 992 cylinders, total 507904 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32       507,903       507,872   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6A16E18A16E15799                       ntfs       Reservado para el sistema     
/dev/sda2        D096EC7B96EC6386                       ntfs       hp1                           
/dev/sda3        18A0F8BBA0F8A084                       ntfs       hp2                           
/dev/sda5        7103403b-6b65-4848-9664-5623fd547dcf   ext4                                     
/dev/sda6                                               swap                                     
/dev/sda7        f1c975a8-b783-4d56-9d9e-032694cef674   ext3                                     
/dev/sdb1        94F7-B786                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/root        /                        ext3       (rw,relatime,errors=continue,data=ordered)
/dev/sdb1        /mnt/sdb1                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,quiet,errors=remount-ro)


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
set default="6"
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
search --no-floppy --fs-uuid --set 7103403b-6b65-4848-9664-5623fd547dcf
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
search --no-floppy --fs-uuid --set 7103403b-6b65-4848-9664-5623fd547dcf
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=01
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7103403b-6b65-4848-9664-5623fd547dcf
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=7103403b-6b65-4848-9664-5623fd547dcf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7103403b-6b65-4848-9664-5623fd547dcf
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=7103403b-6b65-4848-9664-5623fd547dcf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7103403b-6b65-4848-9664-5623fd547dcf
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7103403b-6b65-4848-9664-5623fd547dcf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7103403b-6b65-4848-9664-5623fd547dcf
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7103403b-6b65-4848-9664-5623fd547dcf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7103403b-6b65-4848-9664-5623fd547dcf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7103403b-6b65-4848-9664-5623fd547dcf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=7103403b-6b65-4848-9664-5623fd547dcf /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  76.0GB: boot/grub/core.img
  75.6GB: boot/grub/grub.cfg
  76.2GB: boot/initrd.img-2.6.32-21-generic
  76.8GB: boot/initrd.img-2.6.32-26-generic
  75.5GB: boot/vmlinuz-2.6.32-21-generic
  76.4GB: boot/vmlinuz-2.6.32-26-generic
  76.8GB: initrd.img
  76.2GB: initrd.img.old
  76.4GB: vmlinuz
  75.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  27 1b d8 e4 26 1a d9 e5  1e 22 e1 dd 43 7f bc 80  |'...&...."..C...|
00000010  34 08 cb f7 c5 f9 3a 06  3c 00 c3 ff 54 68 ab 97  |4.....:.<...Th..|
00000020  fa c6 05 39 bf 83 40 7c  94 a8 6b 57 c5 f9 3a 06  |...9..@|..kW..:.|
00000030  2f 13 d0 ec 56 6a a9 95  c4 f8 3b 07 cc f0 33 0f  |/...Vj....;...3.|
00000040  56 6a a9 95 f5 c9 0a 36  eb d7 14 28 e1 dd 1e 22  |Vj.....6...(..."|
00000050  aa 96 55 69 08 34 f7 cb  3b 07 c4 f8 f9 c5 06 3a  |..Ui.4..;......:|
00000060  fd c1 02 3e b2 8e 4d 71  a8 94 57 6b 06 3a f9 c5  |...>..Mq..Wk.:..|
00000070  8e b2 71 4d a7 9b 58 64  4e 72 b1 8d 68 54 97 ab  |..qM..XdNr..hT..|
00000080  9f a3 60 5c 07 3b f8 c4  cf f3 30 0c b4 88 4b 77  |..`\.;....0...Kw|
00000090  bf 83 40 7c 61 5d 9e a2  f7 cb 08 34 cb f7 34 08  |..@|a].....4..4.|
000000a0  56 6a a9 95 10 2c ef d3  6a 56 95 a9 c7 fb 38 04  |Vj...,..jV....8.|
000000b0  60 5c 9f a3 bd 81 42 7e  aa 96 55 69 06 3a f9 c5  |`\....B~..Ui.:..|
000000c0  aa 96 55 69 76 4a 89 b5  f2 ce 0d 31 5d 61 a2 9e  |..UivJ.....1]a..|
000000d0  3d 01 c2 fe 15 29 ea d6  d8 e4 27 1b 6b 57 94 a8  |=....)....'.kW..|
000000e0  1d 21 e2 de e8 d4 17 2b  38 04 c7 fb 93 af 6c 50  |.!.....+8.....lP|
000000f0  bb 87 44 78 8b b7 74 48  42 7e bd 81 46 7a b9 85  |..Dx..tHB~..Fz..|
00000100  7f 43 80 bc 6d 51 92 ae  f8 c4 07 3b 4a 76 b5 89  |.C..mQ.....;Jv..|
00000110  f7 cb 08 34 13 2f ec d0  12 2e ed d1 60 5c 9f a3  |...4./......`\..|
00000120  ea d6 15 29 22 1e dd e1  64 58 9b a7 13 2f ec d0  |...)"...dX.../..|
00000130  3a 06 c5 f9 49 75 b6 8a  9c a0 63 5f b2 8e 4d 71  |:...Iu....c_..Mq|
00000140  c6 fa 39 05 de e2 21 1d  f1 cd 0e 32 3a 06 c5 f9  |..9...!....2:...|
00000150  e5 d9 1a 26 94 a8 6b 57  3d 01 c2 fe 7e 42 81 bd  |...&..kW=...~B..|
00000160  b5 89 4a 76 1f 23 e0 dc  54 68 ab 97 ee d2 11 2d  |..Jv.#..Th.....-|
00000170  c5 f9 3a 06 0c 30 f3 cf  ca f6 35 09 f1 cd 0e 32  |..:..0....5....2|
00000180  87 bb 78 44 e1 dd 1e 22  61 5d 9e a2 ba 86 45 79  |..xD..."a]....Ey|
00000190  de e2 21 1d 92 ae 6d 51  6d 51 92 ae 02 3e fd c1  |..!...mQmQ...>..|
000001a0  56 6a a9 95 ab 97 54 68  52 6e ad 91 88 b4 77 4b  |Vj....ThRn....wK|
000001b0  4f 73 b0 8c d8 e4 27 1b  4a 76 b5 89 90 ac 00 ef  |Os....'.Jv......|
000001c0  ff ff 83 ef ff ff 02 00  00 00 0c 34 80 00 00 ef  |...........4....|
000001d0  ff ff 05 ef ff ff 0e 34  80 00 02 de 1f 00 00 00  |.......4........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda6

00000000  4c 37 b3 c8 2b 50 d4 af  19 62 e6 9d bf c4 40 3b  |L7..+P...b....@;|
00000010  f0 8b 0f 74 9b e0 64 1f  dc a7 23 58 cc b7 33 48  |...t..d...#X..3H|
00000020  f1 8a 0e 75 db a0 24 5f  81 fa 7e 05 04 7f fb 80  |...u..$_..~.....|
00000030  00 7b ff 84 e4 9f 1b 60  99 e2 66 1d c3 b8 3c 47  |.{.....`..f...<G|
00000040  42 39 bd c6 98 e3 67 1c  c1 ba 3e 45 c4 bf 3b 40  |B9....g...>E..;@|
00000050  05 7e fa 81 49 32 b6 cd  c1 ba 3e 45 1b 60 e4 9f  |.~..I2....>E.`..|
00000060  1e 65 e1 9a a9 d2 56 2d  03 78 fc 87 88 f3 77 0c  |.e....V-.x....w.|
00000070  26 5d d9 a2 84 ff 7b 00  1e 65 e1 9a c6 bd 39 42  |&]....{..e....9B|
00000080  0e 75 f1 8a 54 2f ab d0  70 0b 8f f4 bd c6 42 39  |.u..T/..p.....B9|
00000090  6d 16 92 e9 a0 db 5f 24  e8 93 17 6c ac d7 53 28  |m....._$...l..S(|
000000a0  76 0d 89 f2 09 72 f6 8d  b8 c3 47 3c 53 28 ac d7  |v....r....G<S(..|
000000b0  8f f4 70 0b 5c 27 a3 d8  40 3b bf c4 86 fd 79 02  |..p.\'..@;....y.|
000000c0  ab d0 54 2f 67 1c 98 e3  4d 36 b2 c9 7d 06 82 f9  |..T/g...M6..}...|
000000d0  01 7a fe 85 87 fc 78 03  a8 d3 57 2c 46 3d b9 c2  |.z....x...W,F=..|
000000e0  53 28 ac d7 d3 a8 2c 57  c4 bf 3b 40 b6 cd 49 32  |S(....,W..;@..I2|
000000f0  54 2f ab d0 c4 bf 3b 40  37 4c c8 b3 98 e3 67 1c  |T/....;@7L....g.|
00000100  43 38 bc c7 ec 97 13 68  56 2d a9 d2 9c e7 63 18  |C8.....hV-....c.|
00000110  29 52 d6 ad ff 84 00 7b  d8 a3 27 5c 46 3d b9 c2  |)R.....{..'\F=..|
00000120  df a4 20 5b a4 df 5b 20  6f 14 90 eb 38 43 c7 bc  |.. [..[ o...8C..|
00000130  8a f1 75 0e 55 2e aa d1  3f 44 c0 bb ef 94 10 6b  |..u.U...?D.....k|
00000140  28 53 d7 ac bb c0 44 3f  f5 8e 0a 71 77 0c 88 f3  |(S....D?...qw...|
00000150  f2 89 0d 76 63 18 9c e7  d6 ad 29 52 07 7c f8 83  |...vc.....)R.|..|
00000160  1c 67 e3 98 c0 bb 3f 44  15 6e ea 91 0e 75 f1 8a  |.g....?D.n...u..|
00000170  9b e0 64 1f 9a e1 65 1e  f0 8b 0f 74 44 3f bb c0  |..d...e....tD?..|
00000180  7c 07 83 f8 7c 07 83 f8  f0 8b 0f 74 99 e2 66 1d  ||...|......t..f.|
00000190  7a 01 85 fe 58 23 a7 dc  6c 17 93 e8 1d 66 e2 99  |z...X#..l....f..|
000001a0  2c 57 d3 a8 1e 65 e1 9a  4e 35 b1 ca f3 88 0c 77  |,W...e..N5.....w|
000001b0  50 2b af d4 40 3b bf c4  3e 45 c1 ba 3e 45 c1 ba  |P+..@;..>E..>E..|
000001c0  01 7a fe 85 35 4e ca b1  f9 82 06 7d 2b 50 d4 af  |.z..5N.....}+P..|
000001d0  de a5 21 5a 3d 46 c2 b9  70 0b 8f f4 99 e2 66 1d  |..!Z=F..p.....f.|
000001e0  61 1a 9e e5 3e 45 c1 ba  f6 8d 09 72 13 68 ec 97  |a...>E.....r.h..|
000001f0  09 72 f6 8d de a5 21 5a  61 1a 9e e5 aa d1 55 2e  |.r....!Za.....U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

hda hdb hdc hdd sdc sdd sde sdf sdg sdh sdi 

```

---

### Post by oldfred on 2011-04-20
Do you have Puppy installed in sda7. It seems to have some corruption and the script cannot mount it. Does it boot?

If issues with sda7 run this from liveCD.

From liveCD so everything is unmounted,swap off if necessary, change sda7 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda7
if errors:
sudo e2fsck -f -y -v /dev/sda7

---

### Post by Kharlo on 2011-04-20
sorry for the delay oldfred

yes i have Puppy installed in sda7

and yes, it boot and works(the Puppy) fine and the windows too.

---

### Post by oldfred on 2011-04-20
Script was not able to see the Puppy partition, but that may be something unique about Puppy. I do not know if Puppy's grub would boot Ubuntu anyway since Ubuntu is ext4. 

I suggest installing Ubuntu's grub. If you do not want grub2 you have to chroot into your Ubuntu install and uninstall grub & grub2 and reinstall just grub legacy.

I think these instructions are to uninstall both but reinstall grub2.
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Your install is in sda5 so the example has the correct XY drive & partition examples.

Do all the steps except change this:
In step 4 instead of this (grub-pc is grub2):
apt-get install grub-common grub-pc
do this:
[COLOR=DarkRed]apt-get install grub-common grub

[COLOR=Black]After getting Ubuntu working we will probably have to manually update its menu.lst to boot Puppy.[/COLOR]
[/COLOR]

---

### Post by Kharlo on 2011-04-20
Ok
Thank you a lot for your answer oldfred
you answer me MANY question that i didnt evenr remember:
like;
is puppy's grub compatible with ext4?
> I do not know if Puppy's grub would boot  Ubuntu anyway since Ubuntu is ext4. 

if so, which grub should i install puppy's grubor ubuntu's grub?
> I suggest installing Ubuntu's grub. 
can i have grub legacy in ubuntu?
> If you do not want grub2 you have to  chroot into your Ubuntu install and uninstall grub & grub2 and  reinstall just grub legacy.

where do i install it?
>  Your install is in sda5 so the example has the correct XY drive & partition examples.
[COLOR=DarkRed][COLOR=Black]
THANK YOU!

[/COLOR][/COLOR]
i'll be trying to do that..
i'll let you know the results

thanks!

---

### Post by Kharlo on 2011-04-20
mmm..
need little help

here, in:
**[COLOR=Navy]1. Chroot into your real system.[/COLOR]** T............
.............
............

**[COLOR=DarkRed]Mounting Instructions:[/COLOR]**
.................
.................
...............

[LIST=A]
[*]**[COLOR=DarkRed]Only If You Have a Separate /boot partition.[/COLOR]** 
[*]**[COLOR=DarkRed]Only If You Are Running WUBI (Ubuntu inside Windows)[/COLOR]** 
[*]**[COLOR=DarkRed]If You Have a Normal Installation.[/COLOR]**
[/LIST]

which one is my case?

i mean, i dont undertand very clear what is the meaning....

example, is i have a separate boot partition, what is the meaning? a oot partition in another hard disk drive? or a boot partition in a disk partition only used for boot (is not that the MBR?) or a boot partition that is not in the OS that belongs....


which one is my case?

---

### Post by Kharlo on 2011-04-20
Hi

Sorry oldfred

but this did not work:
> 
Do all the steps except change this:
In step 4 instead of this (grub-pc is grub2):
apt-get install grub-common grub-pc
do this:
**[COLOR=DarkRed]apt-get install grub-common grub[/COLOR]**

it says:

```
eading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  grub-legacy-doc mdadm multiboot-doc grub-emu
The following NEW packages will be installed:
  grub grub-common
0 upgraded, 2 newly installed, 0 to remove and 354 not upgraded.
Need to get 1,911kB of archives.
After this operation, 5,267kB of additional disk space will be used.
Err http://do.archive.ubuntu.com/ubuntu/ lucid-updates/main grub-common 1.98-1ubuntu10
  Could not resolve 'do.archive.ubuntu.com'
Err http://do.archive.ubuntu.com/ubuntu/ lucid/main grub 0.97-29ubuntu60
  Could not resolve 'do.archive.ubuntu.com'
Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.98-1ubuntu10_i386.deb  Could not resolve 'do.archive.ubuntu.com'
Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu60_i386.deb  Could not resolve 'do.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntu:/# 


```

so for a while im without grub:???:.. ?

---

### Post by oldfred on 2011-04-20
The /boot is normally just one of the folders inside your standard / (root). Servers and very old computers with a 137GB boot limit may need a separate /boot partition. You do not have wubi which is an install inside the standard NTFS windows partition for testing. For most desktops all folders should just be in root which yours is.

Did the chroot work without error? If it did not load all the mounts it may  not see everything it needs. 

is this your standard download location?
do.archive.ubuntu.com

Post this inside code tags since it will be long.
If in chroot this should work:
fred@fred-MavericDT:~$ sudo cp /etc/apt/sources.list ~/sources.list.backup
[sudo] password for fred: 
fred@fred-MavericDT:~$ nano ~/sources.list.backup

May be different location if just in liveCD.

---

### Post by Kharlo on 2011-04-20
> **oldfred said:**
> The /boot is normally just one of the folders inside your standard / (root). Servers and very old computers with a 137GB boot limit may need a separate /boot partition. You do not have wubi which is an install inside the standard NTFS windows partition for testing. For most desktops all folders should just be in root which yours is.
so the "C" option is the one for me (**[COLOR=DarkRed]If You Have a Normal Installation.[/COLOR]** )

> **oldfred said:**
> Did the chroot work without error? If it did not load all the mounts it may  not see everything it needs. 
if it changed from "ubuntu@ubuntu:~$"  to  "root@ubuntu:/#"?
yes

> **oldfred said:**
> is this your standard download location?
do.archive.ubuntu.com
dont understand
by the "do" words in the front, are you asking me if im in that location/country? "do"?


> **oldfred said:**
> Post this inside code tags since it will be long.
If in chroot this should work:
fred@fred-MavericDT:~$ sudo cp /etc/apt/sources.list ~/sources.list.backup
[sudo] password for fred: 
fred@fred-MavericDT:~$ nano ~/sources.list.backup

May be different location if just in liveCD.
???:confused:

---

### Post by oldfred on 2011-04-20
do is just a name for a server where ever you are at. I assume it is correct. I just wanted to see if all your settings were that. Slim possibility that your server was down temporarily. 

Were you connected with a Ethernet cable as you have to be on line for the download to work. (step #2)?

---

### Post by Kharlo on 2011-04-20
so, do i try again, from the begining?

mm.. just you to know, afther the update finished, i accidentally unplug the lan wire.. maybe the whole proceses or at least from the first attempt to internet it requieres to be connected until finish all the steps?

the lan wire im using for doing that is the same im using to write you in this foorum (in other laptop)

and..
since im installing grub legacy and you told me grub-pc is grub2

**instead:**
apt-get install grub-common grub-pc

**is:**
apt-get install grub-common grub
**or**
apt-get install grub-common

---

### Post by oldfred on 2011-04-20
It is both common and grub. Package names in Ubuntu do not always match the names we use.

apt-get install grub-common grub

It seemed like it did not connect.

Is your liveCD the same version Lucid 10.04? In system, Administration, Software Sources (I forget exact configure) check what liveCD has as the source for Ubuntu downloads. 
In 10.10 they have moved the software sources to a Settings button on Update Manager and it may also be there. That shows download from: and a combo box to choose where in the world to download updates from. It usually defaults to something local, but has a other option that will search for 'best' server to download from. If something is better then you change to that and it updates the sources.list. But I do not know how to do that from command line. Just confirm that you can down load grub from liveCd.

Sometimes when chroot and having mounted something, it may not work or work correctly if still active. Often best to start all over.

---

### Post by Kharlo on 2011-04-20
> **oldfred said:**
> It is both common and grub. Package names in Ubuntu do not always match the names we use.

apt-get install grub-common grub

ok
> 
It seemed like it did not connect.

Is your liveCD the same version Lucid 10.04? 
yes

> In system, Administration, Software Sources (I forget exact configure) check what liveCD has as the source for Ubuntu downloads. 
im lost
i cannt find "ubuntu downloads"
do you mean "ubuntu updates" below the "ubsates" tab?

> 
In 10.10 they have moved the software sources to a Settings button on Update Manager and it may also be there. That shows download from: and a combo box to choose where in the world to download updates from. It usually defaults to something local, but has a other option that will search for 'best' server to download from. If something is better then you change to that and it updates the sources.list. But I do not know how to do that from command line. **Just confirm that you can down load grub from liveCd.**


there is an option that says: download from: Main servers. servers for united states and others...
Also 
and
> **Just confirm that you can down load grub from liveCd.**
there is a tab named "other software"
with an option "add CD-ROM"
could that be the key?

---

### Post by oldfred on 2011-04-20
It is the 'other', that then shows the servers that are available, something over 300 worldwide.

I am not sure but there may be a way to use CD, but again I do not know how from chroot command line. 

I will be off line for a couple of hours.

---

### Post by Kharlo on 2011-04-20
ok

---

### Post by Kharlo on 2011-04-20
ok, now everything worked fine, no error mensages, but when i reboot, when i tried to enter to ubuntu 10, i got the same
"error 15: file not found"

---

### Post by Kharlo on 2011-04-20
exploring the options i found something called: "grub4dos" in puppy linux 525, i installed it and everything is working now!

i only have one issue now, i notice that the grub4dos saved the menu.lst and the stage1.5 (not sure) in the 100mb partition that windows use to boot, everything seems to work ok even the ubuntu 10.04, someone told me not to bother the 100mb partition of windows.. what you think

---

### Post by oldfred on 2011-04-20
You really should not have any grub in the windows partition, but if it is working for now, I would not change it.

Please post the boot script again. Best if from Ubuntu. I would like to see where things are installed and what menu.lst says.

---

### Post by Kharlo on 2011-04-22
> **oldfred said:**
> You really should not have any grub in the windows partition, but if it is working for now, I would not change it.

Please post the boot script again. Best if from Ubuntu. I would like to see where things are installed and what menu.lst says.

Hi olfred!

sorry for my delayed answer..

im really with you. i dont like that idea and curiously afther installing the grub4dos, 

(i tryed before to install it in the puppy partition but that software keep lelling me that not, that must be installed in the MBR, despite which OS are installed or managing that section...  now i think i understand why is that, and I THINK is because the grub4dos its like a type of grub plus supergrubdisk.. all in one pachagebecause if there is a problem with some of the partitions it geves you options even to enter command lines.. i dotn knwo just an idea..)

curiosly (and thats why i didnt reply you at time), after installing grub4dos i start to have some random problems in my windows, the ybernation didnt work, i solved it, then the suspend mode was unavailable.. bu ti solve it. i didnt like the xtrange behavior of the windows and i decide to use windows repair disk to turn back the 100mb boot partition and MBR at its original state...  after doing that, then i came back to here to read you and to follow the steps again, and i did what the pae you gave me says:
> [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
[SIZE=4][COLOR=DarkRed]**HOWTO: Purge and Reinstall Grub 2 from the Live CD**[/COLOR][/SIZE]

but i had no option i installed the grub 2, so i discard the to have grub legacy on ubuntu.

now everything seems to work pretty good.

and i want to give a very sincere **thank you** for your help, time and dedication to y problem.

---

### Post by oldfred on 2011-04-22
Glad you got it working.

My understanding of grub4dos is that it is just another version of grub for dos partitions. But I use grub2 for booting ISO in FAT32 partitions, so I have not followed the details of the differences of grub4dos.

---

