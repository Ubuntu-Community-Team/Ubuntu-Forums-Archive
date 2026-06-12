---
title: "lucid and win 7 .....not responding"
date: 2011-02-11
forum: General Help
---

### Post by JG6_oddball on 2011-02-11
hi folks i hope some one here can shed some light on the the catastrophe that happened tonight...to make a long story short i lef tht e room and when i came back the system had rebooted itself (was in win 7) so i tried to go back into win 7 and got a BSOD  :( with this in the title "IRQL_NOT_LESS_OR_EQUAL" so i decided to boot into lucid and do a search....well when i got in to lucid i was greeted with a :network disabled " problem...well after rebooting several more times GRUB stop showing up and all i gotr was a flashing white curser :( next i threw in my live cd which booted up no problem with (network sound ...etc )which is where i am typing this from) i used disk utility to check both HD and they passed with no errors...so then i set about unplugging everything 9keyboard,mouse,sound, slave drive...etc) and still no grub...i can access both drives and all the files no problem.

since i can run from a liveCd my first thought is that the HD (boot-able one) is bad..but i hope not..is it possible that the MBR has become corrupt or worse yet a virus has gotten in there?

system:
asrock 830 extreme
4 gig corsair 1066
seagate 160 hd (boot) 
samsung 500gig
ati 5750 vid
corsair 750 watt

i have googled this  but found nothing concrete...thnx for any help

---

### Post by Rubi1200 on 2011-02-11
First thing to do is backup all important data using the LiveCD.

You might also want to try running memtest from the LiveCD to see if faulty memory is the problem and/or take the modules out and clean them carefully.

If you can, post the results of the boot info script:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by JG6_oddball on 2011-02-11
here is the requested info, i will run mem test aswell as rmoving and swaping them out, thnx for any help

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   170,514,879   170,308,032   7 HPFS/NTFS
/dev/sdb3         170,516,478   312,580,095   142,063,618   5 Extended
/dev/sdb5         170,516,480   306,700,287   136,183,808  83 Linux
/dev/sdb6         306,702,336   312,580,095     5,877,760  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        42489B0404B7326B                       ntfs       sam500                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4A80071E80070FDD                       ntfs       System Reserved               
/dev/sdb2        985A0B325A0B0D26                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        e58a4f2e-9902-4732-9d92-222e8dd43cd1   ext4                                     
/dev/sdb6        da1131c6-3187-4b55-96f0-7d8929f683d1   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set e58a4f2e-9902-4732-9d92-222e8dd43cd1
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set e58a4f2e-9902-4732-9d92-222e8dd43cd1
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set e58a4f2e-9902-4732-9d92-222e8dd43cd1
	linux	/boot/vmlinuz-2.6.32-28-generic-pae root=UUID=e58a4f2e-9902-4732-9d92-222e8dd43cd1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set e58a4f2e-9902-4732-9d92-222e8dd43cd1
	echo	'Loading Linux 2.6.32-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-28-generic-pae root=UUID=e58a4f2e-9902-4732-9d92-222e8dd43cd1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set e58a4f2e-9902-4732-9d92-222e8dd43cd1
	linux	/boot/vmlinuz-2.6.32-27-generic-pae root=UUID=e58a4f2e-9902-4732-9d92-222e8dd43cd1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set e58a4f2e-9902-4732-9d92-222e8dd43cd1
	echo	'Loading Linux 2.6.32-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-27-generic-pae root=UUID=e58a4f2e-9902-4732-9d92-222e8dd43cd1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set e58a4f2e-9902-4732-9d92-222e8dd43cd1
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=e58a4f2e-9902-4732-9d92-222e8dd43cd1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set e58a4f2e-9902-4732-9d92-222e8dd43cd1
	echo	'Loading Linux 2.6.32-26-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=e58a4f2e-9902-4732-9d92-222e8dd43cd1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set e58a4f2e-9902-4732-9d92-222e8dd43cd1
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=e58a4f2e-9902-4732-9d92-222e8dd43cd1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set e58a4f2e-9902-4732-9d92-222e8dd43cd1
	echo	'Loading Linux 2.6.32-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=e58a4f2e-9902-4732-9d92-222e8dd43cd1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set e58a4f2e-9902-4732-9d92-222e8dd43cd1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set e58a4f2e-9902-4732-9d92-222e8dd43cd1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 4a80071e80070fdd
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e58a4f2e-9902-4732-9d92-222e8dd43cd1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=da1131c6-3187-4b55-96f0-7d8929f683d1 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 128.3GB: boot/grub/core.img
 107.1GB: boot/grub/grub.cfg
 128.4GB: boot/initrd.img-2.6.32-25-generic-pae
 128.4GB: boot/initrd.img-2.6.32-26-generic-pae
 128.5GB: boot/initrd.img-2.6.32-27-generic-pae
 128.5GB: boot/initrd.img-2.6.32-28-generic-pae
 128.2GB: boot/vmlinuz-2.6.32-25-generic-pae
 128.3GB: boot/vmlinuz-2.6.32-26-generic-pae
 128.5GB: boot/vmlinuz-2.6.32-27-generic-pae
 128.5GB: boot/vmlinuz-2.6.32-28-generic-pae
 128.5GB: initrd.img
 128.5GB: initrd.img.old
 128.5GB: vmlinuz
 128.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  0c 8f c7 ac 57 0b 40 93  b0 23 b8 3b 57 78 e3 66  |....W.@..#.;Wx.f|
00000010  84 0e 1e bc 16 84 d7 48  35 57 bf 8e 10 ad b3 b3  |.......H5W......|
00000020  0a 1e 76 e8 21 22 e7 5c  db 0a 6f e0 1b ee 10 37  |..v.!".\..o....7|
00000030  7d f7 f3 12 06 82 62 64  70 3d a9 d4 4d a4 56 cd  |}.....bdp=..M.V.|
00000040  c4 85 bd 68 bf 7b 73 b8  77 2a 8c 48 78 8a 28 32  |...h.{s.w*.Hx.(2|
00000050  3a 3a 61 ef 3d 8c ac 81  b8 12 7c 61 ac ce 18 06  |::a.=.....|a....|
00000060  cb 49 e8 eb 8f 56 a8 89  83 fb f1 af 6d 6a fe 99  |.I...V......mj..|
00000070  22 61 3b 5f 29 0a 58 03  d2 bd 47 a2 7e 52 48 a3  |"a;_).X...G.~RH.|
00000080  0e b6 91 4e 4f 40 96 a8  fe d5 56 69 07 f5 70 e7  |...NO@....Vi..p.|
00000090  f7 2d 42 34 bd d2 af 50  95 5c 48 24 2e 8e a8 c6  |.-B4...P.\H$....|
000000a0  b3 1a 5f 10 95 7a 41 4c  57 e3 b2 94 48 e0 12 97  |.._..zALW...H...|
000000b0  2c 83 3e 41 43 55 cb ce  a9 b0 cc 1c 71 b5 ee 60  |,.>ACU......q..`|
000000c0  20 b4 fc e5 0b 28 d9 42  33 be 87 21 4a c0 c2 b2  | ....(.B3..!J...|
000000d0  4c 86 cb a7 18 81 16 40  0f 5b 6d fe 93 f4 b7 5d  |L......@.[m....]|
000000e0  c8 e9 b3 8d 28 50 dc ba  92 e8 93 98 a3 3c 1f 4d  |....(P.......<.M|
000000f0  d6 c0 bb f6 1a ba 74 ec  d6 1d 59 e6 f5 3b cc 39  |......t...Y..;.9|
00000100  25 3b ea 5d ea 86 a2 77  ec 20 c0 4e 34 fb 1b 1b  |%;.]...w. .N4...|
00000110  5f 67 d0 e2 cc f1 d3 e7  38 df 08 0f 51 07 70 a7  |_g......8...Q.p.|
00000120  f7 6c c5 7f ef fb 6b 85  25 b6 8e 45 8b cf a7 5a  |.l....k.%..E...Z|
00000130  b0 72 5d 90 98 6f ac c8  7d 7a c4 d6 c6 06 82 60  |.r]..o..}z.....`|
00000140  28 25 77 98 10 79 94 a0  5e f6 52 93 85 5a ff 8a  |(%w..y..^.R..Z..|
00000150  44 56 60 41 82 db 09 80  28 0f 8d bf 46 22 de 36  |DV`A....(...F".6|
00000160  bf a5 2f 2b eb f0 29 9e  41 5a 62 4f ee ae 5f 60  |../+..).AZbO.._`|
00000170  c2 fa fc 5b f2 35 dd e7  25 87 53 79 cd 85 d2 a7  |...[.5..%.Sy....|
00000180  0a f1 5a 86 ad 43 b6 56  61 77 db 05 75 28 e7 b3  |..Z..C.Vaw..u(..|
00000190  18 cb 7e 4a fd 97 a4 9a  40 dc 50 12 dd d6 e1 41  |..~J....@.P....A|
000001a0  c7 67 f3 bf 34 59 cc af  c7 38 a4 46 aa f9 59 0b  |.g..4Y...8.F..Y.|
000001b0  6e 19 66 d7 94 fa 97 7c  04 34 62 0b 35 3c 00 fe  |n.f....|.4b.5<..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 1e 08 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 00  1e 08 00 b8 59 00 00 00  |............Y...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2011-02-11
Windows is installed in the MBR of /dev/sdb

This is in the sdb 160 gig HD's mbr, it should be grub2 unless you have been using another bootloader. You can reload it, and first in line to be read in the bios.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by JG6_oddball on 2011-02-11
thank you wilee , I am doing a mem test now and it has made 1 pass without error :) as for the 160 gig it was the original HD the 500gig came later, i have been dual booting for 4 months with the 1600gig with no problems, what concerns me is not grub failing but why would it cause windows to BSOD  and lucid to lose network connectivity?...i fear i already know...the MB is on its way out :(:( its only 4 months old :( i will follow the grub reinstallation link and hope that fixes atleat one of the problems :)

---

### Post by JG6_oddball on 2011-02-11
in my grub.cfg there are 2 lines that refer to the bootable hard drive as "set root='(hd1.5) but the MBR is on sdb5 should that not say hd2,5?

---

### Post by wilee-nilee on 2011-02-11
> **JG6_oddball said:**
> in my grub.cfg there are 2 lines that refer to the bootable hard drive as "set root='(hd1.5) but the MBR is on sdb5 should that not say hd2,5?

hd1.5=sdb is  sda=hd0 the 0 is the sda hd.

---

### Post by JG6_oddball on 2011-02-12
> **wilee-nilee said:**
> hd1.5=sdb is  sda=hd0 the 0 is the sda hd.
 thnx wilee i forgot 0 is the first number :)

well i think i may have found the culprit....i noticed in gpart that there was no boot flag on ext4 so after enabling it grub reappeared and i was back where i started BSOD and no networking lucid...after a few reboots i got into win 7 only to find no network there either...so rebooted went into the bios and saw my link speed had gone from 100mbits to 10...then to 0.

I think i know why windows was crashing and trying to install "new hardwaRE" Because the hd was dying :( if i boot from anything but that HD everything works fine. i hope this helps some one who is having the same issue.

any further thoughts or feedback is welcome, thnx for your help

p.s the above link to "reinstall grub" met with no success..i was able to access the sdb5 from console but it showed a boot folder inside a boot folder:confused:

---

