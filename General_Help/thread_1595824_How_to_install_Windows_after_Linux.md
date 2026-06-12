---
title: "How to install Windows after Linux?"
date: 2010-10-13
forum: General Help
---

### Post by GermanGuaimare on 2010-10-13
[LEFT]Hey guys, I'm having an issue and i need your help. I'm using Mint 9 x64 and Windows 7 x64 and I'm having a lot of problems with my Windows partition, so I want to format and reinstall Windows in that partition. The last time I tried to do that, Windows erased the Grub, so I could not enter my Linux partition. I had to reinstall Linux aswell. So I'm here to ask you guys if there is a way I can install Windows without damaging my Linux partition. Thank you for your help.
[/LEFT]

---

### Post by coffeecat on 2010-10-13
> **GermanGuaimare said:**
> The last time I tried to do that, Windows erased the Grub, so I could not enter my Linux partition. I had to reinstall Linux aswell. So I'm here to ask you guys if there is a way I can install Windows without damaging my Linux partition.


Unless you told Windows to use the whole disc, it would not have damaged your Linux partition, so you needn't have re-installed. Windows simply overwrites stage 1 of grub with the Windows MBR. It's quite easy to repair grub. All you need is an Ubuntu live CD (or Mint live CD) and these instructions:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by GermanGuaimare on 2010-10-13
Well, I'm sure I installed Windows on it's previous partition, not the whole disk. And after the install I could not select wich system to use. Thanks anyway. Would like to hear more recommendations.

---

### Post by stinkeye on 2010-10-13
I recommend coffeecat's recommendations.

---

### Post by coffeecat on 2010-10-13
> **GermanGuaimare said:**
> Well, I'm sure I installed Windows on it's previous partition, not the whole disk. And after the install I could not select wich system to use. Thanks anyway.

Yes. When Windows replaces grub stage 1 with the Windows MBR, you boot straight into Windows. But grub stage 2 and the grub configuration files (including the menu) were still in your Linux root partition. A re-install was not necessary. The link I gave tells you all you need to know.

---

### Post by GermanGuaimare on 2010-10-13
Well, I will try it then. Thanks for the help, let you know if it worked.:)

---

### Post by GermanGuaimare on 2010-10-13
Hey guys, now I reaaally need your help. Dont know how but I was trying to repair the Grub from the Live CD and  I really messed it up now. Instead of having a Grub to select my operative system, I have a terminal kind of screen. It says file not found, rescue Grub, and it lets me enter commands. Don't know what to do. If I have to install both systems all over again I will cry. Seriously. Please help me. Thanks for all.

---

