---
title: "Grub removed after xp install"
date: 2010-05-18
forum: General Help
---

### Post by Sammy88 on 2010-05-18
Hi, 
I'm relatively new to ubuntu. I have an IBM X31 type 2672. It was running
windows 7 and ubuntu netbook edition 10.04. I installed windows xp after running these two OS' for a while to try and fix an issue I had with video playback. However, when I run the pc now it boots straight into xp. I have read the forums about reinstalling grub. However, the first command in the grub shell that locates the HDD doesn't work :confused: . Which means the other commands don't work. Any suggestions? Thanks in advance :)

---

### Post by dcstar on 2010-05-18
> **Sammy88 said:**
> Hi, 
I'm relatively new to ubuntu. I have an IBM X31 type 2672. It was running
windows 7 and ubuntu netbook edition 10.04. I installed windows xp after running these two OS' for a while to try and fix an issue I had with video playback. However, when I run the pc now it boots straight into xp. I have read the forums about reinstalling grub. However, the first command in the grub shell that locates the HDD doesn't work :confused: . Which means the other commands don't work. Any suggestions? Thanks in advance :)

Do not used old legacy Grub HOWTOs, find Grub 2 instructions.

---

### Post by wilee-nilee on 2010-05-18
Post this script in code tags=highlight the text in the reply and click on # then submit reply.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
This script will let us know exactly whats going on.

---

### Post by Sammy88 on 2010-05-18
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   275,093,279   274,886,432   7 HPFS/NTFS
/dev/sda3         275,093,280   348,153,119    73,059,840   7 HPFS/NTFS
/dev/sda4         348,162,046   625,141,759   276,979,714   5 Extended
/dev/sda5         348,162,048   619,137,023   270,974,976  83 Linux
/dev/sda6         619,139,072   625,141,759     6,002,688  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        643087193086F0FA                       ntfs       System Reserved               
/dev/sda2        348C92678C922380                       ntfs                                     
/dev/sda3        B060BDB060BD7E22                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        67b1d3b2-5d18-4953-9417-4d89ead5e9ab   ext4                                     
/dev/sda6        a978c0f9-831b-4bd9-b8da-b391b60025bd   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 

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
search --no-floppy --fs-uuid --set 67b1d3b2-5d18-4953-9417-4d89ead5e9ab
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
search --no-floppy --fs-uuid --set 67b1d3b2-5d18-4953-9417-4d89ead5e9ab
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67b1d3b2-5d18-4953-9417-4d89ead5e9ab
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=67b1d3b2-5d18-4953-9417-4d89ead5e9ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67b1d3b2-5d18-4953-9417-4d89ead5e9ab
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=67b1d3b2-5d18-4953-9417-4d89ead5e9ab ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67b1d3b2-5d18-4953-9417-4d89ead5e9ab
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=67b1d3b2-5d18-4953-9417-4d89ead5e9ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67b1d3b2-5d18-4953-9417-4d89ead5e9ab
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=67b1d3b2-5d18-4953-9417-4d89ead5e9ab ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67b1d3b2-5d18-4953-9417-4d89ead5e9ab
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67b1d3b2-5d18-4953-9417-4d89ead5e9ab
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 643087193086f0fa
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=67b1d3b2-5d18-4953-9417-4d89ead5e9ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a978c0f9-831b-4bd9-b8da-b391b60025bd none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 296.5GB: boot/grub/core.img
 227.8GB: boot/grub/grub.cfg
 296.5GB: boot/initrd.img-2.6.32-21-generic
 296.5GB: boot/initrd.img-2.6.32-22-generic
 296.5GB: boot/vmlinuz-2.6.32-21-generic
 296.5GB: boot/vmlinuz-2.6.32-22-generic
 296.5GB: initrd.img
 296.5GB: initrd.img.old
 296.5GB: vmlinuz
 296.5GB: vmlinuz.old


is this right? :-?

---

### Post by oldfred on 2010-05-18
You just need to be sure to follow instructions for grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD:
Find linux partition:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

Your windows combined win7 & XP boots, but does XP boot? It is in sda1 but
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOW  S 
says partition 3 ??

---

### Post by Sammy88 on 2010-05-18
IT GOT GRUB BACK!! :) however it appears that XP overwrote windows  7 or something so it gives me no option for xp but simply boots it when i boot widnows 7 :( But thanks so much for your help as I now have ubuntu back, which is my main OS :) on a completely random note, is there anyway to switch to normal ubuntu 10.04 without losing all my programs etc? Thanks :)

---

### Post by oldfred on 2010-05-18
What do you mean by normal 10.04?

I added a comment on your boot.ini showing the wrong partition. I would change that to 1
default=multi(0)disk(0)rdisk(0)partition([COLOR=Red]1[/COLOR])\WINDOW  S 

It would be best to do from windows, but it may be a hidden file since it is system related. You can use nano but not other linux editors as most do not recognized the difference in line endings LF vs LF & CR.

Since you are combined with win7 I do not know if you also have to edit the BCD with BCDedit in windows to then see the XP correctly.

---

