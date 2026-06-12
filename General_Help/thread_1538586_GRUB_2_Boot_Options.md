---
title: "GRUB 2 Boot Options"
date: 2010-07-25
forum: General Help
---

### Post by Webpope on 2010-07-25
When I start Grub I get 6 boot options.  How can I eliminate the other four so I just have Windows 7 and Ubuntu as my boot options?  I have tried Synaptics but there is an old Vista boot i cant remove and I can't figure out the old ubuntu install from my new.  They have the same number (2.6.32-21)

Also is there anyway to change the resolution settings in grub 2?

---

### Post by drs305 on 2010-07-25
Which boot options - different kernels, the memtest86+ test, recovery modes?

You can remove memtest86+ and recovery modes by changing the settings in /etc/default/grub.
Take a look at this Grub 2 Basics Thread (Sections 5 & 6):
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")



You can remove older kernels from your system, which also removes them from the menu. The easiest way is to use Ubuntu Tweak. See the "Removing Older Kernels" section of this thread:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

You can change the resolution of the Grub2 menu via the /etc/default/grub file. Again, reference the above link on G2 Basics. See the setting for "GRUB_GFXMODE=640x480".

---

### Post by Webpope on 2010-07-25
> **drs305 said:**
> Which boot options - different kernels, the memtest86+ test, recovery modes?

You can remove memtest86+ and recovery modes by changing the settings in /etc/default/grub.
Take a look at this Grub 2 Basics Thread (Sections 5 & 6):
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)



You can remove older kernels from your system, which also removes them from the menu. The easiest way is to use Ubuntu Tweak. See the "Removing Older Kernels" section of this thread:
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

You can change the resolution of the Grub2 menu via the /etc/default/grub file. Again, reference the above link on G2 Basics. See the setting for "GRUB_GFXMODE=640x480".


Thanks.  Do you know how to remove an old Vista loader?

Also, synaptics failed to find ver. 2.6.32-17 when i searched it.  I also have a 2.6.32-21 on my boot screen that i can not find.  *Note - I am running a 2.6.32-21 and i can find it, just not the old one.

Edit:  Ubuntu Tweak removed some ver. -24 but it can not find ver. 17 or the old -21 and the boot screen has not gotten any shorter.

---

### Post by drs305 on 2010-07-25
Probably the best thing to do would be to run *meierfra's* boot info script:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")
Paste the contents between "code" tags, which you can generate by pressing the # icon.

By looking at the grub configuration files it should help us find the old references. I would suspect that if you can't find the actual linux  kernels they are listed in an old grub.cfg or menu.lst file, which Grub2 'mines' when 30_os-prober goes looking for other OS's. The same may be true for the Vista loader as well but I'm not as knowledgeable about Windows if it's not embedded within a Grub menu somewhere.

**Added:** You could test this theory by temporarily turning off 30_os-prober, running "update-grub", and checking the new menuentries to see if the list is shorter. Then turn 30_os-prober back on to make sure you retain your Windows option:
```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
cat /boot/grub/grub.cfg | grep menuentry
sudo chmod +x /etc/grub.d/30_os-prober
```

---

### Post by Webpope on 2010-07-25
My results from the menuentry:

```
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {

```

It does not change from +x to -x.


Results from Boot Info Script

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/burg.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   332,481,239   332,479,192   7 HPFS/NTFS
/dev/sda2         461,145,825   488,392,064    27,246,240   7 HPFS/NTFS
/dev/sda3         332,481,301   461,145,824   128,664,524   5 Extended
/dev/sda5         332,481,303   398,215,740    65,734,438  83 Linux
/dev/sda6         455,812,308   461,145,824     5,333,517  82 Linux swap / Solaris
/dev/sda7         398,217,216   453,343,231    55,126,016  83 Linux
/dev/sda8         453,345,280   455,811,071     2,465,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E0408C8A408C695C                       ntfs                                     
/dev/sda2        2C88743C8874071C                       ntfs       HP_RECOVERY                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        252f5f1e-a0c7-4328-b7f7-b904b2fd990a   ext4                                     
/dev/sda6        ebd2b0de-236e-4ae7-904b-2563518125e7   swap                                     
/dev/sda7        d79e90f8-613d-4c82-abb2-e2f6de844b52   ext4                                     
/dev/sda8        eded9ca3-6faa-4c69-8b81-d04db7695b6f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 252f5f1e-a0c7-4328-b7f7-b904b2fd990a
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
search --no-floppy --fs-uuid --set 252f5f1e-a0c7-4328-b7f7-b904b2fd990a
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 252f5f1e-a0c7-4328-b7f7-b904b2fd990a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=252f5f1e-a0c7-4328-b7f7-b904b2fd990a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 252f5f1e-a0c7-4328-b7f7-b904b2fd990a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=252f5f1e-a0c7-4328-b7f7-b904b2fd990a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 252f5f1e-a0c7-4328-b7f7-b904b2fd990a
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=252f5f1e-a0c7-4328-b7f7-b904b2fd990a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 252f5f1e-a0c7-4328-b7f7-b904b2fd990a
    echo    'Loading Linux 2.6.31-17-generic ...'
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=252f5f1e-a0c7-4328-b7f7-b904b2fd990a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 252f5f1e-a0c7-4328-b7f7-b904b2fd990a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 252f5f1e-a0c7-4328-b7f7-b904b2fd990a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e0408c8a408c695c
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=252f5f1e-a0c7-4328-b7f7-b904b2fd990a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ebd2b0de-236e-4ae7-904b-2563518125e7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 178.3GB: boot/grub/core.img
 175.4GB: boot/grub/grub.cfg
 171.9GB: boot/initrd.img-2.6.31-17-generic
 171.9GB: boot/initrd.img-2.6.32-21-generic
 171.3GB: boot/vmlinuz-2.6.31-17-generic
 171.6GB: boot/vmlinuz-2.6.32-21-generic
 171.9GB: initrd.img
 171.9GB: initrd.img.old
 171.6GB: vmlinuz
 171.3GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set d79e90f8-613d-4c82-abb2-e2f6de844b52
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set d79e90f8-613d-4c82-abb2-e2f6de844b52
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
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set d79e90f8-613d-4c82-abb2-e2f6de844b52
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d79e90f8-613d-4c82-abb2-e2f6de844b52 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set d79e90f8-613d-4c82-abb2-e2f6de844b52
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d79e90f8-613d-4c82-abb2-e2f6de844b52 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=d79e90f8-613d-4c82-abb2-e2f6de844b52 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=eded9ca3-6faa-4c69-8b81-d04db7695b6f none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 221.2GB: boot/grub/core.img
 221.3GB: boot/grub/grub.cfg
 221.5GB: boot/initrd.img-2.6.32-21-generic
 221.3GB: boot/vmlinuz-2.6.32-21-generic
 221.5GB: initrd.img.old
 221.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  e7 d3 c7 3a ea f2 0f 61  2b 06 84 11 9f a5 82 14  |...:...a+.......|
