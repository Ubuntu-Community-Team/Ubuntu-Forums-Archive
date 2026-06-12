---
title: "grub menu lost vista"
date: 2010-10-17
forum: General Help
---

### Post by agkq62 on 2010-10-17
I have just loaded version 10.04 on to my laptop in a new partition so I now have Vista, 9.10 and !0.04. The grub menu is showing the two ubu versions but Vista is missing. I have run the commands from this link [http://ubuntuforums.org/showpost.php?p=8008800&postcount=3](http://ubuntuforums.org/showpost.php?p=8008800&postcount=3)   but still no Vista.

Any suggestion please.

maxwell@maxwell-laptop:~$ sudo apt-http://ubuntuforums.org/showpost.php?p=8008800&postcount=3get install os-prober
Reading package lists... Done
Building dependency tree       
Reading state information... Done
os-prober is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 327 not upgraded.
maxwell@maxwell-laptop:~$ sudo os-prober
/dev/sda1:Dell Utility Partition:DellUtility:chain
/dev/sda3:Windows Vista (loader):Windows:chain
/dev/sda9:Ubuntu 10.04 LTS (10.04):Ubuntu:linux
maxwell@maxwell-laptop:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/sda1
Found Windows Vista (loader) on /dev/sda3
Found Ubuntu 10.04 LTS (10.04) on /dev/sda9
done
maxwell@maxwell-laptop:~$

---

### Post by wilee-nilee on 2010-10-17
Post the bootscript in my signature. When you paste the text from running the script click on the # and put the text in the generated code tags.

---

### Post by drs305 on 2010-10-17
> **agkq62 said:**
> I have just loaded version 10.04 on to my laptop in a new partition so I now have Vista, 9.10 and !0.04. The grub menu is showing the two ubu versions but Vista is missing.  ... but still no Vista.

Any suggestion please.

maxwell@maxwell-laptop:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/sda1
[COLOR="Red"]Found Windows Vista (loader) on /dev/sda3[/COLOR]
Found Ubuntu 10.04 LTS (10.04) on /dev/sda9
done
maxwell@maxwell-laptop:~$

It does appear G2 is finding the Vista partition. I suspect you are updating the wrong grub.cfg file. Switch to your other Ubuntu OS and run update-grub. You will probably find the missing Vista entry. You can also *chroot* into your other Ubuntu partition and perform the update.

---

### Post by agkq62 on 2010-10-17
If I have done this correctly it will be a miracle :)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       224,909       224,847   6 FAT16
/dev/sda2             225,280    21,196,799    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,196,800    96,598,844    75,402,045   7 HPFS/NTFS
/dev/sda4          96,600,062   156,296,384    59,696,323   5 Extended
/dev/sda5         117,129,978   117,467,279       337,302   6 FAT16
/dev/sda6         154,577,493   156,296,384     1,718,892  82 Linux swap / Solaris
/dev/sda7         117,467,343   152,938,799    35,471,457  83 Linux
/dev/sda8         152,938,863   154,577,429     1,638,567  82 Linux swap / Solaris
/dev/sda9          96,600,064   116,156,415    19,556,352  83 Linux
/dev/sda10        116,158,464   117,129,215       970,752  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       0323e755-84a4-4124-98a4-f6e7b4dd455e   swap                                     
/dev/sda1        07D7-0503                              vfat                                     
/dev/sda2        8454AAD454AAC7EE                       ntfs       RECOVERY                      
/dev/sda3        A6D8CC16D8CBE2A3                       ntfs                                     
/dev/sda5        B4F9-1B6A                              vfat                                     
/dev/sda6        52b57f04-0b68-40d5-81af-2838291b3c18   swap                                     
/dev/sda7        f337a3ff-6fef-4163-a90f-b95e61cb2e26   ext4                                     
/dev/sda8        8809a457-e847-4fe0-ae59-d7129546264e   swap                                     
/dev/sda9        7dc6d4c6-74b5-4765-862f-06be96c08452   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="6"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set f337a3ff-6fef-4163-a90f-b95e61cb2e26
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=4
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set f337a3ff-6fef-4163-a90f-b95e61cb2e26
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f337a3ff-6fef-4163-a90f-b95e61cb2e26 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set f337a3ff-6fef-4163-a90f-b95e61cb2e26
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f337a3ff-6fef-4163-a90f-b95e61cb2e26 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 07d7-0503
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set a6d8cc16d8cbe2a3
    chainloader +1
}
menuentry "'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda9)" {
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 7dc6d4c6-74b5-4765-862f-06be96c08452
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=7dc6d4c6-74b5-4765-862f-06be96c08452 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda9)" {
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 7dc6d4c6-74b5-4765-862f-06be96c08452
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=7dc6d4c6-74b5-4765-862f-06be96c08452 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=f337a3ff-6fef-4163-a90f-b95e61cb2e26 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=8809a457-e847-4fe0-ae59-d7129546264e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  60.2GB: boot/grub/core.img
  63.5GB: boot/grub/grub.cfg
  62.5GB: boot/initrd.img-2.6.31-14-generic
  62.5GB: boot/vmlinuz-2.6.31-14-generic
  62.5GB: initrd.img
  62.5GB: vmlinuz

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 7dc6d4c6-74b5-4765-862f-06be96c08452
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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 7dc6d4c6-74b5-4765-862f-06be96c08452
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 7dc6d4c6-74b5-4765-862f-06be96c08452
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7dc6d4c6-74b5-4765-862f-06be96c08452 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 7dc6d4c6-74b5-4765-862f-06be96c08452
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7dc6d4c6-74b5-4765-862f-06be96c08452 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 7dc6d4c6-74b5-4765-862f-06be96c08452
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 7dc6d4c6-74b5-4765-862f-06be96c08452
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07d7-0503
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a6d8cc16d8cbe2a3
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f337a3ff-6fef-4163-a90f-b95e61cb2e26
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=f337a3ff-6fef-4163-a90f-b95e61cb2e26 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f337a3ff-6fef-4163-a90f-b95e61cb2e26
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=f337a3ff-6fef-4163-a90f-b95e61cb2e26 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=7dc6d4c6-74b5-4765-862f-06be96c08452 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=0323e755-84a4-4124-98a4-f6e7b4dd455e none            swap    sw              0       0

