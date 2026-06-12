---
title: "GRUB - Cannot start Win XP after new installation of UBUNTU 10.10"
date: 2011-01-26
forum: General Help
---

### Post by Strolchi on 2011-01-26
Hallo experts,
I finally installed successfully UBUNTU 10.10, but now I have no access to Win XP with all my data, mail etc.

Please help.

[B]BR

Strolchi

[/B]

---

### Post by oldfred on 2011-01-26
First from Ubuntu try this:

sudo  update-grub

If no windows is shown then run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by madashell on 2011-01-27
hi Im new and as innocent as a newborn when it comes to Linux but after having a positive experience running a previous version of Ubuntu (8:10) I thought it may be nice to update to a more recent version so I obtained the CD version of Ubuntu 10:10 Maverick Meerkat
My main OS is Windows XP Professional (SP3) and I installed and ran 8:10 as a programme within windows, unfortunately when I tried to do the same with 10:10 I had a problem so decided to install on boot-up using the option to run both OS side-by-side.
Now I have lost the option on boot-up to select which OS I want to use! It automatically goes straight into the login page for the Ubuntu there is no sign of WinXP
so PLEASE Help!
I have read the previous response and am going to find and post the results report as suggested and hopefully some kind soul will help me resolve my problem because I am desperate :( I have personal files on Windows I just can NOT lose! its only 4 days since I put all my grand-daughters first birthday pictures and film on there!
as soon as I work out how to generate the results report thing I will post it.....
here's hoping 
Guy

---

### Post by madashell on 2011-01-27
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   105,172,513   105,172,451   7 HPFS/NTFS
/dev/sdc2         105,172,990   156,296,384    51,123,395   f W95 Ext d (LBA)
/dev/sdc5         124,792,983   156,296,384    31,503,402   7 HPFS/NTFS
/dev/sdc6         105,172,992   123,858,943    18,685,952  83 Linux
/dev/sdc7         123,860,992   124,792,831       931,840  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1024252124250AF4                       ntfs       Ayshea                        
/dev/sda                                                nvidia_raid_member                               
/dev/sdc1        3A6478AC64786C8F                       ntfs       Christopher                   
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        E298535898532A75                       ntfs       Caitlin                       
/dev/sdc6        6b8d583d-0135-40ee-9b61-bbee6229bfcf   ext4                                     
/dev/sdc7        ed133039-97ca-41e2-bd1c-c5e683cd3422   swap                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/Ayshea            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf ro single 
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
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

=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc7 during installation
UUID=ed133039-97ca-41e2-bd1c-c5e683cd3422 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc6: Location of files loaded by Grub: ===================


  61.2GB: boot/grub/core.img
  56.4GB: boot/grub/grub.cfg
  55.3GB: boot/initrd.img-2.6.35-22-generic
  55.2GB: boot/initrd.img-2.6.35-24-generic
  61.2GB: boot/vmlinuz-2.6.35-22-generic
  61.3GB: boot/vmlinuz-2.6.35-24-generic
  55.2GB: initrd.img
  55.3GB: initrd.img.old
  61.3GB: vmlinuz
  61.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  eb 06 00 00 00 00 00 00  33 c0 fa 8e d0 bc 00 7c  |........3......||
00000010  fb 8e d8 8b f4 8e c0 bf  26 7e 06 57 bf 00 7e b9  |........&~.W..~.|
00000020  00 02 fc f3 a4 cb be 02  7e ad 8b c8 66 ad bb 00  |........~...f...|
00000030  80 83 f9 00 75 2e be be  7f ac 3c 80 74 1b 83 c6  |....u.....<.t...|
00000040  0f 81 fe fe 7f 75 f2 be  44 7f e8 33 00 be 92 7f  |.....u..D..3....|
00000050  e8 2d 00 33 c0 cd 16 cd  19 83 c6 07 66 ad b9 01  |.-.3........f...|
00000060  00 bb 00 7c 32 f6 e8 24  00 be 62 7f 72 dc 8b f3  |...|2..$..b.r...|
00000070  81 c6 fe 01 ad be 7f 7f  3d 55 aa 75 cd 06 53 cb  |........=U.u..S.|
00000080  b4 0e fc ac 3c 00 74 04  cd 10 eb f7 c3 66 60 1e  |....<.t......f`.|
00000090  06 66 50 53 51 52 8b ec  b4 41 bb aa 55 8a 56 00  |.fPSQR...A..U.V.|
000000a0  cd 13 72 39 81 fb 55 aa  75 33 f6 c1 01 74 2e 66  |..r9..U.u3...t.f|
000000b0  33 c0 66 50 66 8b 46 06  66 50 8b 46 0a 50 8b 46  |3.fPf.F.fP.F.P.F|
000000c0  04 50 66 b8 10 00 01 00  66 50 16 1f 8b f4 8b 56  |.Pf.....fP.....V|
000000d0  00 b8 00 42 02 e6 cd 13  83 c4 10 eb 50 b4 08 8a  |...B........P...|
000000e0  56 00 33 ff 8e c7 cd 13  72 43 66 83 e1 3f fe c6  |V.3.....rCf..?..|
000000f0  8a de 66 8b 46 06 66 33  d2 66 f7 f1 42 52 8a cb  |..f.F.f3.f..BR..|
00000100  66 33 d2 66 f7 f1 8a f2  59 66 3d ff 03 00 00 77  |f3.f....Yf=....w|
00000110  1b 86 e0 c0 e0 06 03 c8  8e 46 0a 8b 5e 04 8b 46  |.........F..^..F|
00000120  00 8a d0 80 c4 02 b0 01  cd 13 eb 01 f9 5a 59 5b  |.............ZY[|
00000130  66 58 72 0b 81 c3 00 02  66 40 49 0f 85 52 ff 07  |fXr.....f@I..R..|
00000140  1f 66 61 c3 0d 0a 41 63  74 69 76 65 20 70 61 72  |.fa...Active par|
00000150  74 69 74 69 6f 6e 20 6e  6f 74 20 66 6f 75 6e 64  |tition not found|
00000160  21 00 0d 0a 45 72 72 6f  72 20 72 65 61 64 69 6e  |!...Error readin|
00000170  67 20 62 6f 6f 74 20 73  65 63 74 6f 72 21 00 0d  |g boot sector!..|
00000180  0a 42 61 64 20 62 6f 6f  74 20 73 65 63 74 6f 72  |.Bad boot sector|
00000190  21 00 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |!...Press any ke|
000001a0  79 2e 2e 2e 0d 0a 00 00  00 00 00 00 00 00 00 00  |y...............|
000001b0  00 00 00 00 00 00 00 00  18 9d c2 3c 00 00 80 01  |...........<....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 e3 cd 44 06 00 fe  |......?.....D...|
000001d0  ff ff 0f fe ff ff fe cf  44 06 c3 14 0c 03 00 00  |........D.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by madashell on 2011-01-27
as requested and promised here is my post
I do hope that I have followed the instructions correctly?
and also it will provide the infomation required to help me fix my problem!?
many thanks in anticipation
Guy

---

### Post by drs305 on 2011-01-27
madashell,

So I guess you are able to get into a normally-running Ubuntu without problems?

First, have you tried running:
```
sudo update-grub
```
That should force Grub2 to search for the Windows OS.

Second, Grub is installed on sda but not on your Ubuntu drive, sdc. While this can work, it's probably advisable to install G2 onto the MBR of sdc as well:
```
sudo grub-install /dev/sdc
sudo update-grub # Just for good measure
```

If you reboot after doing the two items above, if it still doesn't find Windows, try changing the boot order to boot your sdc drive first. Once you have the BIOS boot to the Ubuntu drive first, we can reinstate the Windows bootloader on the Windows drive if necessary.

---

### Post by madashell on 2011-01-27
many thanks for the speedy response!
ok first it appears that the version of Ubuntu (10:10) that I installed is working perfectly, it has only been less than 24 hours but I have had no problems at all. I am very pleased with it.

I tried the "sudo update-grub" approach and could see nothing that mentioned Windows

Im sorry to admit that this:-
"Second, Grub is installed on sda but not on your Ubuntu drive, sdc.  While this can work, it's probably advisable to install G2 onto the MBR  of sdc as well:
     Code:
sudo grub-install /dev/sdc
sudo update-grub # Just for good measure"
didn't have a great deal of meaning for me, but I did input the codes and rebooted but it still immediately went into the Ubuntu login screen (NO Windows option)

I know how to change the boot order in BIOS but I have no idea what my SDC drive is? or for that matter SDA? Please remember I am a novice with doing things for myself.I have been seduced by microsoft for a longggg time LOL

---

### Post by drs305 on 2011-01-27
> **madashell said:**
> I know how to change the boot order in BIOS but I have no idea what my SDC drive is? or for that matter SDA? Please remember I am a novice with doing things for myself.I have been seduced by microsoft for a longggg time LOL

You can look in BIOS and see the order the drives are listed; this usually translates in Linux terms into sda for the first drive listed, sdb for the second drive, etc.  You can also confirm which is which by looking at the drive sizes reported in BIOS.

Once you have determined which drive contains your Ubuntu installation you should change the BIOS boot order so the Ubuntu drive is listed first.

Then reboot, and run the "sudo update-grub" command once more. You can tell if G2 found Windows by watching the command run in terminal. If it finds it Windows will be mentioned on one of the terminal lines as the command is executed.

If you still have problems finding Windows, run and post the contents of RESULTS.txt once more.  It will show us all your partitions and the revised state of your boot files:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by madashell on 2011-01-27
I think I should have created a new results report to reflect any changes I had created so here it is........... another small step on the road to recovery I hope!


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   105,172,513   105,172,451   7 HPFS/NTFS
/dev/sdc2         105,172,990   156,296,384    51,123,395   f W95 Ext d (LBA)
/dev/sdc5         124,792,983   156,296,384    31,503,402   7 HPFS/NTFS
/dev/sdc6         105,172,992   123,858,943    18,685,952  83 Linux
/dev/sdc7         123,860,992   124,792,831       931,840  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1024252124250AF4                       ntfs       Ayshea                        
/dev/sda                                                nvidia_raid_member                               
/dev/sdc1        3A6478AC64786C8F                       ntfs       Christopher                   
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        E298535898532A75                       ntfs       Caitlin                       
/dev/sdc6        6b8d583d-0135-40ee-9b61-bbee6229bfcf   ext4                                     
/dev/sdc7        ed133039-97ca-41e2-bd1c-c5e683cd3422   swap                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/Ayshea            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/Christopher       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /media/Caitlin           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf ro single 
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
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

=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc7 during installation
UUID=ed133039-97ca-41e2-bd1c-c5e683cd3422 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc6: Location of files loaded by Grub: ===================


  60.4GB: boot/grub/core.img
  56.4GB: boot/grub/grub.cfg
  55.3GB: boot/initrd.img-2.6.35-22-generic
  55.2GB: boot/initrd.img-2.6.35-24-generic
  61.2GB: boot/vmlinuz-2.6.35-22-generic
  61.3GB: boot/vmlinuz-2.6.35-24-generic
  55.2GB: initrd.img
  55.3GB: initrd.img.old
  61.3GB: vmlinuz
  61.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by drs305 on 2011-01-27
We posted about the same time, so I will add one more thing to try. After booting into your normal Ubuntu OS, try running:
```
sudo os-prober
```
See if that command works. The section of your Grub menu file includes some boilerplate but nothing about Windows. Let's make sure the command which would place Windows in the menu is working.

---

### Post by oldfred on 2011-01-27
I first thought it was strange that the script did not see sdb, but it has this:
/dev/sda                     nvidia_raid_member 

Is this hardware RAID or software, If software which with nvidia is sounds like:
Have you installed mdadm package:
#   Is able to search Linux Software Raid partitions (MD Raids) if
#       the "mdadm" package is installed.

Script works better with mdadm and perhaps that is why osprober is not seeing windows.

---

### Post by madashell on 2011-01-27
hi again!
 tried the code "sudo os-prober" and there is absolutely no information displayed?

---

### Post by madashell on 2011-01-27
> **oldfred said:**
> I first thought it was strange that the script did not see sdb, but it has this:
/dev/sda                     nvidia_raid_member 

Is this hardware RAID or software, If software which with nvidia is sounds like:
Have you installed mdadm package:
#   Is able to search Linux Software Raid partitions (MD Raids) if
#       the "mdadm" package is installed.

Script works better with mdadm and perhaps that is why osprober is not seeing windows.

  thanks for your input oldfred but I need a translation please, no offence meant! LOL
I dont know what RAID harware or software means, when I installed Ubuntu I automatically downloaded and installed a whole raft of updates, and I also allowed certain "recommended" nvidia drivers to be used (although I have no idea what!) but I did recall reading that some proprietary drivers are not open-source and therefore cannot be "tweaked" specifically for Linux, sorry if my language is not correct but I hope you understand my meaning?
os-prober is defininitely NOT seeing windows :(

---

### Post by kansasnoob on 2011-01-27
Maybe I'm just confused this AM :confused:

Are the users _Impact_, madashell, and Strolchi the same person?

I just happened to see comment #11 and, as I said, I'm confused :P

---

### Post by kansasnoob on 2011-01-27
Or maybe it's just a matter of multiple threads:

[http://ubuntuforums.org/showthread.php?t=1676055](http://ubuntuforums.org/showthread.php?t=1676055)

But somehow I keep ending up back here:

[http://ubuntuforums.org/showthread.php?t=1675301](http://ubuntuforums.org/showthread.php?t=1675301)

Maybe I need a second pot of coffee :confused:

---

### Post by Elfy on 2011-01-27
Closed.

Strolchi - please do not post duplicate threads.

madashell - please do not hijack threads - it is easy to confuse information for one person with another - while sometimes this does not matter - it could matter a great deal with grub.

---

