---
title: "ubuntu 10.04 not listed in grub2 after windows installation"
date: 2011-07-22
forum: General Help
---

### Post by elingeniero on 2011-07-22
Hi I'm new here :)

I just started using Linux, I have no idea why I didn't use it before! the  things you can do with the system are amazing compared to 'other systems' (although I don't know much!). i will stop ranting now :P

here is how I got the problem described in the title:

i was dual booting windows 7 and ubuntu 10.04 with grub2 as the boot loader then I had to reinstall windows because of some issues, during the installation I had to DELETE the partition windows was installed on then create a new one, this was the ONLY Primary partition in the hd and it was the partition grub2 installed on.

After the installation finished, i loaded an ubuntu live cd and reinstalled grub2 using the graphical tool "boot-repair", it worked and windows 7 appears on the list but ubuntu does not!. I tried *sudo update-grub2* (found a tutorial to make this command work in Live CD) but the problem still exists. I also tried booting using the command line (*set root=(hd0,1)*....etc) but it doesn't work, windows boots when the value is set to 1 but when I try 2 I get an error.

I have a few questions:

Is there a way to verify that the ubuntu installation is still working and how can I make it appear on grub2 if it's still working. 

As I said the deleted windows partition was the only Primary partition and the / & /boot & /home & swap were all logical, do I need to set / partition to be Primary in the installation?

part of fdisk -l:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c6c2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6686    53705263+   7  HPFS/NTFS
/dev/sda2            6687        9730    24438785    5  Extended
/dev/sda5            6687        6719      250880   83  Linux
/dev/sda6            6719        8907    17576960   83  Linux
/dev/sda7            8907        9150     1951744   82  Linux swap / Solaris
/dev/sda8            9150        9730     4656128   83  Linux

