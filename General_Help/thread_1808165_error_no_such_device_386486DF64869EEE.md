---
title: "error: no such device: 386486DF64869EEE"
date: 2011-07-20
forum: General Help
---

### Post by DugMatt77 on 2011-07-20
I restored my Windows Vista back to factory settings and then tried installing ubuntu 11.04 (i think) from my pen drive. Although I can run ubuntu, I am now unable to boot windows due to the recurring message of error: no such device: 386486DF64869EEE. 
Help Please!
THANKS

---

### Post by Quackers on 2011-07-20
Welcome to UF :-)
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by DugMatt77 on 2011-07-20
```

```matty@MasterShifu:~$ cd downloads/boot_info_script060
bash: cd: downloads/boot_info_script060: No such file or directory
matty@MasterShifu:~$ sudo bash boot_info_script.sh
[sudo] password for matty: 
bash: boot_info_script.sh: No such file or directory
matty@MasterShifu:~$ sudo bash boot_info_script060.sh
bash: boot_info_script060.sh: No such file or directory
matty@MasterShifu:~$ sudo bash boot_info_script060
bash: boot_info_script060: No such file or directory
matty@MasterShifu:~$ cd Downloads/boot_info_script060
matty@MasterShifu:~/Downloads/boot_info_script060$ ^C
matty@MasterShifu:~/Downloads/boot_info_script060$ 

This is the only message I get. I followed the link to the website and downloaded the folder/files boot_info_script060 to my downloads folder and unzipped there. Then I entered the command and the above is what it comes back with. 

Sorry I'm not too flash with computers. It was more like the older sibling experimental project on the younger siblings laptop gone wrong. To make it worse, he now lives on the other side of the world! 

I look forward to more help! :D

---

### Post by Quackers on 2011-07-20
Downloads has a capital D, that's important in Linux :wink:

---

### Post by DugMatt77 on 2011-07-20
Sorry, scratch that CODE for the last post. I got 

```

```matty@MasterShifu:~$ sudo bash ~/Desktop/boot_info_script060
[sudo] password for matty: 
/home/matty/Desktop/boot_info_script060: /home/matty/Desktop/boot_info_script060: is a directory
matty@MasterShifu:~$

---

### Post by DugMatt77 on 2011-07-20
Sorry kinda misread your message a little bit. Downloaded to Downloads folder and typed in the cd message. Came back with the following:


```

```matty@MasterShifu:~$ cd Downloads/boot_info_script060
matty@MasterShifu:~/Downloads/boot_info_script060$

---

### Post by Quackers on 2011-07-20
That's good :-)
Now type ```
sudo bash boot_info_script.sh
```

---

### Post by DugMatt77 on 2011-07-20
Ah nice indeed.. I think

```

```matty@MasterShifu:~$ cd Downloads/boot_info_script060
matty@MasterShifu:~/Downloads/boot_info_script060$ sudo bash boot_info_script.sh[sudo] password for matty: 

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/matty/Downloads/boot_info_script060/".

matty@MasterShifu:~/Downloads/boot_info_script060$

---

