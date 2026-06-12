---
title: "I need help! Any advice would make me happy!"
date: 2010-10-23
forum: General Help
---

### Post by AlbatronX on 2010-10-23
Hello everyone! im new to the linux community! I have made the stupid mistake to just delete a linux partition and now when i boot a message appears and says 
error: unknown filesystem grub rescue >
I have search on the net for this problem and i have understand it a little.  But my situation is a bit different and because i don't want to format my hard disc i wanna try to fix it. So before a couple months i download ubuntu 9.10 and i installed it a month later.  But my computer used to crash all the time and i couldnt use it.  So i download the latest ubuntu 10.4 and install it while having windows xp and the old ubuntu 9.10(so i had windows xp, ubuntu 9.10 and ubuntu 10.4 partitions).  Now i tried to delete the partition of ubuntu 9.10 from disc utility.  so  i have the message i wrote above when i boot.  I dont wanna delete my windows xp and ubuntu 10.4.  what should i do to stop this message from appearing.  im sorry for my bad english! if anyone need further explanation for my problem just say it! everyone thanks in advance for your time!

---

### Post by spiky001 on 2010-10-23
Hi in terminal type ```
sudo update-grub
```
use live cd to get terminal

---

### Post by AlbatronX on 2010-10-23
> **spiky001 said:**
> Hi in terminal type ```
sudo update-grub
```use live cd to get terminal


I tried it and i got: 
/usr/sbin/grub-probe: error: cannot find a devise for / (is /dev mounted?).

I mounted all volums with disk utility but nothing changed...

---

### Post by Rubi1200 on 2010-10-23
Please post the output of the following commands (run them separately):
```
sudo fdisk -l 
```

```
cat /etc/fstab 
```

```
sudo blkid
```

Thanks.

---

### Post by AlbatronX on 2010-10-23
thats what i got:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0e070e06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       67408   541454159+   7  HPFS/NTFS
/dev/sda2           84949      121601   294415192    5  Extended
/dev/sda5           85773      119379   269943808   83  Linux
/dev/sda6          119379      120490     8926208   82  Linux swap / Solaris
/dev/sda7          120491      121601     8924076   83  Linux
/dev/sda8           84949       85772     6618717   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x412cd1ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS



ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0



ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0058405F58405616" TYPE="ntfs" 
/dev/sda5: UUID="c36e2e8f-6239-4fa9-80c9-97e5ac718fa2" TYPE="ext4" 
/dev/sda6: UUID="612496dd-d253-46e0-bb08-035e820b9cf3" TYPE="swap" 
/dev/sda7: UUID="395165dc-25f2-48fe-8ef2-6759931297d7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="3572534a-c0e1-430e-8d14-f55c271cfd83" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="OneTouch 4" UUID="55D123D9E79ABF54" TYPE="ntfs" 





***(one touch is a hard disc out my computer)***
**the two ext3 linux partitions are the ubuntu9.10 and the swap partition that i deleted**

---

### Post by Rubi1200 on 2010-10-23
Well, if you deleted them I am not sure why they are still showing up.

Since you are on the LiveCD, please post the results from the boot-script linked at the bottom of my post.

Wrap the text with the # tag when posting back here.

Thanks.

---

### Post by lindsay7 on 2010-10-23
you can try this,

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

Your grub configuration may have been on the parition you deledted.

---

