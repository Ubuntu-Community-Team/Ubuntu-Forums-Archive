---
title: "Quad Boot?"
date: 2010-11-03
forum: General Help
---

### Post by frank cox on 2010-11-03
I have 2 drives, one dual boots XP and Ubuntu 9.04 which I intend to replace with 10.4 or perhaps some other Linux Distro in time and the on the other  dual boots Mint Isadora and Xubuntu 10.10 mostly for demonstration purposes .

Everything works fine, I can boot the first drive with Ubuntu 9.04 and access the other linux drives and all the data, i can boot XP ,  but what I can't do is boot off one of the Linux distros on the second drive without switching the sata cables and making drive 2 drive 1 .
Is there a way to put all 4 distros in the Grub on the first drive and select between all 4 at boot up? Actually I would like to add a few more Linux Distros to drive 2 to show customers I talk out of reinstalling windows what choices are available and to play with them myself.

If this is not reasonable or feasible is there such a thing as a switch that would allow me to choose which drive to boot without opening the case?

---

### Post by sikander3786 on 2010-11-03
Boot into Ubuntu or Xubuntu, whichever drive you wish to keep as the first bootable device and from terminal, run

```
sudo update-grub
```

That should be enough to sort out everything.

---

### Post by frank cox on 2010-11-04
> **sikander3786 said:**
> Boot into Ubuntu or Xubuntu, whichever drive you wish to keep as the first bootable device and from terminal, run

```
sudo update-grub
```That should be enough to sort out everything.

Thanks, I thought about that but fixing Grub when it forgets where windows is can be a pain. Will let you know how it went.
Thanks

---

### Post by frank cox on 2010-11-04
It did nothing for the first drive as far as accessing the second but I remembered that you could switch hard drives by hitting f12 and that allowed me to boot the second easy enough but the second  did not give me the option of booting off the first drive but the first drive did show up in computer so I can access if ,

Not sure if it is worth the trouble but if anyone knows how to get grub to list all the OS's on both drives from drive 1  I would appreciate it. As it is it does every thing I need it to really, just greedy I guess.:}

I imagine I have to tell the OS's on the second drive that Grub is on the first but I don't know how.
If it is real likely to leave me unable to boot at all I will probably leave well enough alone, 

It is a good deal the bios lets you easily choose which drive to boot because there is no such animal as a sata drive switch I can find other than one that shuts off the power which would not help at all and those are very expensive . 

There is a cool way to do it with IDE drives if your bios dose not support a quick selection, run LED wires from the jumpers and wire in a switch to change master to slave. Of course you have to power down.

---

### Post by sikander3786 on 2010-11-04
It is Ubuntu 9.04 on the 1st drive and it has got Grub Legacy by default, not Grub2 and the above command is intended for Grub2. Sorry for that.

But from Xubuntu 10.10, you should be able to run it successfully. If you do it, please post the output so we can have a look it.

Yes you need to tell the Grub on 2nd drive that 1st drive also has got some installations + Grub and the above command is intended to do the same.

I don't remember anything helpful regarding Grub Legacy so I give up for your first drive.

---

### Post by frank cox on 2010-11-04
> **sikander3786 said:**
> It is Ubuntu 9.04 on the 1st drive and it has got Grub Legacy by default, not Grub2 and the above command is intended for Grub2. Sorry for that.

But from Xubuntu 10.10, you should be able to run it successfully. If you do it, please post the output so we can have a look it.

Yes you need to tell the Grub on 2nd drive that 1st drive also has got some installations + Grub and the above command is intended to do the same.

I don't remember anything helpful regarding Grub Legacy so I give up for your first drive.

I should have thought of that. Thanks

Here are  my concerns. The obvious one is that I could leave well enough alone at this point ,that the advantage of being able to call up all of the OS's on both drives  at once is minor. Being I am still a long way from being proficient at Grub  I may not be able to easily fix a screwup. And lastly  if I boot of the second hard drive will XP boot seeing it has lost the shotgun position Mr. Bill demands it has?

If it does not boot windows there is no point other than learning which of course is valid. Would it make sense to update the Grub on 9.04 {legacy}  to Grub 2? I don't recall reading a whole lot good about the new one but that may have been from from those still learning the ropes.

Thanks again for taking your irreplaceable time to help a stranger.

---

### Post by sikander3786 on 2010-11-04
It would be just better to add the entries in Xubuntu's grub. I believe and hope that it will not vanish your Windows entry. It actually shouldn't.