```[I]
P.S I don't have anything installed on ubuntu so installing it again will solve everything but I really don't want to do this every time I face a problem (did it 4 or 5 times this week!!)[/I]

---

### Post by elingeniero on 2011-07-22
I also tried reinstalling grub by running some commands in the terminal, it works but ubuntu doesn't appear as before...

---

### Post by Quackers on 2011-07-22
Which commands did you use to re-install grub? Which partition did you mount first?

Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
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

### Post by elingeniero on 2011-07-22
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.
 => FreeDOS (eXtended FDisk) is installed in the MBR of /dev/sdc.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda5 and looks at sector 117486152 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files:        /IO.SYS /MSDOS.SYS /COMMAND.COM

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........D.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 1612504 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   107,410,589   107,410,527   7 NTFS / exFAT / HPFS
/dev/sda2         107,423,742   156,301,311    48,877,570   5 Extended
/dev/sda5         107,423,744   107,925,503       501,760  83 Linux
/dev/sda6         107,927,552   143,081,471    35,153,920  83 Linux
/dev/sda7         143,083,520   146,987,007     3,903,488  82 Linux swap / Solaris
/dev/sda8         146,989,056   156,301,311     9,312,256  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS
/dev/sdb2         976,768,065 1,953,520,064   976,752,000   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63       128,519       128,457  de Dell Utility
/dev/sdc2    *        128,520   254,855,159   254,726,640   7 NTFS / exFAT / HPFS
/dev/sdc3         465,290,595   488,279,137    22,988,543   7 NTFS / exFAT / HPFS
/dev/sdc4         254,855,160   465,290,594   210,435,435   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 4059 MB, 4059561984 bytes
255 heads, 63 sectors/track, 493 cylinders, total 7928832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *            128     7,928,831     7,928,704   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        EC4612584612243C                       ntfs       
/dev/sda5        b6cc8248-e828-4d49-b199-5f366d5bbee8   ext2       
/dev/sda6        c22bba40-a5e0-43dd-a0a7-90ba5c67801b   ext4       
/dev/sda7        1e4828ed-77fc-40df-b2b5-d748e3d9892e   swap       
/dev/sda8        53fce306-fc40-4533-acac-e80fff21d000   ext4       
/dev/sdb1        58380C7E6634CF88                       ntfs       
/dev/sdb2        29374CC2238AB313                       ntfs       
/dev/sdc1        07D5-0604                              vfat       DellUtility
/dev/sdc2        02E02243E0223CF3                       ntfs       
/dev/sdc3        01C8A32D0141BB80                       ntfs       
/dev/sdc4        01C902B82D0F8680                       ntfs       
/dev/sdd1        D45C-195B                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr0         /media/CD_ROM            iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


============================= sda5/grub/grub.cfg: ==============================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set c22bba40-a5e0-43dd-a0a7-90ba5c67801b
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
search --no-floppy --fs-uuid --set b6cc8248-e828-4d49-b199-5f366d5bbee8
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set c22bba40-a5e0-43dd-a0a7-90ba5c67801b
insmod tga
if background_image /usr/share/images/desktop-base/libyanflag444444.tga ; then
  set color_normal=white/black
  set color_highlight=yellow/blue
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6cc8248-e828-4d49-b199-5f366d5bbee8
    linux    /vmlinuz-2.6.32-33-generic root=UUID=c22bba40-a5e0-43dd-a0a7-90ba5c67801b ro   quiet splash
    initrd    /initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6cc8248-e828-4d49-b199-5f366d5bbee8
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /vmlinuz-2.6.32-33-generic root=UUID=c22bba40-a5e0-43dd-a0a7-90ba5c67801b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6cc8248-e828-4d49-b199-5f366d5bbee8
    linux    /vmlinuz-2.6.32-28-generic root=UUID=c22bba40-a5e0-43dd-a0a7-90ba5c67801b ro   quiet splash
    initrd    /initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6cc8248-e828-4d49-b199-5f366d5bbee8
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /vmlinuz-2.6.32-28-generic root=UUID=c22bba40-a5e0-43dd-a0a7-90ba5c67801b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6cc8248-e828-4d49-b199-5f366d5bbee8
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6cc8248-e828-4d49-b199-5f366d5bbee8
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 30B4BB0AB4BAD218
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  51.286850929 = 55.068836864   boot/grub/core.img                             2
  51.304270744 = 55.087541248   grub/core.img                                  2
  51.305494308 = 55.088855040   grub/grub.cfg                                  1
  51.251626015 = 55.031014400   initrd.img-2.6.32-28-generic                  35
  51.273592949 = 55.054601216   initrd.img-2.6.32-33-generic                  34
  51.234262466 = 55.012370432   vmlinuz-2.6.32-28-generic                     19
  51.235119820 = 55.013291008   vmlinuz-2.6.32-33-generic                     18

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set c22bba40-a5e0-43dd-a0a7-90ba5c67801b
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set c22bba40-a5e0-43dd-a0a7-90ba5c67801b
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
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set c22bba40-a5e0-43dd-a0a7-90ba5c67801b
insmod tga
if background_image /usr/share/images/desktop-base/libyanflag444444.tga ; then
  set color_normal=white/black
  set color_highlight=yellow/blue
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set EC4612584612243C
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
UUID=c22bba40-a5e0-43dd-a0a7-90ba5c67801b /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=b6cc8248-e828-4d49-b199-5f366d5bbee8 /boot           ext2    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=53fce306-fc40-4533-acac-e80fff21d000 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=1e4828ed-77fc-40df-b2b5-d748e3d9892e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  55.683082581 = 59.789254656   boot/grub/core.img                             1
  55.834968567 = 59.952340992   boot/grub/grub.cfg                             1

============================== sdd1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
--------------------------------------------------------------------------------

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  69 61 62 6c 65 49 62 45  45 45 45 4e 53 36 5f 49  |iableIbEEEENS6_I|
00000010  4e 53 35 5f 35 76 61 6c  75 65 49 69 45 45 45 45  |NS5_5valueIiEEEE|
00000020  53 45 5f 53 45 5f 53 45  5f 45 45 45 45 45 35 70  |SE_SE_SE_EEEEE5p|
00000030  61 72 73 65 49 4e 53 31  5f 37 73 63 61 6e 6e 65  |arseINS1_7scanne|
00000040  72 49 50 4b 63 4e 53 31  5f 31 36 73 63 61 6e 6e  |rIPKcNS1_16scann|
00000050  65 72 5f 70 6f 6c 69 63  69 65 73 49 4e 53 31 5f  |er_policiesINS1_|
00000060  31 36 69 74 65 72 61 74  69 6f 6e 5f 70 6f 6c 69  |16iteration_poli|
00000070  63 79 45 4e 53 31 5f 31  32 6d 61 74 63 68 5f 70  |cyENS1_12match_p|
00000080  6f 6c 69 63 79 45 4e 53  31 5f 31 33 61 63 74 69  |olicyENS1_13acti|
00000090  6f 6e 5f 70 6f 6c 69 63  79 45 45 45 45 45 45 45  |on_policyEEEEEEE|
000000a0  4e 53 31 5f 31 33 70 61  72 73 65 72 5f 72 65 73  |NS1_13parser_res|
000000b0  75 6c 74 49 53 53 5f 54  5f 45 34 74 79 70 65 45  |ultISS_T_E4typeE|
000000c0  52 4b 53 31 34 5f 00 5f  5a 4e 4b 35 62 6f 6f 73  |RKS14_._ZNK5boos|
000000d0  74 36 73 70 69 72 69 74  37 63 6c 61 73 73 69 63  |t6spirit7classic|
000000e0  36 61 63 74 69 6f 6e 49  4e 53 31 5f 35 63 68 6c  |6actionINS1_5chl|
000000f0  69 74 49 63 45 45 4e 37  70 68 6f 65 6e 69 78 35  |itIcEEN7phoenix5|
00000100  61 63 74 6f 72 49 4e 53  35 5f 39 63 6f 6d 70 6f  |actorINS5_9compo|
00000110  73 69 74 65 49 4e 53 5f  34 77 61 76 65 38 67 72  |siteINS_4wave8gr|
00000120  61 6d 6d 61 72 73 34 69  6d 70 6c 32 35 63 6f 6d  |ammars4impl25com|
00000130  70 6f 73 65 5f 63 68 61  72 61 63 74 65 72 5f 6c  |pose_character_l|
00000140  69 74 65 72 61 6c 45 4e  53 36 5f 49 4e 53 35 5f  |iteralENS6_INS5_|
00000150  31 34 63 6c 6f 73 75 72  65 5f 6d 65 6d 62 65 72  |14closure_member|
00000160  49 4c 69 30 45 4e 53 35  5f 37 63 6c 6f 73 75 72  |ILi0ENS5_7closur|
00000170  65 49 6a 62 4e 53 35 5f  35 6e 69 6c 5f 74 45 53  |eIjbNS5_5nil_tES|
00000180  45 5f 53 45 5f 53 45 5f  45 45 45 45 45 45 4e 53  |E_SE_SE_EEEEEENS|
00000190  36 5f 49 4e 53 43 5f 49  4c 69 31 45 53 46 5f 45  |6_INSC_ILi1ESF_E|
000001a0  45 45 45 4e 53 36 5f 49  4e 53 35 5f 38 76 61 72  |EEENS6_INS5_8var|
000001b0  69 61 62 6c 65 49 62 45  45 45 45 4e 53 36 00 fe  |iableIbEEEENS6..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 a8 07 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 a8  07 00 00 70 18 02 00 00  |...........p....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdc1

00000000  eb 46 90 44 65 6c 6c 20  34 2e 31 00 02 04 01 00  |.F.Dell 4.1.....|
00000010  02 00 02 00 00 f8 7e 00  3f 00 ff 00 3f 00 00 00  |......~.?...?...|
00000020  c9 f5 01 00 80 00 29 04  06 d5 07 44 65 6c 6c 55  |......)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  fa b8 00 00 8e d0 bc fc  |................|
00000050  7b fb fc 8e d8 81 3e 72  04 45 44 74 1d ff 0e 13  |{.....>r.EDt....|
00000060  04 8b 0e 13 04 c1 e1 06  8e c1 b9 00 01 33 f6 33  |.............3.3|
00000070  ff f3 66 a5 c7 06 72 04  45 44 8e c0 bd 00 7c e8  |..f...r.ED....|.|
00000080  21 01 0f 82 bb 00 66 0f  b7 86 16 00 66 d1 e0 66  |!.....f.....f..f|
00000090  0f b7 9e 0e 00 66 03 c3  66 03 86 1c 00 66 89 86  |.....f..f....f..|
000000a0  3e 00 8b 86 11 00 c1 e8  04 89 86 46 00 bb 00 05  |>..........F....|
000000b0  e8 aa 00 0f 82 8a 00 ba  10 00 b9 0b 00 be f2 7d  |...............}|
000000c0  8b fb f3 a6 74 16 83 c3  20 4a 75 ee 66 ff 86 3e  |....t... Ju.f..>|
000000d0  00 ff 8e 46 00 75 d6 be  e1 7d eb 6d 66 0f b7 86  |...F.u...}.mf...|
000000e0  11 00 66 ba 20 00 00 00  66 f7 e2 66 0f b7 8e 0b  |..f. ...f..f....|
000000f0  00 66 03 c1 66 48 66 f7  f1 66 01 86 3e 00 66 8b  |.f..fHf..f..>.f.|
00000100  86 3e 00 66 89 46 fc 66  0f b7 47 1a 8b f8 2d 02  |.>.f.F.f..G...-.|
00000110  00 66 0f b6 9e 0d 00 66  f7 e3 66 01 86 3e 00 bb  |.f.....f..f..>..|
00000120  00 07 c7 86 46 00 04 00  e8 32 00 72 14 81 c3 00  |....F....2.r....|
00000130  02 66 ff 86 3e 00 ff 8e  46 00 75 ec ea 00 02 70  |.f..>...F.u....p|
00000140  00 be d4 7d eb 03 be e1  7d e8 02 00 eb fe ac 3c  |...}....}......<|
00000150  00 74 09 b4 0e bb 07 00  cd 10 eb f2 c3 66 8b 86  |.t...........f..|
00000160  3e 00 66 33 d2 66 0f b7  8e 18 00 66 f7 f1 66 42  |>.f3.f.....f..fB|
00000170  88 96 45 00 66 33 d2 66  0f b7 8e 1a 00 66 f7 f1  |..E.f3.f.....f..|
00000180  88 96 44 00 89 86 42 00  b8 01 02 8b 8e 42 00 c0  |..D...B......B..|
00000190  e5 06 0a ae 45 00 86 e9  8a b6 44 00 8a 96 24 00  |....E.....D...$.|
000001a0  cd 13 c3 80 3e c2 07 06  74 29 b8 01 02 bb 00 06  |....>...t)......|
000001b0  b9 01 00 b6 00 8a 96 24  00 cd 13 72 16 c6 06 c2  |.......$...r....|
000001c0  07 06 b8 01 03 bb 00 06  b9 01 00 b6 00 8a 96 24  |...............$|
000001d0  00 cd 13 c3 44 69 73 6b  20 65 72 72 6f 72 0d 0a  |....Disk error..|
000001e0  00 4d 69 73 73 69 6e 67  20 6c 6f 61 64 65 72 0d  |.Missing loader.|
000001f0  0a 00 49 4f 20 20 20 20  20 20 53 59 53 00 55 aa  |..IO      SYS.U.|
00000200



```Thanks for the quick reply, sdb & sdc are *not* related, they are old hard drives used for storage only, they weren't formatted properly, that's why they have traces of windows xp and 7!

I first used boot-repair then I used this command

```
sudo mount /dev/sdXY /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sdX
```I mounted the root partition (sda6)

---

### Post by Quackers on 2011-07-22
All seems to be in order except that sda5, which is your boot partition, seems to have too many boot files (or more than normal anyway).
I would suggest that you boot from the live cd/usb and select "try Ubuntu" and then connect to the internet.
Then follow the guide below to purge then re-install grub to your system.
Please note that as you have a separate boot partition the instructions are slightly different in that you need to mount /dev/sda5 and /dev/sda6, as described in the CHROOT section Part A. The last command is also different for your system, at section 7.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by elingeniero on 2011-07-22
Worked like a charm

Thanks a lot.

---