=================== sda9: Location of files loaded by Grub: ===================


  56.2GB: boot/grub/core.img
  54.6GB: boot/grub/grub.cfg
  56.3GB: boot/initrd.img-2.6.32-21-generic
  56.2GB: boot/vmlinuz-2.6.32-21-generic
  56.3GB: initrd.img
  56.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  50 12 5c 47 04 db 70 03  0d 71 18 80 40 0a 7d 0a  |P.\G..p..q..@.}.|
00000010  80 02 e6 07 d7 31 15 75  11 f5 14 f6 70 03 dc 70  |.....1.u....p..p|
00000020  03 f1 14 82 d9 7f 03 00  88 d6 e6 07 31 0e 07 f5  |............1...|
00000030  61 72 0a b0 73 d2 5d 47  04 dd 4b 70 03 f1 0d 7e  |ar..s.]G..Kp...~|
00000040  ff 14 00 b8 70 0a d8 39  b0 11 00 50 03 8c 72 0a  |....p..9...P..r.|
00000050  70 50 25 5e 58 47 04 de  70 03 71 0a 4a 7f 03 00  |pP%^XG..p.q.J...|
00000060  20 28 fc e5 07 80 b0 03  00 90 41 7b 03 ba 64 47  | (........A{..dG|
00000070  04 df 74 03 0e 43 70 82  fd 0d 18 00 e6 07 31 31  |..t..Cp.......11|
00000080  00 ac b0 71 d0 16 f7 6f  e3 70 03 e0 70 03 20 08  |...q...o.p..p. .|
00000090  20 ee 8e e9 ff 0d 00 60  13 f0 06 b1 0a 00 d0 fb  | ......`........|
000000a0  06 e4 65 47 94 04 e1 f4  06 3c ff 1b 00 98 70 03  |..eG.....<....p.|
000000b0  31 b1 0a 00 10 15 f2 06  f5 0d 89 66 18 47 04 e2  |1..........f.G..|
000000c0  74 03 ff d8 00 00 d0 33  70 03 31 07 00 50 78 03  |t......3p.1..Px.|
000000d0  f0 0c 21 67 28 47 04 e3  74 03 55 ff 06 00 08 e6  |..!g(G..t.U.....|
000000e0  fd f0 df b0 03 00 ac 93  0f f2 06 f0 30 a0 8f 68  |............0..h|
000000f0  47 04 e4 74 03 03 ff 14  cc 00 40 70 03 31 07 00  |G..t......@p.1..|
00000100  0c a3 ab 75 03 a0 bf 6c  47 04 e5 74 03 fb ff 06  |...u...lG..t....|
00000110  cc 00 b0 70 03 31 07 00  4c 40 7d f0 01 41 75 03  |...p.1..L@}..Au.|
00000120  14 6e 47 04 e6 74 03 ea  a9 7f 03 00 e8 70 03 50  |.nG..t.......p.P|
00000130  f8 29 a8 f4 29 5a 46 70  03 e7 70 03 71 26 a7 7f  |.)..)ZFp..p.q&..|
00000140  03 00 10 20 fe e5 07 b1  0a 00 cc 0a 09 d0 01 00  |... ............|
00000150  00 f5 06 f5 71 47 04 4a  e8 f4 06 f3 7f 03 00 58  |....qG.J.......X|
00000160  70 03 78 39 30 07 00 f2  c0 0f f0 01 f2 06 1a 00  |p.x90...........|
00000170  40 00 37 72 47 04 e9 f4  06 cd 31 7f 03 00 38 ff  |@.7rG.....1...8.|
00000180  70 e3 71 03 fc 0d 83 d0  01 f7 06 ac 74 47 04 ea  |p.q.........tG..|
00000190  ff 06 9b 32 02 41 00 90  f0 06 31 0e 00 44 f8 06  |...2.A....1..D..|
000001a0  41 70 18 99 7d 47 04 eb  f4 06 f2 01 80 02 00 00  |Ap..}G..........|
000001b0  65 f7 16 ff 14 38 70 03  62 c8 b0 0a 00 3e 00 fe  |e....8p.b....>..|
000001c0  ff ff 06 fe ff ff fc 42  39 01 96 25 05 00 00 fe  |.......B9..%....|
000001d0  ff ff 05 fe ff ff 18 aa  74 03 ab 3a 1a 00 00 00  |........t..:....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by drs305 on 2010-10-17
agkq62,

It all looks good to me. If you boot into Maverick you should be able to see and boot to your Ubuntu *and* Vista installs.

If it does work and you want to know *what* I looked for I'd be happy to elaborate. If it doesn't work, then ...

---

### Post by agkq62 on 2010-10-17
Thanks for the replies.

How do I boot into Maverick?

Thanks

---

### Post by drs305 on 2010-10-17
> **agkq62 said:**
> Thanks for the replies.

How do I boot into Maverick?

Thanks

I misspoke.

Boot from the first menuentry and see where it takes you.

If you run the mount command
```
mount | grep " / "
```
 and / is not on sda9:


```

sudo mount /dev/sda9 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

To do this if you are on Karmic (the same, just expressed differently):
```
sudo mount /dev/sda9 /mnt
sudo grub-install --root-directory=/mnt /dev/sda9
```

Reboot and hopefully it will boot to Lucid on sda9. Then run:
```
sudo update-grub
```

---

### Post by oldfred on 2010-10-17
It looks like the os prober found your windows in sda3 but called it recovery environment. It should let you boot your windows.

If you want correct title drs305 has some good info on changing titles.
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

I just copy the entry to 40_custom and edit it.
Something like this post which discusses editing 40_custom:
How to: Create a Customized GRUB2 Screen that is Maintenance Free. 
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by drs305 on 2010-10-17
@ oldfred,

I've seen a few of these recently. Do you know if "Windows Recovery Environment (loader)" is being used as the default entry by Grub for the normal Win7 boot option. Does it only do this when there are two Win7 partitions?

I can put that title in the Title Tweaks if it's becoming a standard misnomer.

@ agkq62,

When you ran the boot info script, had you booted the first menuentry? Your / was mounted on sda7 at the time you ran the script.

---

### Post by oldfred on 2010-10-17
It was with either Karmic or Lucid (or both) and the Recovery would be shown as Vista (not recovery) and if Vista or 7 it seemed to be recovery. I know several XP users complained they did not even have Vista, but I assumed they were versions of Vista down graded to XP and they just did not update the recovery partition.

But I think more recent versions Maverick have it correct. I will watch more closely and let you know.

---

### Post by drs305 on 2010-10-17
> **oldfred said:**
> It was with either Karmic or Lucid (or both) and the Recovery would be shown as Vista (not recovery) and if Vista or 7 it seemed to be recovery. I know several XP users complained they did not even have Vista, but I assumed they were versions of Vista down graded to XP and they just did not update the recovery partition.

But I think more recent versions Maverick have it correct. I will watch more closely and let you know.

Thanks. I vaguely remember the issue from the past but didn't know how it related to current installs. I went ahead and added a section to the Title Tweaks to change "Windows Recovery Partition" to "Windows Vista" but it would actually apply to changing any 30_os-prober Windows title to something else.

---

### Post by agkq62 on 2010-10-18
> **drs305 said:**
> @ oldfred,


@ agkq62,

When you ran the boot info script, had you booted the first menuentry? Your / was mounted on sda7 at the time you ran the script.

No I was running 9.10 the next to last entry. I am still having severe problems with 10.04 regardng the moniter display [http://ubuntuforums.org/showthread.php?p=9982323#post9982323](http://ubuntuforums.org/showthread.php?p=9982323#post9982323) and the wireless connection.Good job I kept 9.10

You were right Recovery does boot Vista, strangely I did try Recovery at first and it loaded a disk utility and then nothing but it now works. Incidently I did initially try an upgrade to 10.04 and the grub menu was the same with Recovery and no Vista.

Thanks for your help but I think 10.04 just doesn't like my laptop.

---