Upgrading to Grub2, well I don't see any advantages or disadvantages as support period for 9.04 is already ended. It would be better to upgrade it to the latest version or do a clean install with any of the newer version i.e, 10.10 or 10.04 and they already come with Grub2.

Open for further queries :-)

---

### Post by oldfred on 2010-11-04
I boot Ubuntu from either sdc7 (Lucid) or sdb2 (Maverick) and either lets me boot my XP install in sda1 without issue. 

I still have an old grub legacy partition which I used to boot everything but I had to manually add most new systems (Chainloading made that easier). The real advantage of grub2 is the osprober that finds just about everything and sets it up to boot. The old verison of osprober with 9.04 was at the very beginning of the grub2 updates and did not work all the time.

Anyone with multiple installs should run this before & after any system changes. One to document what you have just in case you need exact old partition layout and after to make sure you changed what you thought you changed.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by frank cox on 2010-11-04
This is after I ran the update command in legacy Grub and the next will be after I update Grub2

Thanks

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

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
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb8 starts at sector 422156133.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb9 starts at sector 626294088.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb10 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb10 starts at sector 833757498.
    Operating System:  
    Boot files/dirs:   

sdb11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009cd00

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    14,649,343    14,647,296  83 Linux
/dev/sda2          14,651,390   488,394,751   473,743,362   5 Extended
/dev/sda5         484,493,312   488,394,751     3,901,440  82 Linux swap / Solaris
/dev/sda6          14,651,392   152,005,763   137,354,372  83 Linux
/dev/sda7         289,181,696   484,489,215   195,307,520   b W95 FAT32
/dev/sda8         152,006,656   283,486,207   131,479,552  83 Linux
/dev/sda9         283,488,256   289,169,407     5,681,152  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4a034a03

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   116,599,769   116,599,707   7 HPFS/NTFS
/dev/sdb2         116,599,770   123,443,459     6,843,690  83 Linux
/dev/sdb3         123,443,460   976,768,064   853,324,605   5 Extended
/dev/sdb5         123,443,523   130,287,149     6,843,627  83 Linux
/dev/sdb6         130,287,213   390,829,319   260,542,107  83 Linux
/dev/sdb7         390,829,383   422,156,069    31,326,687  83 Linux
/dev/sdb8         422,156,133   626,294,024   204,137,892   b W95 FAT32
/dev/sdb9         626,294,088   833,757,434   207,463,347   b W95 FAT32
/dev/sdb10        833,757,498   970,904,339   137,146,842   b W95 FAT32
/dev/sdb11        970,904,403   976,768,064     5,863,662  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5031dd05-4336-4d94-a847-309f4ffbf8e4   ext4                                     
/dev/sda5        e9c80de9-4910-44a1-bd61-79488759f495   swap                                     
/dev/sda6        40e3f44b-3ed0-4f9d-ae9e-5d684e0d255c   ext4                                     
/dev/sda7        47A7-C218                              vfat                                     
/dev/sda8        524632f2-7b7e-4ef2-97f8-2200edf676b5   ext4                                     
/dev/sda9        dcb76c64-2f71-4def-8943-6dbabbae13d8   swap                                     
/dev/sdb10       4B5A-D514                              vfat       Dual-Use3                     
/dev/sdb11       3a09e702-45b7-4912-a829-fecb634126a2   swap                                     
/dev/sdb1        9EC8A2D0C8A2A64D                       ntfs                                     
/dev/sdb2        24305024-e76c-4ec6-9ecc-e7d64ca9550c   ext3                                     
/dev/sdb5        d3edce97-12f5-4878-8827-49b4f4c1609f   ext3                                     
/dev/sdb6        31ac9a84-03fb-4a45-898d-19db167e4c70   ext3                                     
/dev/sdb7        ab9fd6e0-c069-4dba-99d8-9c8dd3579667   ext3                                     
/dev/sdb8        4B5A-D509                              vfat       Dual-Use                      
/dev/sdb9        4B5A-D511                              vfat       Dual-Use-2                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb6        /home                    ext3       (rw,relatime)
/dev/sdb7        /usr                     ext3       (rw,relatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5031dd05-4336-4d94-a847-309f4ffbf8e4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5031dd05-4336-4d94-a847-309f4ffbf8e4 ro single 
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
    search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5031dd05-4336-4d94-a847-309f4ffbf8e4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=40e3f44b-3ed0-4f9d-ae9e-5d684e0d255c /home           ext4    defaults        0       2
/dev/sda7       /windows        vfat    utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.7GB: boot/grub/core.img
   2.9GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.35-22-generic
   2.9GB: boot/vmlinuz-2.6.35-22-generic
   1.5GB: initrd.img
   2.9GB: vmlinuz

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 524632f2-7b7e-4ef2-97f8-2200edf676b5
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 524632f2-7b7e-4ef2-97f8-2200edf676b5
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 524632f2-7b7e-4ef2-97f8-2200edf676b5
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda8)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 524632f2-7b7e-4ef2-97f8-2200edf676b5
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=524632f2-7b7e-4ef2-97f8-2200edf676b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda8) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 524632f2-7b7e-4ef2-97f8-2200edf676b5
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=524632f2-7b7e-4ef2-97f8-2200edf676b5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 524632f2-7b7e-4ef2-97f8-2200edf676b5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 524632f2-7b7e-4ef2-97f8-2200edf676b5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=5031dd05-4336-4d94-a847-309f4ffbf8e4 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=5031dd05-4336-4d94-a847-309f4ffbf8e4 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=524632f2-7b7e-4ef2-97f8-2200edf676b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=dcb76c64-2f71-4def-8943-6dbabbae13d8 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 129.5GB: boot/grub/core.img
 131.7GB: boot/grub/grub.cfg
 129.8GB: boot/initrd.img-2.6.32-21-generic
 129.8GB: boot/vmlinuz-2.6.32-21-generic
 129.8GB: initrd.img
 129.8GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
 
 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sdb2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=24305024-e76c-4ec6-9ecc-e7d64ca9550c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-19-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=31ac9a84-03fb-4a45-898d-19db167e4c70 /home ext3 relatime 0 2
