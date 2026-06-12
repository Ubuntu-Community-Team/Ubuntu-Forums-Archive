---
title: "Broken MBR on attempting to dual boot 10.10 and XP?"
date: 2010-12-31
forum: General Help
---

### Post by lone_wolfII on 2010-12-31
I've just gone and modified the MBR by following this article:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

What now happens is that I boot up the machine and all that comes up is an error: 

The disk drive for /home is not ready yet or not present

Continue to wait; or Press S to skip mounting or M for manual recovery

I have /home on a separate partition. Using the manual recovery I can see that the partition still exists and has all the files. 

What do I need to do in order to get /home mounting again? Is this even the issue?

---

### Post by Quackers on 2010-12-31
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by lone_wolfII on 2011-01-01
Thanks for the info. Here's the output of the script:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   117,178,109   117,178,047   7 HPFS/NTFS
/dev/sda2         117,188,606   371,210,239   254,021,634   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5         117,188,608   363,397,119   246,208,512  83 Linux
/dev/sda3         363,397,120   371,210,239     7,813,120  82 Linux swap / Solaris
/dev/sda4         371,210,240   488,396,799   117,186,560  83 Linux

/dev/sda2 overlaps with /dev/sda3

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D2A4645FA46447D5                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3                                               swap                                     
/dev/sda4        a2606ede-ddde-4485-a7fa-ed6d7656552c   ext4                                     
/dev/sda5        ae7f266f-7938-4cdd-aa9d-046d9eda4ff1   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a2606ede-ddde-4485-a7fa-ed6d7656552c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a2606ede-ddde-4485-a7fa-ed6d7656552c
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a2606ede-ddde-4485-a7fa-ed6d7656552c
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=a2606ede-ddde-4485-a7fa-ed6d7656552c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a2606ede-ddde-4485-a7fa-ed6d7656552c
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=a2606ede-ddde-4485-a7fa-ed6d7656552c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a2606ede-ddde-4485-a7fa-ed6d7656552c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a2606ede-ddde-4485-a7fa-ed6d7656552c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a2606ede-ddde-4485-a7fa-ed6d7656552c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a2606ede-ddde-4485-a7fa-ed6d7656552c ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a2606ede-ddde-4485-a7fa-ed6d7656552c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a2606ede-ddde-4485-a7fa-ed6d7656552c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda6       /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=99d6ee7b-dcd3-4a7f-a83f-18f287fe1c9d none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 220.2GB: boot/grub/core.img
 203.2GB: boot/grub/grub.cfg
 191.2GB: boot/initrd.img-2.6.35-22-generic
 191.4GB: boot/initrd.img-2.6.35-23-generic
 220.2GB: boot/vmlinuz-2.6.35-22-generic
 220.3GB: boot/vmlinuz-2.6.35-23-generic
 191.4GB: initrd.img
 191.2GB: initrd.img.old
 220.3GB: vmlinuz
 220.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  3b 6a 1f 4d 5a 26 47 3a  61 1a 42 f7 e8 08 79 c5  |;j.MZ&G:a.B...y.|
