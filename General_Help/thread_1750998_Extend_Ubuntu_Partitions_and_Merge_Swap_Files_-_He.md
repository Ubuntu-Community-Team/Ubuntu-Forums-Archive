---
title: "Extend Ubuntu Partitions and Merge Swap Files - Help Needed"
date: 2011-05-06
forum: General Help
---

### Post by Crucias on 2011-05-06
Evening all, 

As you can see from the screenshot the free space for my Ubuntu install to extend into is before the Ubuntu partition in the partition tree.

This means i cannot just extend it normally. I also have 2 swap files for some reason (mu 9.10 and 11.04 fresh installs were given free rein to make their own so this is probably the issue). I have 8GB of ram but would like to fuse the 2 swap files so i can do lots of intensive loading.

I need to know how to fuse the swap partitions (more accurately how to delete them, repartition them, and relink them to Ubuntu) and also how to extend my Ubuntu backwards without breaking my Win7 install or Ubuntu install (or Burg).

I checked some tutorials and googled but none could really help me. 

Ubuntu 11.04 x64
Windows 7 x64

Screenshot attached.

------------

Thanks for your help in advance!

>>EDIT<<

Would it be easier to copy my Ubuntu partition to an external HDD, then wipe the partitions, re-part from LiveCD then copy it back over and make it bootable? If so how? Guides i can find are antiquated

---

### Post by An Sanct on 2011-05-06
For the swap files, use a Live CD or USB and merge them with gparted.

When you run gparted, you will have to swap-off both, then delete one and resize the other to fill its place.

Also note, that you maybe will have to manually edit fstab (!) and enter the correct swap information into it. Besides, if in fstab both swaps are listed, this means, bot are used. This is a problem only if you want to use hibernation, since the swap has to be continuous, for that to work correctly.

a sample fstab, located in /etc/fstab
```

#swap
UUID=59f2*****your own UUID!********39 none            swap    sw              0       0

```I cannot provide help with the windows partition resizing, its slightly more complicated.

---

### Post by Crucias on 2011-05-06
That would explain why my Hibernate is really a Shut Down. So GPart off a liveCD to fix the swap. below is my fstab. So the top Swap is where my active one goes, so i'd just copy the gparted information UUID and paste it there?

```
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid                0  0  
# / was on /dev/sda8 during installation
UUID=a59046be-9ffe-4c79-9721-59a80365bba7  /               ext4  errors=remount-ro                  0  1  
# swap was on /dev/sda9 during installation
UUID=f93bffbd-f960-45f7-8ffe-9f70738325fa  none            swap  sw                                 0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8           0  0  
/dev/sda1                                  /media/sda1     ntfs  nls=iso8859-1,umask=000            0  0  
/dev/sdc1                                  /media/sdc1     ntfs  nls=iso8859-1,ro,noauto,umask=000  0  0  
/dev/sda5                                  /media/sda5     ntfs  nls=iso8859-1,umask=000            0  0  
/dev/sda8                                  /media/sda8     swap  defaults                           0  0  
/dev/sdb1                                  /media/sdb1     ntfs  nls=iso8859-1,umask=000            0  0  
```

---

### Post by An Sanct on 2011-05-06
Yes, get the info of the UUID in gparted with a right click on the partition and selecting "information".

Sample screenshot attached -  note the UUID part, replace the fstab data with that info after you merge the swaps.

---

### Post by Crucias on 2011-05-06
Sounds simple enough. My only problem now is the resizing. 

My problem is confusion, Easeus partition manager only lets you grow partitions on the left into space on the right. The GParted tutorials i read contradict each other, some say you can grow left, some right, and some say both.

I also need to know how to resolve any potential boot problems. If i move Ubuntu will it prevent Burg loading it? Or will it maintain its UUID and still load

---

### Post by An Sanct on 2011-05-06
1. In gparted, you can grow to where you have space (see screenshot and note the arrows on the left and right - also free space "*preceding*" and "*following*")

2. I have 0 knowledge about Burg, the only thing I know is, that it is a Grub alternative ... so, giving advice about this, would be ... well :) not good ;)

UUIDs are good, also, make sure that the swap you remove is no longer in fstab.

AFAIK: swaps have nothing to do with booting, so they are ignored by boot loaders ...

---

### Post by Crucias on 2011-05-06
When i fiddle with the partitions Win7 will not load but i can chuck in the DVD and fix that instantly. 

Im worried that when i resize Ubuntu i will be unable to boot because the physical location of Grub (or burg) will move with the Ubuntu partition.

Would grub just boot normally, or would i have to reinstall it from live CD? (and we can pretend i have Grub, i can always restore Grub till i make the change)