### Post by coffeecat on 2010-10-14
Boot up from the live CD (Ubuntu or Mint - it doesn't matter) and make sure you can connect to the internet. Go to

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

And follow the instructions there. Post the contents of the RESULTS.txt file. When you post it, please be sure to highlight the whole text and then click on the # symbol in the toolbar of the message window, just above the message field. This will put it in [noparse]```

```[/noparse] tags, otherwise it will be impossible to read.

The contents of RESULTS.txt will show us your partition layout, how grub is installed and other useful information and may show us what has gone wrong.

---

### Post by GermanGuaimare on 2010-10-14
Hey guys, I solved my problem using Super Grub Disk, or at least created a Grub. The problem now is that I can boot my Linux Partition, but not my Windows partition. I need your help once again. Please don't post anything super complicated, I'm no expert. Thank you for your help.

---

### Post by coffeecat on 2010-10-14
Same advice. Run the bootinfo script (link in my previous post) and post the RESULTS.txt. It will tell us what's going wrong.

---

### Post by wilee-nilee on 2010-10-14
> **GermanGuaimare said:**
> Hey guys, I solved my problem using Super Grub Disk, or at least created a Grub. The problem now is that I can boot my Linux Partition, but not my Windows partition. I need your help once again. Please don't post anything super complicated, I'm no expert. Thank you for your help.

Try in the linux terminal
```
sudo update-grub
```

If W7 doesn't show in the grub lines made in the terminal run the bootscript, and post it as others have suggested.

---

### Post by GermanGuaimare on 2010-10-14
Hey guys, followed your advice, this is the result.

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   152,813,476   152,606,629   7 HPFS/NTFS
/dev/sda3         607,055,870   625,141,759    18,085,890   5 Extended
/dev/sda5         607,055,872   625,141,759    18,085,888  82 Linux swap / Solaris
/dev/sda4         152,813,568   607,053,823   454,240,256  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DE26FDC626FD9FA7                       ntfs       Reservado para el sistema     
/dev/sda2        4218DCFD18DCF0C1                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        83fc4062-8808-4535-8ee4-4737c2a7b0d1   ext4                                     
/dev/sda5        0d32e0d0-1785-4a99-a244-a23d1faf6196   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 83fc4062-8808-4535-8ee4-4737c2a7b0d1
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 83fc4062-8808-4535-8ee4-4737c2a7b0d1
set locale_dir=($root)/boot/grub/locale
set lang=es
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 83fc4062-8808-4535-8ee4-4737c2a7b0d1
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
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda4)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 83fc4062-8808-4535-8ee4-4737c2a7b0d1
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=83fc4062-8808-4535-8ee4-4737c2a7b0d1 ro  vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda4) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 83fc4062-8808-4535-8ee4-4737c2a7b0d1
    echo    'Cargando Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=83fc4062-8808-4535-8ee4-4737c2a7b0d1 ro single  vga=795
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 83fc4062-8808-4535-8ee4-4737c2a7b0d1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 83fc4062-8808-4535-8ee4-4737c2a7b0d1
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=83fc4062-8808-4535-8ee4-4737c2a7b0d1 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 269.5GB: boot/grub/core.img
 196.6GB: boot/grub/grub.cfg
 269.5GB: boot/initrd.img-2.6.32-21-generic
 269.5GB: boot/vmlinuz-2.6.32-21-generic
 269.5GB: initrd.img
 269.5GB: vmlinuz
```

---

### Post by wilee-nilee on 2010-10-14
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD **/boot/grub/core.img**

This should not be in the NTFS partition, we generally suggest this link for using testdisc.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I had to look through quickly as a class is starting, but I think that is the main problem.

---

### Post by coffeecat on 2010-10-15
@GermanGuaimare, try wilnee-nilee's link, but if that doesn't work for you and you do not have a Windows 7 install or recovery disc, you can download the W7 recovery disc from here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

I can't remember the details, but there's a graphical utility in that for repairing booting problems. But be careful to choose the right one - there's boot sector repair and mbr repair. If you repair the mbr with that, you'll be booting into Windows only again and you'll need to do what I suggested in my post #2, and it's possible that you made an error when using that which is perhaps why the Windows boot sector is corrupted with grub files.

---

### Post by GermanGuaimare on 2010-10-15
Thanks coffeecat, I'm downloading the repair disc for my system, I will try it and let you know what happens. Thank you for your help, you really are trying to repair my pc, glad I can count on people like you.

---

### Post by GermanGuaimare on 2010-10-15
Hey guys, I did the boot repairing with the recovery disk and then ran sudo update-grub, and still my windows partition isn't showing on startup. I'm getting tired already. What else should I do?

---

### Post by oldfred on 2010-10-15
did you delete the extra folder from wilee-nilee's post #13?

---

### Post by GermanGuaimare on 2010-10-15
This folder "Boot files/dirs:   /bootmgr /Boot/BCD **/boot/grub/core.img"**?

---

### Post by oldfred on 2010-10-15
Windows does not see a difference between capitals and small letters so /Boot & /boot are the same in windows and windows does not allow two identical folders. Delete the /boot that is from grub somehow. But be careful not to delete /Boot as that contains essential windows boot files.

---

### Post by GermanGuaimare on 2010-10-15
Hey guys, I erased the foler and ran sudo update-grub. Now my Windows partition is showing on the grub, and I am capable of entering it. Thank you so much for all the help, I learned a few new things thanks to you. The problem is solved.

---