00000010  a1 aa 95 23 32 88 cf a3  76 b3 1b 72 d3 51 45 5c  |...#2...v..r.QE\|
00000020  46 07 43 4d e2 c1 e9 ea  fa 78 fc 2f f0 ab e8 5c  |F.CM.....x./...\|
00000030  65 a3 0f c3 d0 ff 7e 0a  4d f1 5e 1f 80 38 0d e9  |e.....~.M.^..8..|
00000040  c0 93 e3 4f 1a c2 f4 b1  ec 5d 62 d7 bc 44 37 51  |...O.....]b..D7Q|
00000050  1f df 79 d1 90 fe 6f 6d  51 92 3e ee 8b 3b 25 f1  |..y...omQ.>..;%.|
00000060  1d 0b d7 e9 e3 be b8 24  a3 b5 7b e5 2e 7d bc 16  |.......$..{..}..|
00000070  c4 16 7d 0e ab cc 63 95  2f 92 f6 82 39 75 48 1f  |..}...c./...9uH.|
00000080  cf 11 49 8d 25 a4 a8 62  c4 c7 d1 9e 34 bb 51 b8  |..I.%..b....4.Q.|
00000090  fe 04 ab 9c d9 54 2b 45  85 1a 7d 22 b6 0c 28 d0  |.....T+E..}"..(.|
000000a0  88 ce 23 3f d4 c7 36 9f  5d 4f 5a 96 0c 77 e2 f2  |..#?..6.]OZ..w..|
000000b0  e9 a9 17 9b dd af 3c d1  27 ce 1a e8 2b 4c 9e 69  |......<.'...+L.i|
000000c0  87 f4 ea e3 78 44 f6 2f  5d 46 7b fa 59 75 f8 79  |....xD./]F{.Yu.y|
000000d0  cb 50 44 7c 40 1f ca 11  f7 76 9f 3d f8 76 ea 35  |.PD|@....v.=.v.5|
000000e0  4a ff 44 01 d4 51 9f c1  ce 61 7d ce bd 15 36 93  |J.D..Q...a}...6.|
000000f0  f3 92 c2 9e 8e ea 73 ee  71 4c 7e d5 87 73 5b 48  |......s.qL~..s[H|
00000100  8c cb ca 85 45 4b ff e9  e3 3b 7a b7 bf 66 b5 98  |....EK...;z..f..|
00000110  ca 18 b0 fc 69 77 f4 e9  ef 52 33 60 d9 de 4f 4c  |....iw...R3`..OL|
00000120  0b c4 3a 1b 10 7e e6 34  8d f4 aa 17 7a 6e 06 38  |..:..~.4....zn.8|
00000130  e6 8c 43 d5 76 ef 7e 7f  c4 5f 16 02 15 be b7 53  |..C.v.~.._.....S|
00000140  1a d0 00 cb 4f 5f db 00  ad de 78 c4 fe 64 b0 60  |....O_....x..d.`|
00000150  7d 2c 43 61 35 62 34 0e  43 34 76 e8 cb af 63 95  |},Ca5b4.C4v...c.|
00000160  39 fa 4c af ed 56 b1 01  de 8f df 3c ff e5 eb 5c  |9.L..V.....<...\|
00000170  87 01 9e d7 e3 ba 87 b9  0f 75 19 c0 38 54 4e b3  |.........u..8TN.|
00000180  52 fd 81 e3 4f 0d a0 c7  07 0a d0 9b f3 58 c7 3d  |R...O........X.=|
00000190  6e 00 e5 90 ae 7e cb ec  36 cf 9a 09 56 3d 83 27  |n....~..6...V=.'|
000001a0  33 3b 97 cc 19 c0 51 5e  12 e8 fb b4 6d b0 52 ce  |3;....Q^....m.R.|
000001b0  90 e5 9f e0 f8 47 fa f0  12 c4 fe 14 70 45 00 fe  |.....G......pE..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 26 07 eb 03 00 fe  |..........&.....|
000001d0  ff ff 05 fe ff ff 80 e1  59 07 4c 62 51 00 00 00  |........Y.LbQ...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-07-25
The script is not set up to output any burg files.

You only have -17 in sda5 but are booting sda7. So you need to boot into your install in sda5 to delete the -17 kernel.

---