---

### Post by An Sanct on 2011-05-06
Assuming, that the boot loader is on SDA1, then there are no changes to that location (boot sector)

Or did I miss something? :)

Well, anyway, its always good to have a Live CD/USB ready, if the boot loader breaks, you can renew it from there.

Where is burg located right now? (there was a script on this forum, that gives all the needed info ... from Ruby2600, Ill try to find it)

edit: Found it ... [boot info script]("http://bootinfoscript.sourceforge.net/") download it, make sure it is bootable and run it as sudo, post the text file (I think its results.txt on the desktop or in the same folder ...) here.

---

### Post by Crucias on 2011-05-06
Sorry it took me so long, it was well past midnight on your last reply. Right i got it running and the file is attached. Grub is on sda6 the same as Ubuntu

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/burg.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *             63   156,366,205   156,366,143   7 HPFS/NTFS
/dev/sda2         156,376,771 1,953,520,064 1,797,143,294   f W95 Ext d (LBA)
/dev/sda5         156,376,773 1,795,328,009 1,638,951,237   7 HPFS/NTFS
/dev/sda6       1,847,861,248 1,928,742,911    80,881,664  83 Linux
/dev/sda7       1,928,744,960 1,945,518,079    16,773,120  82 Linux swap / Solaris
/dev/sda8       1,945,519,758 1,953,520,064     8,000,307  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   312,578,047   312,576,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        384A052C4A04E888                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5030A41430A3FEDA                       ntfs       Main Disk                     
/dev/sda6        a59046be-9ffe-4c79-9721-59a80365bba7   ext4                                     
/dev/sda7        f93bffbd-f960-45f7-8ffe-9f70738325fa   swap                                     
/dev/sda8        f1eb59cc-90d1-42dd-beeb-19e9dc75de2b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        124AA0D04AA0B1C1                       ntfs       Secondary Disk                
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        42EECCD7EECCC3FF                       ntfs       External                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/sda1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/sda5              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/sdb1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/External          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="4"
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
search --no-floppy --fs-uuid --set=root a59046be-9ffe-4c79-9721-59a80365bba7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root a59046be-9ffe-4c79-9721-59a80365bba7
set locale_dir=($root)/boot/grub/locale
set lang=en_NZ
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
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
	search --no-floppy --fs-uuid --set=root a59046be-9ffe-4c79-9721-59a80365bba7
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a59046be-9ffe-4c79-9721-59a80365bba7 ro  splash vga=795  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a59046be-9ffe-4c79-9721-59a80365bba7
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a59046be-9ffe-4c79-9721-59a80365bba7 ro single  splash vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a59046be-9ffe-4c79-9721-59a80365bba7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a59046be-9ffe-4c79-9721-59a80365bba7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 384A052C4A04E888
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid                0  0  
# / was on /dev/sda8 during installation
UUID=a59046be-9ffe-4c79-9721-59a80365bba7  /               ext4  errors=remount-ro                  0  1  
# swap was on /dev/sda9 during installation
UUID=f93bffbd-f960-45f7-8ffe-9f70738325fa  none            swap  sw                                 0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8           0  0  
/dev/sda1                                  /media/sda1     ntfs  nls=iso8859-1,umask=000            0  0  
#/dev/sdc1                                  /media/sdc1     ntfs  nls=iso8859-1,ro,noauto,umask=000  0  0  
/dev/sda5                                  /media/sda5     ntfs  nls=iso8859-1,umask=000            0  0  
/dev/sda8                                  /media/sda8     swap  defaults                           0  0  
/dev/sdb1                                  /media/sdb1     ntfs  nls=iso8859-1,umask=000            0  0  

=================== sda6: Location of files loaded by Grub: ===================


 976.4GB: boot/grub/core.img
 978.6GB: boot/grub/grub.cfg
 947.4GB: boot/initrd.img-2.6.38-8-generic
 976.4GB: boot/vmlinuz-2.6.38-8-generic
 947.4GB: initrd.img
 976.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  94 56 8c bd b8 b2 be 74  8c 42 42 42 42 46 42 77  |.V.....t.BBBBFBw|