# Entry for /dev/sda7 :
UUID=ab9fd6e0-c069-4dba-99d8-9c8dd3579667 /usr ext3 relatime 0 2
# Entry for /dev/sda8 :
UUID=3a09e702-45b7-4912-a829-fecb634126a2 none swap sw 0 0

=================== sdb2: Location of files loaded by Grub: ===================


  60.7GB: boot/grub/menu.lst
  60.4GB: boot/grub/stage2
  60.3GB: boot/initrd.img-2.6.28-11-generic
  60.2GB: boot/initrd.img-2.6.28-16-generic
  60.3GB: boot/initrd.img-2.6.28-17-generic
  63.1GB: boot/initrd.img-2.6.28-18-generic
  60.1GB: boot/initrd.img-2.6.28-19-generic
  60.3GB: boot/vmlinuz-2.6.28-11-generic
  60.3GB: boot/vmlinuz-2.6.28-16-generic
  60.3GB: boot/vmlinuz-2.6.28-17-generic
  60.3GB: boot/vmlinuz-2.6.28-18-generic
  60.3GB: boot/vmlinuz-2.6.28-19-generic
  60.1GB: initrd.img
  63.1GB: initrd.img.old
  60.3GB: vmlinuz
  60.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  41 1b a9 d7 0f 4e 80 36  74 b9 7a 60 0e 9a d2 04  |A....N.6t.z`....|
00000010  dc 2e 87 23 b4 52 a6 6c  c7 86 a4 3f 7d 11 7a 15  |...#.R.l...?}.z.|
00000020  0c 5e 66 ae 4d 8f 49 58  e6 aa ec fa 19 de f3 91  |.^f.M.IX........|
00000030  b2 b8 ec 8d 01 2c 8b a1  97 77 b5 d3 23 02 83 f0  |.....,...w..#...|
00000040  11 09 41 93 29 c7 42 cf  a0 73 3b 11 c7 6b b0 ef  |..A.).B..s;..k..|
00000050  73 e1 08 b4 b9 6b 74 36  46 2d 53 51 26 ab aa 82  |s....kt6F-SQ&...|
00000060  a3 c3 54 ae be 84 5d 91  64 a3 6d d2 17 f9 a3 47  |..T...].d.m....G|
00000070  16 86 e6 32 db 8f 55 6e  56 e4 8f eb 6c 33 d4 52  |...2..UnV...l3.R|
00000080  aa 54 a1 64 86 d2 4f f7  d6 02 6b a3 fb a5 a9 81  |.T.d..O...k.....|
00000090  68 d2 d5 38 e9 ef e3 f4  58 b9 4f 91 83 ce ed df  |h..8....X.O.....|
000000a0  33 e5 7e 34 ec e4 9a a3  16 b6 26 22 6e 01 0b 0b  |3.~4......&"n...|
000000b0  da 68 ea 96 e4 ae d2 48  01 dd f5 3a 46 15 eb 8b  |.h.....H...:F...|
000000c0  99 fe 4f 4a 16 3e 59 6a  c5 f0 83 66 8c 7b d0 3d  |..OJ.>Yj...f.{.=|
000000d0  7f da 72 3a 07 75 b8 0b  ea 1c 24 11 b4 f5 b4 3a  |..r:.u....$....:|
000000e0  96 37 72 51 5b cb 1b 26  01 f0 21 c9 58 0a 0a 0b  |.7rQ[..&..!.X...|
000000f0  d8 6b 5d e5 94 35 69 c7  86 65 2c c0 2e c5 71 c2  |.k]..5i..e,...q.|
00000100  56 20 c6 70 84 7a f3 fb  c6 27 47 b0 8b 1f 8d ac  |V .p.z...'G.....|
00000110  b8 76 d9 f0 17 36 a3 ac  b9 1a 10 12 22 73 63 34  |.v...6......"sc4|
00000120  4c 9b 54 20 2e fc bb 7a  e8 a8 bb ca d2 5a 08 c9  |L.T ...z.....Z..|
00000130  52 6e 43 1b e3 07 bd 73  5a 33 de 3b f6 8f ae 7d  |RnC....sZ3.;...}|
00000140  32 54 c6 e2 c4 56 24 94  a5 42 6d 6b 7f 4f d4 3a  |2T...V$..Bmk.O.:|
00000150  16 d4 5a ae e0 35 55 6f  12 8c 59 fe 2b 1f c2 53  |..Z..5Uo..Y.+..S|
00000160  50 de b0 84 ce ad 58 55  75 b1 e9 4d 33 36 8e fd  |P.....XUu..M36..|
00000170  df 73 91 16 49 2c 3f d3  a1 07 5c a3 87 19 f6 1a  |.s..I,?...\.....|
00000180  70 3e 86 04 86 a2 ca c2  1a 94 dd 55 2a 8d e8 9f  |p>.........U*...|
00000190  02 e0 d1 6b 8c f0 ad a5  20 80 cd 3b 36 f9 8f 5a  |...k.... ..;6..Z|
000001a0  a3 b5 8d e0 13 08 33 33  37 5d 70 c9 34 08 a3 99  |......337]p.4...|
000001b0  a3 8b d2 ce d0 e1 0c 6c  9c 5b d8 50 d7 50 00 fe  |.......l.[.P.P..|
000001c0  ff ff 82 fe ff ff 02 38  01 1c 00 88 3b 00 00 01  |.......8....;...|
000001d0  f1 90 05 fe ff ff 01 00  00 00 85 dc 2f 08 00 00  |............/...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb5

00000000  eb 2e 00 49 2f 4f 20 65  72 72 6f 72 00 08 00 10  |...I/O error....|
00000010  00 00 10 00 00 04 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 04 00 01  00 1f 00 00 01 00 00 00  |................|
00000030  fc 31 c0 90 8e d0 bc 00  7c 89 e5 50 bb 00 10 53  |.1......|..P...S|
00000040  50 88 56 24 16 b4 41 bb  aa 55 cd 13 1f 72 09 d0  |P.V$..A..U...r..|
00000050  d9 73 05 c6 06 c4 7d 42  66 31 c0 b0 02 57 16 9c  |.s....}Bf1...W..|
00000060  66 48 66 99 66 f7 76 28  66 52 66 99 66 c1 e0 05  |fHf.f.v(fRf.f...|
00000070  66 f7 76 0e 52 66 03 46  2c e8 0a 01 5e 66 58 8b  |f.v.Rf.F,...^fX.|
00000080  56 26 66 f7 e2 66 f7 76  0e 52 66 03 40 08 e8 f5  |V&f..f.v.Rf.@...|
00000090  00 5e 01 de 16 07 8d 7f  a8 b1 2c f3 a5 66 89 4d  |.^........,..f.M|
000000a0  b4 66 8b 45 ac 66 48 66  f7 76 0e 66 40 66 89 45  |.f.E.fHf.v.f@f.E|
000000b0  b0 66 ad 66 85 c0 74 1b  b7 80 e8 c6 00 66 ad 66  |.f.f..t......f.f|
000000c0  85 c0 74 0f b7 c0 e8 ba  00 66 ad 66 85 c0 74 03  |..t......f.f..t.|
000000d0  e8 b3 00 66 8b 5d b4 66  83 eb 0c 72 4f 53 66 2b  |...f.].f...rOSf+|
000000e0  5e 14 58 73 05 80 c4 1c  eb 41 66 53 66 2b 5e 10  |^.Xs.....AfSf+^.|
000000f0  72 1c 66 58 66 93 66 f7  76 10 66 52 66 85 d2 75  |r.fXf.f.v.fRf..u|
00000100  0d c1 e0 02 93 66 8b 01  bb 00 c0 e8 75 00 66 58  |.....f......u.fX|
00000110  66 99 66 f7 76 14 52 85  d2 75 0f c1 e0 02 93 66  |f.f.v.R..u.....f|
00000120  8b 81 00 b0 bb 00 80 e8  59 00 58 93 c1 e3 02 66  |........Y.X....f|
00000130  8b 01 9d 5b 07 9c e8 4d  00 9d 06 53 9c 72 2d 31  |...[...M...S.r-1|
00000140  f6 16 07 1e 8e df bf e2  7d 56 66 ad 66 50 ad 92  |........}Vf.fP..|
00000150  ad fe cc 91 f3 a6 75 02  91 ae 66 58 5e 8c df 1f  |......u...fX^...|
00000160  f9 0f 84 f8 fe 01 d6 3b  76 0e 72 d7 66 ff 45 b4  |.......;v.r.f.E.|
00000170  66 ff 4d b0 0f 85 5b ff  be df 7d 73 76 8b 56 24  |f.M...[...}sv.V$|
00000180  57 16 cb 16 07 f9 72 08  c4 5e fc 75 03 c4 5e fa  |W.....r..^.u..^.|
00000190  66 0f b6 4e 0d 66 f7 e1  66 03 46 1c 66 60 66 52  |f..N.f..f.F.f`fR|
000001a0  66 50 06 53 6a 01 6a 10  66 ff 76 18 59 66 f7 f1  |fP.Sj.j.f.v.Yf..|
000001b0  42 59 52 31 d2 66 f7 f1  86 d6 59 86 c5 c0 e4 06  |BYR1.f....Y.....|
000001c0  08 e1 40 b4 02 89 e6 8a  56 24 06 1e cd 13 1f 5b  |..@.....V$.....[|
000001d0  72 1e 8d 5f 20 8e c3 61  66 61 66 40 e2 be c3 4e  |r.._ ..afaf@...N|
000001e0  6f 20 67 72 6c 64 72 00  00 00 00 00 00 00 e2 59  |o grldr........Y|
000001f0  be 03 7c ac b4 0e cd 10  3c 00 75 f7 eb fe 55 aa  |..|.....<.u...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by frank cox on 2010-11-05
This from the Linux Mint Isadora

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

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
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb8 starts at sector 422156133.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb9 starts at sector 626294088.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb10 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb10 starts at sector 833757498.
    Operating System:  
    Boot files/dirs:   

sdb11: _________________________________________________________________________

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

/dev/sda1    *          2,048    14,649,343    14,647,296  83 Linux
/dev/sda2          14,651,390   488,394,751   473,743,362   5 Extended
/dev/sda5         484,493,312   488,394,751     3,901,440  82 Linux swap / Solaris
/dev/sda6          14,651,392   152,005,763   137,354,372  83 Linux
/dev/sda7         289,181,696   484,489,215   195,307,520   b W95 FAT32
/dev/sda8         152,006,656   283,486,207   131,479,552  83 Linux
/dev/sda9         283,488,256   289,169,407     5,681,152  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   116,599,769   116,599,707   7 HPFS/NTFS
/dev/sdb2         116,599,770   123,443,459     6,843,690  83 Linux
/dev/sdb3         123,443,460   976,768,064   853,324,605   5 Extended
/dev/sdb5         123,443,523   130,287,149     6,843,627  83 Linux
/dev/sdb6         130,287,213   390,829,319   260,542,107  83 Linux
/dev/sdb7         390,829,383   422,156,069    31,326,687  83 Linux
/dev/sdb8         422,156,133   626,294,024   204,137,892   b W95 FAT32
/dev/sdb9         626,294,088   833,757,434   207,463,347   b W95 FAT32
/dev/sdb10        833,757,498   970,904,339   137,146,842   b W95 FAT32
/dev/sdb11        970,904,403   976,768,064     5,863,662  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5031dd05-4336-4d94-a847-309f4ffbf8e4   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e9c80de9-4910-44a1-bd61-79488759f495   swap                                     
/dev/sda6        40e3f44b-3ed0-4f9d-ae9e-5d684e0d255c   ext4                                     
/dev/sda7        47A7-C218                              vfat                                     
/dev/sda8        524632f2-7b7e-4ef2-97f8-2200edf676b5   ext4                                     
/dev/sda9        dcb76c64-2f71-4def-8943-6dbabbae13d8   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb10       4B5A-D514                              vfat       Dual-Use3                     
/dev/sdb11       3a09e702-45b7-4912-a829-fecb634126a2   swap                                     
/dev/sdb1        9EC8A2D0C8A2A64D                       ntfs                                     
/dev/sdb2        24305024-e76c-4ec6-9ecc-e7d64ca9550c   ext3                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        d3edce97-12f5-4878-8827-49b4f4c1609f   ext3                                     
/dev/sdb6        31ac9a84-03fb-4a45-898d-19db167e4c70   ext3                                     
/dev/sdb7        ab9fd6e0-c069-4dba-99d8-9c8dd3579667   ext3                                     
/dev/sdb8        4B5A-D509                              vfat       Dual-Use                      
/dev/sdb9        4B5A-D511                              vfat       Dual-Use-2                    
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5031dd05-4336-4d94-a847-309f4ffbf8e4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5031dd05-4336-4d94-a847-309f4ffbf8e4 ro single 
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
    search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5031dd05-4336-4d94-a847-309f4ffbf8e4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=40e3f44b-3ed0-4f9d-ae9e-5d684e0d255c /home           ext4    defaults        0       2
/dev/sda7       /windows        vfat    utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.7GB: boot/grub/core.img
   2.9GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.35-22-generic
   2.9GB: boot/vmlinuz-2.6.35-22-generic
   1.5GB: initrd.img
   2.9GB: vmlinuz

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 524632f2-7b7e-4ef2-97f8-2200edf676b5
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 524632f2-7b7e-4ef2-97f8-2200edf676b5
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 524632f2-7b7e-4ef2-97f8-2200edf676b5
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda8)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 524632f2-7b7e-4ef2-97f8-2200edf676b5
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=524632f2-7b7e-4ef2-97f8-2200edf676b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda8) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 524632f2-7b7e-4ef2-97f8-2200edf676b5
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=524632f2-7b7e-4ef2-97f8-2200edf676b5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 524632f2-7b7e-4ef2-97f8-2200edf676b5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 524632f2-7b7e-4ef2-97f8-2200edf676b5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=5031dd05-4336-4d94-a847-309f4ffbf8e4 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5031dd05-4336-4d94-a847-309f4ffbf8e4
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=5031dd05-4336-4d94-a847-309f4ffbf8e4 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=524632f2-7b7e-4ef2-97f8-2200edf676b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=dcb76c64-2f71-4def-8943-6dbabbae13d8 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 129.5GB: boot/grub/core.img
 131.7GB: boot/grub/grub.cfg
 129.8GB: boot/initrd.img-2.6.32-21-generic
 129.8GB: boot/vmlinuz-2.6.32-21-generic
 129.8GB: initrd.img
 129.8GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
 
 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sdb2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=24305024-e76c-4ec6-9ecc-e7d64ca9550c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-19-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=31ac9a84-03fb-4a45-898d-19db167e4c70 /home ext3 relatime 0 2