### Post by DugMatt77 on 2011-07-20
```

```                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2             129,024    21,100,543    20,971,520   7 NTFS / exFAT / HPFS
/dev/sda3    *     21,100,544   118,809,530    97,708,987   7 NTFS / exFAT / HPFS
/dev/sda4         118,810,622   312,578,047   193,767,426   f W95 Extended (LBA)
/dev/sda5         307,337,216   312,578,047     5,240,832  dd Dell Media Direct
/dev/sda6         118,810,624   303,163,391   184,352,768  83 Linux
/dev/sda7         303,165,440   307,322,879     4,157,440  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D8-0114                              vfat       DellUtility
/dev/sda2        CA5A087C5A086811                       ntfs       RECOVERY
/dev/sda3        BC768AF2768AAD28                       ntfs       OS
/dev/sda5        7A11-8E76                              vfat       MEDIADIRECT
/dev/sda6        196e2061-c091-4e5c-80a1-0ede86e5d00b   ext4       
/dev/sda7        acd66b50-176b-44dc-a8fd-c498e69a209d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda5/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768 
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 196e2061-c091-4e5c-80a1-0ede86e5d00b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 196e2061-c091-4e5c-80a1-0ede86e5d00b
set locale_dir=($root)/boot/grub/locale
set lang=en_NZ
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 196e2061-c091-4e5c-80a1-0ede86e5d00b
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=196e2061-c091-4e5c-80a1-0ede86e5d00b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 196e2061-c091-4e5c-80a1-0ede86e5d00b
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=196e2061-c091-4e5c-80a1-0ede86e5d00b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 196e2061-c091-4e5c-80a1-0ede86e5d00b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 196e2061-c091-4e5c-80a1-0ede86e5d00b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 386486DF64869EEE
    chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 7a11-8e76
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=196e2061-c091-4e5c-80a1-0ede86e5d00b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=acd66b50-176b-44dc-a8fd-c498e69a209d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 120.793052673 = 129.700552704  boot/grub/core.img                             1
 132.802124023 = 142.595194880  boot/grub/grub.cfg                             1
 105.001464844 = 112.744464384  boot/initrd.img-2.6.38-8-generic               2
 120.791324615 = 129.698697216  boot/vmlinuz-2.6.38-8-generic                  1
 105.001464844 = 112.744464384  initrd.img                                     2
 120.791324615 = 129.698697216  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  f0 83 e6 1f 6b f6 28 8b  0b 0f b6 4c 31 04 83 e1  |....k.(....L1...|
00000010  01 74 bf 50 e8 30 f4 ff  ff 59 89 7d fc 8b 03 f6  |.t.P.0...Y.}....|
00000020  44 30 04 01 74 0e ff 75  08 e8 d3 fe ff ff 59 89  |D0..t..u......Y.|
00000030  45 e4 eb 0f e8 47 9f ff  ff c7 00 09 00 00 00 83  |E....G..........|
00000040  4d e4 ff c7 45 fc fe ff  ff ff e8 09 00 00 00 8b  |M...E...........|
00000050  45 e4 e8 6a 8f ff ff c3  ff 75 08 e8 89 f4 ff ff  |E..j.....u......|
00000060  59 c3 56 8b 74 24 08 8b  46 0c a8 83 74 1e a8 08  |Y.V.t$..F...t...|
00000070  74 1a ff 76 08 e8 af 83  ff ff 81 66 0c f7 fb ff  |t..v.......f....|
00000080  ff 33 c0 59 89 06 89 46  08 89 46 04 5e c3 cc cc  |.3.Y...F..F.^...|
00000090  8b 44 24 08 8b 4c 24 10  0b c8 8b 4c 24 0c 75 09  |.D$..L$....L$.u.|
000000a0  8b 44 24 04 f7 e1 c2 10  00 53 f7 e1 8b d8 8b 44  |.D$......S.....D|
000000b0  24 08 f7 64 24 14 03 d8  8b 44 24 08 f7 e1 03 d3  |$..d$....D$.....|
000000c0  5b c2 10 00 cc cc cc cc  cc cc cc cc cc cc cc cc  |[...............|
000000d0  8d 42 ff 5b c3 8d a4 24  00 00 00 00 8d 64 24 00  |.B.[...$.....d$.|
000000e0  33 c0 8a 44 24 08 53 8b  d8 c1 e0 08 8b 54 24 08  |3..D$.S......T$.|
000000f0  f7 c2 03 00 00 00 74 15  8a 0a 83 c2 01 3a cb 74  |......t......:.t|
00000100  cf 84 c9 74 51 f7 c2 03  00 00 00 75 eb 0b d8 57  |...tQ......u...W|
00000110  8b c3 c1 e3 10 56 0b d8  8b 0a bf ff fe fe 7e 8b  |.....V........~.|
00000120  c1 8b f7 33 cb 03 f0 03  f9 83 f1 ff 83 f0 ff 33  |...3...........3|
00000130  cf 33 c6 83 c2 04 81 e1  00 01 01 81 75 1c 25 00  |.3..........u.%.|
00000140  01 01 81 74 d3 25 00 01  01 01 75 08 81 e6 00 00  |...t.%....u.....|
00000150  00 80 75 c4 5e 5f 5b 33  c0 c3 8b 42 fc 3a c3 74  |..u.^_[3...B.:.t|
00000160  36 84 c0 74 ef 3a e3 74  27 84 e4 74 e7 c1 e8 10  |6..t.:.t'..t....|
00000170  3a c3 74 15 84 c0 74 dc  3a e3 74 06 84 e4 74 d4  |:.t...t.:.t...t.|
00000180  eb 96 5e 5f 8d 42 ff 5b  c3 8d 42 fe 5e 5f 5b c3  |..^_.B.[..B.^_[.|
00000190  8d 42 fd 5e 5f 5b c3 8d  42 fc 5e 5f 5b c3 ff 25  |.B.^_[..B.^_[..%|
000001a0  7c 10 40 00 cc cc cc cc  fe ff ff ff 00 00 00 00  ||.@.............|
000001b0  d4 ff ff ff 00 00 00 00  fe ff ff ff f4 5c 00 fe  |.............\..|
000001c0  ff ff dd fe ff ff 02 b0  3c 0b 00 f8 4f 00 00 fe  |........<...O...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 00 fd 0a 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda5

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 22 18  |.X.MSDOS5.0...".|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 98 51 12  |........?.....Q.|
00000020  00 f8 4f 00 ef 13 00 00  00 00 00 00 02 00 00 00  |..O.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 76 8e 11 7a 44  65 6c 6c 4d 44 33 70 6c  |..)v..zDellMD3pl|
00000050  61 79 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |ayFAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


Hmm

---

### Post by Quackers on 2011-07-20
Ok. Close the terminal. Open your home folder and look for a Results.txt file. From the output it could have gone in Downloads/boot_info_script060 folder, maybe.
Open the Results.txt file and copy ALL of its contents then click on New Reply and then click on the # symbol in the toolbar. Paste the contents of your Results.txt file in between the code tags (where the cursor is).
Move to after the last [/code] word and submit the post.

---

### Post by Quackers on 2011-07-20
For some reason it's looking for a UUID of 386486DF64869EEE which doesn't exist.
Open a terminal and run ```
sudo update-grub
``` and assuming the Windows Loader on /dev/sda3 is found reboot and choose Windows(dev/sda3) from the grub menu and see if it boots, please.

---

### Post by DugMatt77 on 2011-07-20
Hey sorry for the delay. Had to following the installing steps as running Windows in the Grub worked. Now, with that part done, how do I programme my computer to primary boot windows and boot ubuntu secondary.

cheers

---

### Post by Quackers on 2011-07-20
Aha! That's also good :-)
You can install Startup Manager, or Grub Customizer, or you can do it manually with this guide
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by DugMatt77 on 2011-07-20
Can I ask you what you would recommend?

---

### Post by Quackers on 2011-07-20
I'm old, I do it the old way.
Startup Manager works, but can need re-doing every time a new kernel is installed, iirc. It's the easiest way though.
Install through synaptic package manager.

---

### Post by DugMatt77 on 2011-07-20
How can I configure it from vista?
Or should i do it from ubuntu.
Im having trouble :(

---

### Post by Quackers on 2011-07-20
As grub is in the mbr you should do it from Ubuntu.
Trouble? With Startup Manager? Or the old way?

---

### Post by DugMatt77 on 2011-07-20
If you got some spare time and if you dont mind, do you think you could talk me through it?
Would be much appreciated!

---

### Post by DugMatt77 on 2011-07-20
I actually tried doing what the website you linked me suggested and ended up getting 

```
 matty@MasterShifu:~$ sudo apt-get install lilo
[sudo] password for matty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 191 not upgraded.
Need to get 380 kB of archives.
After this operation, 1,360 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://nz.archive.ubuntu.com/ubuntu/ natty/main mbr i386 1.1.10-2 [23.0 kB]
Get:2 http://nz.archive.ubuntu.com/ubuntu/ natty/main lilo i386 1:22.8-10ubuntu1 [357 kB]
Fetched 380 kB in 1s (327 kB/s)
Preconfiguring packages ...
Selecting previously deselected package mbr.
(Reading database ... 129488 files and directories currently installed.)
Unpacking mbr (from .../archives/mbr_1.1.10-2_i386.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-10ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-10ubuntu1) ...
matty@MasterShifu:~$ sudo lilo -M /dev/sda3 mbr
Fatal: /dev/sda3 is not a master device with a primary parition table
matty@MasterShifu:~$ 
 
```

So sda3, which IS windows Vista is not a primary partition table..
How do i make it my primary boot?

---