00000010  8c 57 8c e4 b8 29 fa 14  94 57 8c 88 af 1f 3f 14  |.W...)...W....?.|
00000020  94 57 8c a1 1d b7 b8 77  8c 57 8c 48 ef c9 40 77  |.W.....w.W.H..@w|
00000030  8c 57 8c c2 c1 e9 64 77  8c 54 8c ea e8 e2 c2 14  |.W....dw.T......|
00000040  94 57 8c fd bd bd bd 42  42 57 8c 17 17 57 17 14  |.W.....BBW...W..|
00000050  94 57 8c bd b7 bf b9 14  94 b6 87 30 38 30 b0 d5  |.W.........080..|
00000060  94 57 8c f7 ef 17 97 15  94 77 8c ec 38 97 b7 57  |.W.......w..8..W|
00000070  94 14 8c fd bd bd bd 14  94 57 8c 3d 3d 3d e8 77  |.........W.===.w|
00000080  8c b7 8f fc e9 e8 ea 57  8c 74 8c 68 e8 68 e8 42  |.......W.t.h.h.B|
00000090  42 74 8c 17 17 13 17 77  8c 57 8c e8 f8 a9 9f 74  |Bt.....w.W.....t|
000000a0  8c 57 8c 42 aa b1 80 77  8c 57 8c e8 ab e9 a9 74  |.W.B...w.W.....t|
000000b0  8c 57 8c 9d f5 b7 3c 74  8c 57 8c 1d bc bd 37 57  |.W....<t.W....7W|
000000c0  8c b6 87 c2 6a 68 6c 74  8c 57 8c 77 9d bd ed 74  |....jhlt.W.w...t|
000000d0  8c 57 8c 8e 2e 39 98 42  42 74 8c 17 17 13 17 74  |.W...9.BBt.....t|
000000e0  8c 57 8c 94 95 97 b7 77  8c 57 8c 38 e9 e8 e8 77  |.W.....w.W.8...w|
000000f0  8c 54 8c c1 c0 e0 c8 77  8c 57 8c e8 a8 b8 b4 14  |.T.....w.W......|
00000100  94 57 8c 7d 4b 89 b0 14  94 b6 87 ba fc 48 40 77  |.W.}K........H@w|
00000110  8c b6 87 fd ea 4a 42 42  42 74 8c 17 17 57 17 77  |.....JBBBt...W.w|
00000120  8c 57 8c f4 a5 2c 68 14  94 b6 87 b9 6d 4d 6d 74  |.W...,h.....mMmt|
00000130  8c 91 87 e2 9a 9e 60 74  8c b6 87 49 ab 40 ea 74  |......`t...I.@.t|
00000140  8c 96 87 b2 ba 1a ba 77  8c 96 87 41 ef 4b 4b 74  |.......w...A.KKt|
00000150  8c 57 8c c2 6a fe 6a 77  8c 54 8c e8 e2 ea 68 42  |.W..j.jw.T....hB|
00000160  42 14 94 17 17 57 17 14  94 77 8c 9d b7 ef a7 15  |B....W...w......|
00000170  94 77 8c bd bd bd b5 77  94 74 8c b5 bd bd bd 14  |.w.....w.t......|
00000180  94 57 8c fd bd bd fd 74  94 77 8c b5 b5 b7 bd 14  |.W.....t.w......|
00000190  8c 57 8c e8 b8 9c fc 14  94 57 8c bc bd b7 a9 14  |.W.......W......|
000001a0  94 77 8c bf bd 97 b7 14  94 42 42 42 42 02 42 14  |.w.......BBBB.B.|
000001b0  94 57 8c cd ad b5 f5 74  8c 57 8c 64 4c ca 00 fe  |.W.....t.W.dL...|
000001c0  ff ff 07 fe ff ff 02 00  00 00 45 69 b0 61 00 fe  |..........Ei.a..|
000001d0  ff ff 05 fe ff ff 8d fe  d1 64 b0 2a d2 04 00 00  |.........d.*....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by An Sanct on 2011-05-08
Okay, I looked through the results and as far as I can see, it should be no problem to merge the two swaps.

It should also be okay to move the Ubuntu partition. I cannot provide any help about the NTFS partitions tho. Please create another thread and retry. Some people don't even click posts with 4 and more entries.

Also paste the contents of results.txt in a *code section* (the # button above), since people have to be logged in to see attached files.

---

### Post by Crucias on 2011-05-09
Ok i did it tonight (goddamn it's almost impossible to get gparted working live, went through 5 recommended programs to make a live USB and ended up making a CD)

I deleted and moved the 8.6GB Swap right, and extended Ubuntu to fill the rest of the space (left and now vacated right) and it worked smoothly. Even better i loaded the PC and burg started, then Ubuntu started and to my sweet sweet joy everything works.

Haven't tested Win7 now but im betting it will not work (because windows never works), however it may because i didn't alter the win bootloader or the sda1 partition. Here's hoping!

Thanks for all the help!

---

### Post by An Sanct on 2011-05-09
Your welcome!

Please mark the thread as solved (under thread tools)

---