# Entry for /dev/sda7 :
UUID=ab9fd6e0-c069-4dba-99d8-9c8dd3579667 /usr ext3 relatime 0 2
# Entry for /dev/sda8 :
UUID=3a09e702-45b7-4912-a829-fecb634126a2 none swap sw 0 0

=================== sdb2: Location of files loaded by Grub: ===================


  60.7GB: boot/grub/menu.lst
  60.4GB: boot/grub/stage2
  60.3GB: boot/initrd.img-2.6.28-11-generic
  60.2GB: boot/initrd.img-2.6.28-16-generic
  60.3GB: boot/initrd.img-2.6.28-17-generic
  63.1GB: boot/initrd.img-2.6.28-18-generic
  60.1GB: boot/initrd.img-2.6.28-19-generic
  60.2GB: boot/vmlinuz-2.6.28-11-generic
  60.3GB: boot/vmlinuz-2.6.28-16-generic
  60.3GB: boot/vmlinuz-2.6.28-17-generic
  60.3GB: boot/vmlinuz-2.6.28-18-generic
  60.3GB: boot/vmlinuz-2.6.28-19-generic
  60.1GB: initrd.img
  63.1GB: initrd.img.old
  60.3GB: vmlinuz
  60.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  41 1b a9 d7 0f 4e 80 36  74 b9 7a 60 0e 9a d2 04  |A....N.6t.z`....|
00000010  dc 2e 87 23 b4 52 a6 6c  c7 86 a4 3f 7d 11 7a 15  |...#.R.l...?}.z.|
00000020  0c 5e 66 ae 4d 8f 49 58  e6 aa ec fa 19 de f3 91  |.^f.M.IX........|
00000030  b2 b8 ec 8d 01 2c 8b a1  97 77 b5 d3 23 02 83 f0  |.....,...w..#...|
00000040  11 09 41 93 29 c7 42 cf  a0 73 3b 11 c7 6b b0 ef  |..A.).B..s;..k..|
00000050  73 e1 08 b4 b9 6b 74 36  46 2d 53 51 26 ab aa 82  |s....kt6F-SQ&...|
00000060  a3 c3 54 ae be 84 5d 91  64 a3 6d d2 17 f9 a3 47  |..T...].d.m....G|
00000070  16 86 e6 32 db 8f 55 6e  56 e4 8f eb 6c 33 d4 52  |...2..UnV...l3.R|
00000080  aa 54 a1 64 86 d2 4f f7  d6 02 6b a3 fb a5 a9 81  |.T.d..O...k.....|
00000090  68 d2 d5 38 e9 ef e3 f4  58 b9 4f 91 83 ce ed df  |h..8....X.O.....|
000000a0  33 e5 7e 34 ec e4 9a a3  16 b6 26 22 6e 01 0b 0b  |3.~4......&"n...|
000000b0  da 68 ea 96 e4 ae d2 48  01 dd f5 3a 46 15 eb 8b  |.h.....H...:F...|
000000c0  99 fe 4f 4a 16 3e 59 6a  c5 f0 83 66 8c 7b d0 3d  |..OJ.>Yj...f.{.=|
000000d0  7f da 72 3a 07 75 b8 0b  ea 1c 24 11 b4 f5 b4 3a  |..r:.u....$....:|
000000e0  96 37 72 51 5b cb 1b 26  01 f0 21 c9 58 0a 0a 0b  |.7rQ[..&..!.X...|
000000f0  d8 6b 5d e5 94 35 69 c7  86 65 2c c0 2e c5 71 c2  |.k]..5i..e,...q.|
00000100  56 20 c6 70 84 7a f3 fb  c6 27 47 b0 8b 1f 8d ac  |V .p.z...'G.....|
00000110  b8 76 d9 f0 17 36 a3 ac  b9 1a 10 12 22 73 63 34  |.v...6......"sc4|
00000120  4c 9b 54 20 2e fc bb 7a  e8 a8 bb ca d2 5a 08 c9  |L.T ...z.....Z..|
00000130  52 6e 43 1b e3 07 bd 73  5a 33 de 3b f6 8f ae 7d  |RnC....sZ3.;...}|
00000140  32 54 c6 e2 c4 56 24 94  a5 42 6d 6b 7f 4f d4 3a  |2T...V$..Bmk.O.:|
00000150  16 d4 5a ae e0 35 55 6f  12 8c 59 fe 2b 1f c2 53  |..Z..5Uo..Y.+..S|
00000160  50 de b0 84 ce ad 58 55  75 b1 e9 4d 33 36 8e fd  |P.....XUu..M36..|
00000170  df 73 91 16 49 2c 3f d3  a1 07 5c a3 87 19 f6 1a  |.s..I,?...\.....|
00000180  70 3e 86 04 86 a2 ca c2  1a 94 dd 55 2a 8d e8 9f  |p>.........U*...|
00000190  02 e0 d1 6b 8c f0 ad a5  20 80 cd 3b 36 f9 8f 5a  |...k.... ..;6..Z|
000001a0  a3 b5 8d e0 13 08 33 33  37 5d 70 c9 34 08 a3 99  |......337]p.4...|
000001b0  a3 8b d2 ce d0 e1 0c 6c  9c 5b d8 50 d7 50 00 fe  |.......l.[.P.P..|
000001c0  ff ff 82 fe ff ff 02 38  01 1c 00 88 3b 00 00 01  |.......8....;...|
000001d0  f1 90 05 fe ff ff 01 00  00 00 85 dc 2f 08 00 00  |............/...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb5

00000000  eb 2e 00 49 2f 4f 20 65  72 72 6f 72 00 08 00 10  |...I/O error....|
00000010  00 00 10 00 00 04 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 04 00 01  00 1f 00 00 01 00 00 00  |................|
00000030  fc 31 c0 90 8e d0 bc 00  7c 89 e5 50 bb 00 10 53  |.1......|..P...S|
00000040  50 88 56 24 16 b4 41 bb  aa 55 cd 13 1f 72 09 d0  |P.V$..A..U...r..|
00000050  d9 73 05 c6 06 c4 7d 42  66 31 c0 b0 02 57 16 9c  |.s....}Bf1...W..|
00000060  66 48 66 99 66 f7 76 28  66 52 66 99 66 c1 e0 05  |fHf.f.v(fRf.f...|
00000070  66 f7 76 0e 52 66 03 46  2c e8 0a 01 5e 66 58 8b  |f.v.Rf.F,...^fX.|
00000080  56 26 66 f7 e2 66 f7 76  0e 52 66 03 40 08 e8 f5  |V&f..f.v.Rf.@...|
00000090  00 5e 01 de 16 07 8d 7f  a8 b1 2c f3 a5 66 89 4d  |.^........,..f.M|
000000a0  b4 66 8b 45 ac 66 48 66  f7 76 0e 66 40 66 89 45  |.f.E.fHf.v.f@f.E|
000000b0  b0 66 ad 66 85 c0 74 1b  b7 80 e8 c6 00 66 ad 66  |.f.f..t......f.f|
000000c0  85 c0 74 0f b7 c0 e8 ba  00 66 ad 66 85 c0 74 03  |..t......f.f..t.|
000000d0  e8 b3 00 66 8b 5d b4 66  83 eb 0c 72 4f 53 66 2b  |...f.].f...rOSf+|
000000e0  5e 14 58 73 05 80 c4 1c  eb 41 66 53 66 2b 5e 10  |^.Xs.....AfSf+^.|
000000f0  72 1c 66 58 66 93 66 f7  76 10 66 52 66 85 d2 75  |r.fXf.f.v.fRf..u|
00000100  0d c1 e0 02 93 66 8b 01  bb 00 c0 e8 75 00 66 58  |.....f......u.fX|
00000110  66 99 66 f7 76 14 52 85  d2 75 0f c1 e0 02 93 66  |f.f.v.R..u.....f|
00000120  8b 81 00 b0 bb 00 80 e8  59 00 58 93 c1 e3 02 66  |........Y.X....f|
00000130  8b 01 9d 5b 07 9c e8 4d  00 9d 06 53 9c 72 2d 31  |...[...M...S.r-1|
00000140  f6 16 07 1e 8e df bf e2  7d 56 66 ad 66 50 ad 92  |........}Vf.fP..|
00000150  ad fe cc 91 f3 a6 75 02  91 ae 66 58 5e 8c df 1f  |......u...fX^...|
00000160  f9 0f 84 f8 fe 01 d6 3b  76 0e 72 d7 66 ff 45 b4  |.......;v.r.f.E.|
00000170  66 ff 4d b0 0f 85 5b ff  be df 7d 73 76 8b 56 24  |f.M...[...}sv.V$|
00000180  57 16 cb 16 07 f9 72 08  c4 5e fc 75 03 c4 5e fa  |W.....r..^.u..^.|
00000190  66 0f b6 4e 0d 66 f7 e1  66 03 46 1c 66 60 66 52  |f..N.f..f.F.f`fR|
000001a0  66 50 06 53 6a 01 6a 10  66 ff 76 18 59 66 f7 f1  |fP.Sj.j.f.v.Yf..|
000001b0  42 59 52 31 d2 66 f7 f1  86 d6 59 86 c5 c0 e4 06  |BYR1.f....Y.....|
000001c0  08 e1 40 b4 02 89 e6 8a  56 24 06 1e cd 13 1f 5b  |..@.....V$.....[|
000001d0  72 1e 8d 5f 20 8e c3 61  66 61 66 40 e2 be c3 4e  |r.._ ..afaf@...N|
000001e0  6f 20 67 72 6c 64 72 00  00 00 00 00 00 00 e2 59  |o grldr........Y|
000001f0  be 03 7c ac b4 0e cd 10  3c 00 75 f7 eb fe 55 aa  |..|.....<.u...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf  
```

---

### Post by frank cox on 2010-11-05
Thanks [oldfred]("http://ubuntuforums.org/member.php?u=852711") . thanks sikander3786 !

That was way to easy, almost feel guilty :} 

Everything work  from Linux Mint ,I can access 9.04,Xbuntu 10.10 , windows XP, way cool.Probably should update Xubuntu's Grub as well.

Now I think I will add Open S.U.S.E. . Really need another hard drive to back up my 500 gig and do it right. I almost hate to nuke 9.04 because that was my first Linus distro but that drive is a mess and as you said support has ended.

Thanks again !

---