### Post by AlbatronX on 2010-10-23
#                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,082,908,381 1,082,908,319   7 HPFS/NTFS
/dev/sda2       1,364,689,681 1,953,520,064   588,830,384   5 Extended
/dev/sda5       1,377,929,216 1,917,816,831   539,887,616  83 Linux
/dev/sda6       1,917,818,880 1,935,671,295    17,852,416  82 Linux swap / Solaris
/dev/sda7       1,935,671,913 1,953,520,064    17,848,152  83 Linux
/dev/sda8       1,364,689,746 1,377,927,179    13,237,434  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0058405F58405616                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c36e2e8f-6239-4fa9-80c9-97e5ac718fa2   ext4                                     
/dev/sda6        612496dd-d253-46e0-bb08-035e820b9cf3   swap                                     
/dev/sda7        395165dc-25f2-48fe-8ef2-6759931297d7   ext3                                     
/dev/sda8        3572534a-c0e1-430e-8d14-f55c271cfd83   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        55D123D9E79ABF54                       ntfs       OneTouch 4                    
/dev/sdb: PTTYPE="dos" 

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set c36e2e8f-6239-4fa9-80c9-97e5ac718fa2
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
search --no-floppy --fs-uuid --set c36e2e8f-6239-4fa9-80c9-97e5ac718fa2
set locale_dir=($root)/boot/grub/locale
set lang=el
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
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set c36e2e8f-6239-4fa9-80c9-97e5ac718fa2
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=c36e2e8f-6239-4fa9-80c9-97e5ac718fa2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.32-25-generic-pae (&#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set c36e2e8f-6239-4fa9-80c9-97e5ac718fa2
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=c36e2e8f-6239-4fa9-80c9-97e5ac718fa2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set c36e2e8f-6239-4fa9-80c9-97e5ac718fa2
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=c36e2e8f-6239-4fa9-80c9-97e5ac718fa2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.32-24-generic-pae (&#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set c36e2e8f-6239-4fa9-80c9-97e5ac718fa2
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=c36e2e8f-6239-4fa9-80c9-97e5ac718fa2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set c36e2e8f-6239-4fa9-80c9-97e5ac718fa2
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=c36e2e8f-6239-4fa9-80c9-97e5ac718fa2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.32-23-generic-pae (&#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set c36e2e8f-6239-4fa9-80c9-97e5ac718fa2
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=c36e2e8f-6239-4fa9-80c9-97e5ac718fa2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set c36e2e8f-6239-4fa9-80c9-97e5ac718fa2
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=c36e2e8f-6239-4fa9-80c9-97e5ac718fa2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.32-22-generic-pae (&#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set c36e2e8f-6239-4fa9-80c9-97e5ac718fa2
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=c36e2e8f-6239-4fa9-80c9-97e5ac718fa2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set c36e2e8f-6239-4fa9-80c9-97e5ac718fa2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set c36e2e8f-6239-4fa9-80c9-97e5ac718fa2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0058405f58405616
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 81ec7c48-da72-4a3a-9eb6-1ecbaa36308e
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=81ec7c48-da72-4a3a-9eb6-1ecbaa36308e ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 81ec7c48-da72-4a3a-9eb6-1ecbaa36308e
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=81ec7c48-da72-4a3a-9eb6-1ecbaa36308e ro single
    initrd /boot/initrd.img-2.6.31-14-generic
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
# / was on /dev/sda7 during installation
UUID=c36e2e8f-6239-4fa9-80c9-97e5ac718fa2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=612496dd-d253-46e0-bb08-035e820b9cf3 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 845.2GB: boot/grub/core.img
 821.8GB: boot/grub/grub.cfg
 845.3GB: boot/initrd.img-2.6.32-22-generic-pae
 845.3GB: boot/initrd.img-2.6.32-23-generic-pae
 845.5GB: boot/initrd.img-2.6.32-24-generic-pae
 845.5GB: boot/initrd.img-2.6.32-25-generic-pae
 845.3GB: boot/vmlinuz-2.6.32-22-generic-pae
 845.3GB: boot/vmlinuz-2.6.32-23-generic-pae
 845.3GB: boot/vmlinuz-2.6.32-24-generic-pae
 845.3GB: boot/vmlinuz-2.6.32-25-generic-pae
 845.5GB: initrd.img
 845.5GB: initrd.img.old
 845.3GB: vmlinuz
 845.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fc cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fc e9 c7 47 fd 92  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  ff d1 2c 41 00 00 80 01  |..........,A....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 02 4c 38 3a 00 00  |......?....L8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
#
here it is

---

### Post by Rubi1200 on 2010-10-23
I think lindsay7 is absolutely right: take a look at sda7 and sda5. 

> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition [COLOR=Red]#7[/COLOR] for /boot/grub.

Anyway, a simple GRUB reinstall should fix the problem.

From a LiveCD:

```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sda
```Don't forget to run

```
sudo update-grub
```after booting into Ubuntu again.

---

### Post by AlbatronX on 2010-10-23
woooow thank your guys ! your are both amazing! thanx alot everything is fine now! really u are great! THNX!

---

### Post by Rubi1200 on 2010-10-23
You are more than welcome :)

Enjoy!

---