00000010  1d c7 81 d6 1e 4e b2 dd  80 33 71 5a a3 fc a0 b1  |.....N...3qZ....|
00000020  8a 9e 3c cc a6 7b 16 4b  e6 1a d5 0c db 14 ce ee  |..<..{.K........|
00000030  f1 61 23 91 1e da 29 7b  88 90 88 e9 86 3a 3c 65  |.a#...){.....:<e|
00000040  63 71 e3 94 33 cd 2f fe  a0 4d 6f fe 0c 41 73 59  |cq..3./..Mo..AsY|
00000050  c4 7b 9d 40 21 84 30 75  ec 91 1a 24 7e fc 31 8c  |.{.@!.0u...$~.1.|
00000060  fb c3 69 20 d0 74 30 ec  c5 7e 4b b6 c3 97 ee 89  |..i .t0..~K.....|
00000070  0e 8d 66 ac f7 e3 cc 6c  fd 3e 62 56 a4 b6 7f fb  |..f....l.>bV....|
00000080  57 b5 1f f2 17 4e 09 4c  f4 7e e6 23 aa d8 c3 4c  |W....N.L.~.#...L|
00000090  19 0b 26 6a 92 b1 38 e2  7c b0 02 81 d6 e1 09 30  |..&j..8.|......0|
000000a0  19 e6 9c 20 99 a9 83 23  cf ea c7 c5 07 bb ea c1  |... ...#........|
000000b0  21 48 4f c9 4b ca 4a b6  03 71 74 d5 66 a4 16 e2  |!HO.K.J..qt.f...|
000000c0  af 70 6a f5 3c d1 95 dd  f5 5a 2c 0a 30 62 90 dc  |.pj.<....Z,.0b..|
000000d0  96 d5 cc 10 34 25 ec 60  c0 48 34 48 f6 70 f7 d1  |....4%.`.H4H.p..|
000000e0  b4 6b e8 77 dd 7d fb d1  54 30 72 dd 80 ff 37 47  |.k.w.}..T0r...7G|
000000f0  1a 3e 9c d9 bb 02 1d c2  4b a6 19 68 8a 94 4a 21  |.>......K..h..J!|
00000100  82 5a 11 6a 69 0a b2 9f  ea 54 52 0f f2 48 a2 9b  |.Z.ji....TR..H..|
00000110  57 c7 8c 13 94 8c 45 13  4e 1f b5 d3 df 33 c5 0b  |W.....E.N....3..|
00000120  65 17 64 9b 12 96 a3 67  79 44 05 f2 e7 59 fb c4  |e.d....gyD...Y..|
00000130  a5 e8 9f 78 76 f6 17 7f  90 bb fd 2f aa d8 ed 75  |...xv....../...u|
00000140  b9 bf 61 56 1f 5c fd fc  4f be 24 2d 54 ad 30 d9  |..aV.\..O.$-T.0.|
00000150  42 ed 79 7b 96 c4 bb 00  6b 76 02 f1 1d f5 49 5c  |B.y{....kv....I\|
00000160  24 5e 0e fe 83 b2 9f 94  9c 46 12 a8 79 1a 9f 8d  |$^.......F..y...|
00000170  d2 2b 28 d5 54 30 7d c0  ee d3 cd b0 62 b5 26 49  |.+(.T0}.....b.&I|
00000180  bf 82 c6 d7 53 25 72 21  e7 cb f5 c8 2b 64 19 08  |....S%r!....+d..|
00000190  c2 00 14 a8 2b 61 d4 d2  2c 9b 04 f8 bc 1b c3 6c  |....+a..,......l|
000001a0  ad 58 03 e8 af b2 c4 40  68 02 0b 23 e5 c1 32 0a  |.X.....@h..#..2.|
000001b0  01 aa ce a3 41 56 36 c3  88 f4 f1 53 d9 b1 00 a6  |....AV6....S....|
000001c0  e8 ff 05 6c d0 ff 01 00  00 00 01 d8 ac 0e 00 00  |...l............|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2011-01-01
The parts in red is a big problem!
```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   117,178,109   117,178,047   7 HPFS/NTFS
/dev/sda2         117,188,606   371,210,239   254,021,634   5 Extended
[COLOR="Red"]Extended  partition  linking to another extended partition[/COLOR]
/dev/sda5         117,188,608   363,397,119   246,208,512  83 Linux
/dev/sda3         363,397,120   371,210,239     7,813,120  82 Linux swap / Solaris
/dev/sda4         371,210,240   488,396,799   117,186,560  83 Linux

[COLOR="Red"]/dev/sda2 overlaps with /dev/sda3[/COLOR]
```

---

### Post by lone_wolfII on 2011-01-01
Okay, so /dev/sda5 seems to start on my /home partition and end at my swap. 

Any ideas what that partition could be? Is it something created by grub2? Would it be safe to remove?

---

### Post by Quackers on 2011-01-01
I'm still looking at it, but I think you have bigger problems.
sda3 and sda4 should be primary partitions, but they are now within an extended partition, which shouldn't be possible.
sda5 appears to be a Linux partition with no data in it. It also seems to be that it could be a second extended partition - maybe.
I would like to delete sda5 as a first step, but this carries a BIG risk and would like a second opinion first!
Such an action MAY delete Ubuntu AND part of Windows!

In your original system (with just Windows installed) how many partitions were used? Did you try and change or delete 1 or 2 of those partitions?

---

### Post by lone_wolfII on 2011-01-01
I originally installed ubuntu and put sda4 at the end of the partition table. Swap was next just to the left of it and then /home to the left again. 

I left the rest unpartitioned for the XP install (about a 50GB section to the left). 

When I installed XP I chose to overwrite the MBR (which is required on install). 

It would boot immediately into XP. That's when I attempted to follow the above link I mentioned in my first post.

EDIT

Windows was only a single partition. The entire 50GB left.

---

### Post by Quackers on 2011-01-01
If you installed Ubuntu first it seems that you made all of its partitions primary. They should not now be part of an extended partition. In fact, it shouldn't be possible. However, having said that we have seen it 3 times this week!

I wouldn't normally suggest this but, as both OSes appear to be new, can you afford to take the chance on writing off both systems and re-installing? Windows XP first this time. If so, I would try deleting sda5, if it will allow it! If nothing boots after that, though, you will likely have lost both OSes.

---

### Post by lone_wolfII on 2011-01-01
Okay thanks. 
I'll do a backup of anything I'll need and give it a shot.

---

### Post by Quackers on 2011-01-01
I'm sorry to advocate such a serious backwards step, but I believe that you are going to have serious problems at some time with that partition table.

You can delete all partitions from within the Ubuntu Live cd using gparted. In the case of extended partitions you need to delete all partitions within it before it will allow you to delete the extended partition.
If you re-install, do XP first. When it is installed boot it a couple of times.
Then install Ubuntu in the unallocated space after the XP partition.

---

### Post by lone_wolfII on 2011-01-01
I've reinstalled Windows and Ubuntu and now I'm getting a totally different issue:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 126381536 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img /boot/grub/core.img

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
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   125,837,144   125,837,082   7 HPFS/NTFS
/dev/sda2         125,837,312   126,814,207       976,896  83 Linux
/dev/sda3         126,816,254   488,394,751   361,578,498   5 Extended
/dev/sda5         126,816,256   136,579,071     9,762,816  82 Linux swap / Solaris
/dev/sda6         136,581,120   214,704,127    78,123,008  83 Linux
/dev/sda7         214,706,176   488,394,751   273,688,576  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C0E41944E4193DDA                       ntfs                                     
/dev/sda2        663a5e78-63ec-42b5-8d72-f14009f26b23   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        a5eda426-9183-4017-bcb5-b13ff8ca7930   swap                                     
/dev/sda6        5e2ab27e-8471-410c-844d-93cdebff7e81   ext4                                     
/dev/sda7        fad3e185-5155-4437-828d-e9cdf740ae00   ext4                                     
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
search --no-floppy --fs-uuid --set 5e2ab27e-8471-410c-844d-93cdebff7e81
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 663a5e78-63ec-42b5-8d72-f14009f26b23
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 663a5e78-63ec-42b5-8d72-f14009f26b23
    linux    /vmlinuz-2.6.35-22-generic root=UUID=5e2ab27e-8471-410c-844d-93cdebff7e81 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 663a5e78-63ec-42b5-8d72-f14009f26b23
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=5e2ab27e-8471-410c-844d-93cdebff7e81 ro single 
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 663a5e78-63ec-42b5-8d72-f14009f26b23
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 663a5e78-63ec-42b5-8d72-f14009f26b23
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c0e41944e4193dda
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

=================== sda2: Location of files loaded by Grub: ===================


  64.5GB: boot/grub/core.img
  64.7GB: grub/core.img
  64.7GB: grub/grub.cfg
  64.4GB: initrd.img-2.6.35-22-generic
  64.4GB: vmlinuz-2.6.35-22-generic

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
UUID=5e2ab27e-8471-410c-844d-93cdebff7e81 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=663a5e78-63ec-42b5-8d72-f14009f26b23 /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=fad3e185-5155-4437-828d-e9cdf740ae00 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a5eda426-9183-4017-bcb5-b13ff8ca7930 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  92 ae f5 ee 95 26 3f 59  60 61 ed fd eb 81 f1 5f  |.....&?Y`a....._|
00000010  e4 cb e5 7f 94 92 db ab  54 83 aa 80 46 a3 21 2b  |........T...F.!+|
00000020  fe 57 5a 1f c5 55 3c 29  d3 80 de a5 e1 0c 21 45  |.WZ..U<)......!E|
00000030  22 4c 9f 2e 03 3e 6c f0  3e 16 cb a7 5e a8 b8 4b  |"L...>l.>...^..K|
00000040  54 24 f8 14 22 45 8a f5  ba bc 66 52 2d 36 28 04  |T$.."E....fR-6(.|
00000050  c2 ec 24 18 09 8b c7 25  64 c7 46 05 63 fa ac f0  |..$....%d.F.c...|
00000060  7c 61 f4 16 fe 31 1d 2f  5e 24 83 41 f8 90 a8 19  ||a...1./^$.A....|
00000070  58 95 e2 f1 dc 12 28 36  89 71 6f 7a 6a a9 f5 94  |X.....(6.qozj...|
00000080  ff 08 06 00 23 60 08 e7  a4 55 27 a4 c8 e1 90 42  |....#`...U'....B|
00000090  6d ef 5d 10 22 13 7a 5d  4d eb e8 d2 da 4a b4 a7  |m.].".z]M....J..|
000000a0  75 d5 7b 46 d1 0e d1 a0  5c 67 1f c3 a0 a0 b8 7c  |u.{F....\g.....||
000000b0  1e 0b 4b f3 f1 ac a7 a9  ef 69 d7 00 30 31 77 62  |..K......i..01wb|
000000c0  e0 01 00 00 ff fb a4 04  17 80 03 5d 58 da fb 03  |...........]X...|
000000d0  2c 7a 6e 6b fb 5f 60 65  8f 0c 9d 59 6d ec 24 49  |,znk._`e...Ym.$I|
000000e0  29 91 2b 2d bd 81 89 bd  de 96 2b aa 40 7c 56 dc  |).+-......+.@|V.|
000000f0  fe 97 ad 13 64 56 55 3f  6c 96 5e fd 67 56 ea d5  |....dVU?l.^.gV..|
00000100  96 aa 3e e5 41 77 29 8a  a4 c8 ec 11 52 25 dc ea  |..>.Aw).....R%..|
00000110  ee 66 d4 88 29 6a dd 3f  46 bb 0b 9d 95 2c 35 80  |.f..)j.?F....,5.|
00000120  72 30 60 da 33 3e 4c 2a  aa 10 02 5a 45 be 5d 35  |r0`.3>L*...ZE.]5|
00000130  5e 35 97 20 22 05 dc 64  91 b9 0b 4e 9d 81 e6 e7  |^5. "..d...N....|
00000140  e2 f4 74 97 33 b3 7c 3a  9d 32 e6 a8 c5 4c cc 15  |..t.3.|:.2...L..|
00000150  47 36 3d e8 de 96 2b aa  40 7c 56 dc f3 a5 eb 44  |G6=...+.@|V....D|
00000160  d9 15 95 4f db 25 97 bf  59 d5 ba b5 65 aa 8f b9  |...O.%..Y...e...|
00000170  50 5d ca 62 a9 32 3b 04  54 89 77 3a bb 99 b5 22  |P].b.2;.T.w:..."|
00000180  0a 5a b7 4f d1 ae c2 e7  63 a5 84 59 0a 72 2a 15  |.Z.O....c..Y.r*.|
00000190  0a 95 16 8a bb b7 44 13  02 d3 6d 37 c4 46 2f 7a  |......D...m7.F/z|
000001a0  00 92 30 54 e9 76 d0 d1  ee 2e c4 44 41 cd 18 6c  |..0T.v.....DA..l|
000001b0  e3 6b db 2e 82 bb 25 d5  64 34 90 61 05 bb 00 fe  |.k....%.d4.a....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f8 94 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 f8  94 00 00 18 a8 04 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

So what is this core.img file? I only mounted /boot when I ran sudo grub-install, do I need to mount / as well?

---

