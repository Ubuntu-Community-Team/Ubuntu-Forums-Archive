---
title: "Boot up options"
date: 2010-07-07
forum: General Help
---

### Post by scotchfudge on 2010-07-07
Hi

I installed Ubuntu 10.04 three days back. After some days of working smoothly I did something wrong somewhere which led to the disappearance of Windows 7 from the boot up options. Also, [U][B]
bootmgr missing 
PRESS CTRL+ALT+DELETE[/B][/U]

The above error shows up every time windows7 was selected to load. Now even the option does not appear in the list. 

I tried to edit menu.lst but it dint help(perhaps because my editing and coding was flawed).

Please help me get out of this mess!!

Thanks!

---

### Post by Leppie on 2010-07-07
please download and run the [boot info script]("http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.55/boot_info_script055.sh/download") and post the generated RESULTS.txt

---

### Post by scotchfudge on 2010-07-07
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1             145,408    21,116,927    20,971,520   7 HPFS/NTFS
/dev/sda2    *     21,116,928   177,190,903   156,073,976   7 HPFS/NTFS
/dev/sda3         177,192,958   312,580,095   135,387,138   f W95 Ext d (LBA)
/dev/sda5         177,192,960   302,054,115   124,861,156   7 HPFS/NTFS
/dev/sda6         302,055,424   312,014,847     9,959,424  83 Linux
/dev/sda7         312,016,896   312,580,095       563,200  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AA403383403354F3                       ntfs       TRASH                         
/dev/sda2        AE780ED4780E9AEB                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        7E442025441FDF29                       ntfs       New Volume                    
/dev/sda6        d18e8313-ef1b-46b9-a2ad-d77acb7c9c80   ext4                                     
/dev/sda7        83cedb62-47cd-4b87-a9c2-882e183e4a51   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


=========================== sda6/boot/grub/menu.lst: ===========================

title        Ubuntu 10.04, kernel 2.6.28-15-generic
uuid        16cba197-6288-4261-8bbd-367d837e9f61
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=16cba197-6288-4261-8bbd-367d837e9f61 ro quiet splash
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

#title        Ubuntu 10.04, kernel 2.6.28-15-generic (recovery mode)
#uuid        16cba197-6288-4261-8bbd-367d837e9f61
#kernel        /boot/vmlinuz-2.6.28-15-generic #root=UUID=16cba197-6288-4261-8bbd-367d837e9f61 ro  single
#initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 10.04, kernel 2.6.28-14-generic
uuid        16cba197-6288-4261-8bbd-367d837e9f61
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=16cba197-6288-4261-8bbd-367d837e9f61 ro quiet splash
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

#title        Ubuntu 10.04, kernel 2.6.28-14-generic (recovery mode)
#uuid        16cba197-6288-4261-8bbd-367d837e9f61
#kernel        /boot/vmlinuz-2.6.28-14-generic #root=UUID=16cba197-6288-4261-8bbd-367d837e9f61 ro  single
#initrd        /boot/initrd.img-2.6.28-14-generic


 This entry automatically added by the Debian installer for a non-linux OS  on /dev/sda1
title        Windows 7
root        (hd0,1)
savedefault
makeactive
chainloader    +1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set d18e8313-ef1b-46b9-a2ad-d77acb7c9c80
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
search --no-floppy --fs-uuid --set d18e8313-ef1b-46b9-a2ad-d77acb7c9c80
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d18e8313-ef1b-46b9-a2ad-d77acb7c9c80
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=d18e8313-ef1b-46b9-a2ad-d77acb7c9c80 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d18e8313-ef1b-46b9-a2ad-d77acb7c9c80
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=d18e8313-ef1b-46b9-a2ad-d77acb7c9c80 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d18e8313-ef1b-46b9-a2ad-d77acb7c9c80
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d18e8313-ef1b-46b9-a2ad-d77acb7c9c80 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d18e8313-ef1b-46b9-a2ad-d77acb7c9c80
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d18e8313-ef1b-46b9-a2ad-d77acb7c9c80 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d18e8313-ef1b-46b9-a2ad-d77acb7c9c80
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d18e8313-ef1b-46b9-a2ad-d77acb7c9c80
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=d18e8313-ef1b-46b9-a2ad-d77acb7c9c80 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=83cedb62-47cd-4b87-a9c2-882e183e4a51 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 157.1GB: boot/grub/core.img
 157.6GB: boot/grub/grub.cfg
 155.0GB: boot/grub/menu.lst
 158.6GB: boot/initrd.img-2.6.32-21-generic
 159.0GB: boot/initrd.img-2.6.32-23-generic
 158.6GB: boot/vmlinuz-2.6.32-21-generic
 158.7GB: boot/vmlinuz-2.6.32-23-generic
 159.0GB: initrd.img
 158.6GB: initrd.img.old
 158.7GB: vmlinuz
 158.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  48 34 48 34 48 34 48 34  48 34 48 34 48 34 48 34  |H4H4H4H4H4H4H4H4|
*
00000040  48 34 00 00 00 00 48 34  48 34 4c 34 4c 34 4c 34  |H4....H4H4L4L4L4|
00000050  4c 34 4c 34 4c 34 4c 34  4c 34 4c 34 4c 34 4c 34  |L4L4L4L4L4L4L4L4|
*
00000180  56 34 00 00 58 34 00 00  5a 34 00 00 56 34 56 34  |V4..X4..Z4..V4V4|
00000190  58 34 58 34 5a 34 5a 34  5b 34 00 00 5f 34 00 00  |X4X4Z4Z4[4.._4..|
000001a0  00 00 00 00 5b 34 5b 34  5f 34 5f 34 56 34 61 34  |....[4[4_4_4V4a4|
000001b0  58 34 65 34 5a 34 00 00  00 00 61 34 61 34 00 fe  |X4e4Z4....a4a4..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 e4 3a 71 07 00 fe  |...........:q...|
000001d0  ff ff 05 fe ff ff f4 3a  71 07 0e fd 97 00 00 00  |.......:q.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Leppie on 2010-07-07
was this a clean install of Lucid?
Lucid uses by default grub2, but you also seem to have parts of grub legacy.
First remove the legacy parts:
```
sudo apt-get purge grub && sudo rm /boot/grub/menu.lst
```

Now rebuild the grub2 menu:
```
sudo update-grub
```
please post the output of the last command.

---

### Post by scotchfudge on 2010-07-07
[U]
**RESULT OF FIRST COMMAND**[/U]

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-headers-2.6.32-23-generic (2.6.32-23.37) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing linux-headers-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-23-generic; however:
  Package linux-headers-2.6.32-23-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 linux-headers-2.6.32-23-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)








_**RESULT OF SECOND COMMAND**_
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by scotchfudge on 2010-07-07
A clean install according to what I understand by clean install.

Win7 was already on drive C.

Everything was working perfect till I fiddled with something which created a mess :|

---

### Post by Leppie on 2010-07-07
> **scotchfudge said:**
> Everything was working perfect till I fiddled with something which created a mess :|
what was it exactly you were fiddling with? knowing this could save us a lot of time...

you seem to have an issue with the package archives as well.
issue the following command to see if it resolves anything:
```
sudo apt-get -f install
```

---

