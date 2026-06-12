---
title: "WinXP missing in grub menu"
date: 2011-10-03
forum: General Help
---

### Post by slaveofone on 2011-10-03
Hello all. I have boot issues.

When I first installed my system, I installed Win XP followed by Ubuntu 10.04. The grub menu showed both partitions and let me boot into either one.

After upgrading my kernel and kernel headers in Ubuntu and restarting the computer, I lost the grub menu and was booted into the grub prompt.

Having no idea what to do at this point, I used the Ubuntu 10.04 live CD, installed Boot Repair, did a repair, and rebooted.

My grub menu was back. But WinXP was no longer listed in the grub menu.

Now, every time there is a kernel update, I lose the boot menu and have to re-insert the Live CD, re-install Boot Repair, do a repair, and I'm back to a working grub menu with an Ubuntu system, but still no Win XP.

So, my question is: how do I get Win XP (dev/sda2) onto the boot menu without losing that boot menu and having to use Boot Repair all over again (which means I lose access to Win XP again)?

When I try to make changes to my grub using Grub Customizer, it takes away my Grub menu and I have to re-insert the Live CD, re-install Boot Repair, do a repair, and I'm back to a working grub menu with an Ubuntu system, but no Win XP.

For now, the only way I can boot Win XP is by using Super Grub Disk.

It would also be nice if I didn't have to lose the grub menu every single time there was a kernel update.

Thanks.

Here is my RESULTS file:

---

### Post by Dangertux on 2011-10-04
You can do the following to add it to your grub bootloader.

```

sudo mount /dev/sda2 /mnt -t ntfs
sudo update-grub

```
Reboot and your Windows XP should be in your bootloader.


If that doesn't work I suggest consulting the following : [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by slaveofone on 2011-10-04
Thanks for the tips. Unfortunately, whenever I run sudo update-grub, my grub menu disappears on reboot and I'm left at the grub prompt again. And then I have to do the whole process over again of rescuing my grub menu with Boot Repair using the Live CD. And then I'm back to square one.

I've spent time looking at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and I really have no idea what to do with it.

---

### Post by Dangertux on 2011-10-04
While it is not recommended you could edit the grub.conf file manually to add the entry for windows xp. 


Note this is not recommended and can be potentially hazardous to your bootloader's health have a recovery method handy. 

You could add an entry to /boot/grub/grub.conf something like this. 

```

menuentry  "Windows XP" {
insmod ntfs
set root=(hd0,2)
chainloader +1
}

```

That might work just be very careful when editing grub.conf

---

### Post by mastablasta on 2011-10-04
Unknown BootLoader on sda3 =?
 
 
anyway this is how oyu post results txt - just use the code tags (# icon)
 
```
                  Boot Info Script 0.60    from 17 May 2011
 
============================= Boot Info Summary: ===============================
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
sda1: __________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf
sda2: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM
sda3: __________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  
sda5: __________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda6: __________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1               2,048     1,026,047     1,024,000  83 Linux
/dev/sda2    *      1,028,160   108,438,454   107,410,295   7 NTFS / exFAT / HPFS
/dev/sda3         108,439,550 1,465,147,391 1,356,707,842   5 Extended
/dev/sda5         108,439,552 1,453,070,335 1,344,630,784  83 Linux
/dev/sda6       1,453,072,384 1,465,147,391    12,075,008  82 Linux swap / Solaris
 
"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/sda1        1c74011b-4e3e-49b4-9685-e9a4768dcc00   ext4       
/dev/sda2        30846C34846BFAAC                       ntfs       
/dev/sda5        24073ae0-09f5-4902-9038-3407a85690b1   ext4       
/dev/sda6        055b4450-4e5e-4008-9574-9e5ccd34ceea   swap       
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/sda5        /                        ext4       (rw,errors=remount-ro)
 
============================= sda1/grub/grub.conf: =============================
--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_aeon-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/pdc_fffhggbf
default=0
timeout=0
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.40.3-0.fc15.i686)
 root (hd0,0)
 kernel /vmlinuz-2.6.40.3-0.fc15.i686 ro root=/dev/mapper/vg_aeon-lv_root rd_DM_UUID=pdc_fffhggbf rd_LVM_LV=vg_aeon/lv_root rd_LVM_LV=vg_aeon/lv_swap rd_NO_LUKS rd_NO_MD LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
 initrd /initramfs-2.6.40.3-0.fc15.i686.img
title Fedora (2.6.38.6-26.rc1.fc15.i686)
 root (hd0,0)
 kernel /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=/dev/mapper/vg_aeon-lv_root rd_DM_UUID=pdc_fffhggbf rd_LVM_LV=vg_aeon/lv_root rd_LVM_LV=vg_aeon/lv_swap rd_NO_LUKS rd_NO_MD LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
 initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
--------------------------------------------------------------------------------
=================== sda1: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)
   0.015139580 = 0.016256000    grub/grub.conf                                 2
   0.015139580 = 0.016256000    grub/menu.lst                                  2
   0.014535904 = 0.015607808    grub/stage2                                    1
   0.031785011 = 0.034128896    initramfs-2.6.38.6-26.rc1.fc15.i686.img        2
   0.051601410 = 0.055406592    initramfs-2.6.40.3-0.fc15.i686.img             2
   0.012580872 = 0.013508608    vmlinuz-2.6.38.6-26.rc1.fc15.i686              1
   0.035872459 = 0.038517760    vmlinuz-2.6.40.3-0.fc15.i686                   1
================================ sda2/boot.ini: ================================
--------------------------------------------------------------------------------
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
--------------------------------------------------------------------------------
=========================== sda5/boot/grub/grub.cfg: ===========================
--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set 24073ae0-09f5-4902-9038-3407a85690b1
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
search --no-floppy --fs-uuid --set 24073ae0-09f5-4902-9038-3407a85690b1
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###
### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###
### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-34-generic" --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 24073ae0-09f5-4902-9038-3407a85690b1
 linux /boot/vmlinuz-2.6.32-34-generic root=UUID=24073ae0-09f5-4902-9038-3407a85690b1 ro   quiet splash
 initrd /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ubuntu, with Linux 2.6.32-34-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 24073ae0-09f5-4902-9038-3407a85690b1
 echo 'Loading Linux 2.6.32-34-generic ...'
 linux /boot/vmlinuz-2.6.32-34-generic root=UUID=24073ae0-09f5-4902-9038-3407a85690b1 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic" --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 24073ae0-09f5-4902-9038-3407a85690b1
 linux /boot/vmlinuz-2.6.32-21-generic root=UUID=24073ae0-09f5-4902-9038-3407a85690b1 ro   quiet splash
 initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 24073ae0-09f5-4902-9038-3407a85690b1
 echo 'Loading Linux 2.6.32-21-generic ...'
 linux /boot/vmlinuz-2.6.32-21-generic root=UUID=24073ae0-09f5-4902-9038-3407a85690b1 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux_proxy ###
### BEGIN /etc/grub.d/20_os-prober_proxy ###
### END /etc/grub.d/20_os-prober_proxy ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------
=============================== sda5/etc/fstab: ================================
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=24073ae0-09f5-4902-9038-3407a85690b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=055b4450-4e5e-4008-9574-9e5ccd34ceea none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------
=================== sda5: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)
 133.845058441 = 143.715037184  boot/grub/core.img                             1
 133.840862274 = 143.710531584  boot/grub/grub.cfg                             1
 133.968193054 = 143.847251968  boot/initrd.img-2.6.32-21-generic              1
 134.575073242 = 144.498884608  boot/initrd.img-2.6.32-33-generic              1
 134.707649231 = 144.641236992  boot/initrd.img-2.6.32-34-generic              1
 133.839199066 = 143.708745728  boot/vmlinuz-2.6.32-21-generic                 1
 429.659034729 = 461.342875648  boot/vmlinuz-2.6.32-33-generic                 3
 134.364063263 = 144.272314368  boot/vmlinuz-2.6.32-34-generic                 1
 134.707649231 = 144.641236992  initrd.img                                     1
 134.575073242 = 144.498884608  initrd.img.old                                 1
 134.364063263 = 144.272314368  vmlinuz                                        1
 429.659034729 = 461.342875648  vmlinuz.old                                    3
======================== Unknown MBRs/Boot Sectors/etc: ========================
Unknown BootLoader on sda3
00000000  aa b3 30 d7 b3 ce 7e 50  1c eb 37 7e 57 98 36 66  |..0...~P..7~W.6f|
00000010  31 81 b1 ad 0b d2 1d 76  46 54 16 2d f7 a6 3d 18  |1......vFT.-..=.|
00000020  ab a5 6c af dd 58 6c de  48 fb 49 3d fb 8e 5c 44  |..l..Xl.H.I=..\D|
00000030  7b 1c 42 ea af fd 98 26  8a 65 8d e6 ba fd fb 49  |{.B....&.e.....I|
00000040  5d 24 f0 e6 35 81 d6 70  96 03 09 77 30 31 45 b3  |]$..5..p...w01E.|
00000050  cd b8 b0 67 a1 24 9c 9a  c7 62 11 ea 15 1f bf 35  |...g.$...b.....5|
00000060  d1 2c 96 7f 6f 83 d4 df  90 f5 3e cb 36 f8 ab f6  |.,..o.....>.6...|
00000070  2a 75 c1 de 93 33 38 ef  22 33 b7 fb b5 6a e9 3f  |*u...38."3...j.?|
00000080  3a f3 a2 14 89 5e 21 51  98 06 9d 27 49 dc 7e aa  |:....^!Q...'I.~.|
00000090  b0 cb 30 cf 96 7a 83 7c  ca 44 e4 31 3a 25 42 79  |..0..z.|.D.1:%By|
000000a0  74 d8 98 57 16 a3 03 27  83 94 f1 50 96 c9 91 fb  |t..W...'...P....|
000000b0  14 14 d6 53 03 da 7b a6  d3 bc af 1e 06 ec 39 56  |...S..{.......9V|
000000c0  2c 9c 8a 72 98 b1 fa fa  1a 44 47 bb 97 f8 a7 c4  |,..r.....DG.....|
000000d0  f1 be 76 d7 fc ca e8 eb  92 9c 11 38 3f 84 23 dc  |..v........8?.#.|
000000e0  ac 15 87 33 94 8b 87 a5  9b 17 5f 77 a5 3b 7a 3a  |...3......_w.;z:|
000000f0  04 02 6c f7 26 4f 72 47  ed 40 a8 1c a1 2a ca 48  |..l.&OrG.@...*.H|
00000100  7b 8c c3 fb 38 ce 51 1d  ac f4 a8 8f a1 17 47 47  |{...8.Q.......GG|
00000110  f6 e7 d3 90 d2 cc 53 c4  28 3f 9b 11 8f d8 69 12  |......S.(?....i.|
00000120  ed 33 5d b0 6a 39 36 83  79 0c 04 28 b3 62 3f 58  |.3].j96.y..(.b?X|
00000130  7a 13 b2 f6 4a 17 5a 7e  66 1c 5a 81 3a 19 a2 4c  |z...J.Z~f.Z.:..L|
00000140  9b d5 4e 9b 65 9b 3c a9  6a f9 38 1a 85 e1 0d 48  |..N.e.<.j.8....H|
00000150  96 55 70 57 66 a5 f7 9f  84 d3 f1 31 70 89 12 a7  |.UpWf......1p...|
00000160  39 92 74 b2 67 d9 6f dc  55 54 f2 06 65 2c b8 1a  |9.t.g.o.UT..e,..|
00000170  81 cc 2d 8f e0 44 06 41  01 0a a4 4d 42 25 69 ef  |..-..D.A...MB%i.|
00000180  48 31 2a 7e 88 33 f5 ae  65 89 3f 39 ad 79 0d a5  |H1*~.3..e.?9.y..|
00000190  7b 16 51 55 b9 19 32 83  d9 86 52 35 0c 83 90 b6  |{.QU..2...R5....|
000001a0  b4 ce 15 81 10 4c 3d 8b  83 71 64 db 2b f0 bf 13  |.....L=..qd.+...|
000001b0  2c db 55 33 fa a8 49 89  94 11 54 ed 39 e5 00 fe  |,.U3..I...T.9...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 70 25 50 00 fe  |...........p%P..|
000001d0  ff ff 05 fe ff ff 02 70  25 50 00 48 b8 00 00 00  |.......p%P.H....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
 

```
 
you have a mess in partitions there. what exactly were you trying to achieve upon OS install? 2 partitions - WinXP on first Ubuntu on second?
 
at the moment you have 
partition 1 - something formated to ext4
partition 2 - windows XP
Parittion 3 - empty disk space
partition 5 - Ubuntu
Partition 6 - swap partition for Ubuntu

---

### Post by slaveofone on 2011-10-04
Thanks for the responses.

What I ended up doing was something similar to editing grub.cfg. I created a "20_windows_xp" file like this:

#! /bin/sh -e

cat << EOF
 menuentry "WinXP Home Edition" {
 set root=(hd0,2)
 chainloader +1
 }
 EOF

Then I did sudo update-grub. It took away my grub menu. So I went into the Live CD, installed Boot Repair, repaired, and when I rebooted, I had my grub menu back AND I finally had Win XP in the menu!! Whoo-hoo!

Unfortunately, there was something wrong with the WinXP boot. So I booted the Win XP CD into recovery console, did "bootcfg /rebuild", added "/Fastdetect" and when I rebooted, not only did I have a working grub menu with Ubuntu, I also had Win XP!

So grub menu is now working, both OSes are in the menu, and I can boot into both.

Hopefully when next my kernels are updated, I don't have to go through that process all over again.

---

### Post by slaveofone on 2011-10-04
Oh, yeah, I have since used GParted to remove /sda1 - it was a holdover from Fedora before I installed Win XP and Ubuntu.

---

### Post by Dangertux on 2011-10-04
Glad it worked out for you :-)

---

