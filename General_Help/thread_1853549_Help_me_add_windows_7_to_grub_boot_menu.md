---
title: "Help me add windows 7 to grub boot menu"
date: 2011-10-02
forum: General Help
---

### Post by JoshH54 on 2011-10-02
I am new to Ubuntu and the forums so forgive me if i do something stupid haha.

My problem isn't really bad it's just annoying.

My computer came with windows 7 installed. 

I bought a hard drive and installed it. I then installed Ubuntu 11.04 on it so i boot off that hard drive to get to the grub menu thing to go onto Ubuntu. 

But.... when i choose to boot windows 7 it give me a black screen with a flicking white spacer, so basically my question is WFT!??   :(

I can get into windows by booting off the main hard drive but it would be so much cooler if its just boots off grub when i tell it to.

So if any of you guys can give me a hand that would be awsome. Thanks in advance :)

---

### Post by ajgreeny on 2011-10-02
First try running ```
sudo update-grub
```in a terminal in Ubuntu, to see if that works.

If it does not help, from your Ubuntu system click on the **boot-info-script** link in my signature and follow the instructions to download and run the script, then copy the RESULTS.txt file back here between code tags which you get when you click the # in the toolbar of the reply entry box.

---

### Post by prodigy_ on 2011-10-02
Welcome to the forums. :)

Boot into Ubuntu, download Boot Info Script (linked in my sig). Unpack and run it (follow the instructions on the d/l page). It will output a file named RESULTS.TXT. Post the contents of the file here.

---

### Post by Blasphemist on 2011-10-02
Just an FYI for all. There is a better tool for this IMHO. Boot-repair can be installed to ubuntu and used for this. You can have it just produce a bit more detailed summary and have that reviewed here in the forums, and then have it make repairs automatically or via your control choices. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by prodigy_ on 2011-10-02
I don't have any experience with Boot-Repair, so can't comment. Personally, I'm used to CLI tools and I like the detailed output of BIS (though I admit it's not a silver bullet).

---

### Post by Blasphemist on 2011-10-02
understood prodigy. Check out boot-repair and look at its summary. It's basically the same but with a bit more at the end. I think it helps for a lot of users and we can always ask them to run commands if we are in doubt. The advanced tabs offer good options.

---

### Post by JoshH54 on 2011-10-02
Right did what you said and got all this mumbo jumbo haha
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   According to the info in the boot sector, sdb2 has 0 
                       sectors.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    39,847,935    39,845,888  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     39,847,936    40,052,735       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          40,052,736 1,484,888,063 1,444,835,328   7 NTFS / exFAT / HPFS
/dev/sda4       1,484,888,064 2,930,274,303 1,445,386,240   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   156,301,487   156,301,487  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2         262,178       301,240        39,063 EFI System partition
/dev/sdb3         301,241   143,898,897   143,597,657 Data partition (Windows/Linux)
/dev/sdb4     143,898,898   156,301,438    12,402,541 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8E6EE1326EE113AD                       ntfs       PQSERVICE
/dev/sda2        8E7EE1BA7EE19B6B                       ntfs       SYSTEM RESERVED
/dev/sda3        C284E2C384E2B8D5                       ntfs       Acer
/dev/sda4        42320C09320C051F                       ntfs       DATA
/dev/sdb2        F166-829F                              vfat       
/dev/sdb3        a77cbd1a-5479-4c09-b2f9-3351d632ba4d   ext4       
/dev/sdb4        f7ffc357-3b42-4675-b493-974dc961c07b   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb2        /boot/efi                vfat       (rw)
/dev/sdb3        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt3)'
search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt3)'
search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 8E6EE1326EE113AD
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 8E7EE1BA7EE19B6B
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
--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
UUID=F166-829F  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sdb4 during installation

hope it helps guys :D

---

### Post by prodigy_ on 2011-10-02
> => No boot loader is installed in the MBR of /dev/sdb.
This looks strange. Normally, in a setup like yours, Grub (Linux bootloader) would be listed here. Since you're able to boot into Ubuntu somehow this shouldn't be the source of the problem though I'd reinstall Grub just in case:
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

Which Windows entry did you choose in Grub menu when you tried to boot? The right one is "Windows 7 (loader) (on /dev/sda2)".

---

### Post by Blasphemist on 2011-10-02
Well, this is a bit complicated, or too new for me. :D

This is where we start. [http://www.rodsbooks.com/efi-bootloaders/index.html](http://www.rodsbooks.com/efi-bootloaders/index.html)

Rod is a forum user and the best with this that I have seen. I'll start following this documentation and see what I come up with. You have EFI and a GPT (Guid partition table). This is the new standard replacing BIOS and MBR.

---

### Post by prodigy_ on 2011-10-02
Well, sdb indeed uses GPT (so it probably makes sense that the script can't find Grub) but sda uses MBR and chainloading should work as usual.

---

### Post by JoshH54 on 2011-10-02
Thanks for your help guys. I am going to install grub again and i will post another result k. 2 secs :D

---

### Post by JoshH54 on 2011-10-02
Would it just be easier to use the windows boot menu and add Ubuntu to that???

---

### Post by JoshH54 on 2011-10-02
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   According to the info in the boot sector, sdb2 has 0 
                       sectors.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    39,847,935    39,845,888  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     39,847,936    40,052,735       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          40,052,736 1,484,888,063 1,444,835,328   7 NTFS / exFAT / HPFS
/dev/sda4       1,484,888,064 2,930,274,303 1,445,386,240   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   156,301,487   156,301,487  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2         262,178       301,240        39,063 EFI System partition
/dev/sdb3         301,241   143,898,897   143,597,657 Data partition (Windows/Linux)
/dev/sdb4     143,898,898   156,301,438    12,402,541 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8E6EE1326EE113AD                       ntfs       PQSERVICE
/dev/sda2        8E7EE1BA7EE19B6B                       ntfs       SYSTEM RESERVED
/dev/sda3        C284E2C384E2B8D5                       ntfs       Acer
/dev/sda4        42320C09320C051F                       ntfs       DATA
/dev/sdb2        F166-829F                              vfat       
/dev/sdb3        a77cbd1a-5479-4c09-b2f9-3351d632ba4d   ext4       
/dev/sdb4        f7ffc357-3b42-4675-b493-974dc961c07b   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb2        /boot/efi                vfat       (rw)
/dev/sdb3        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt3)'
search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt3)'
search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 8E6EE1326EE113AD
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 8E7EE1BA7EE19B6B
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
--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
UUID=F166-829F  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sdb4 during installation
UUID=f7ffc357-3b42-4675-b493-974dc961c07b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  14.292416096 = 15.346364928   boot/grub/grub.cfg                             1
   1.773106098 = 1.903858176    boot/initrd.img-2.6.38-11-generic              2
   1.335567951 = 1.434055168    boot/initrd.img-2.6.38-8-generic               1
   1.241611958 = 1.333170688    boot/vmlinuz-2.6.38-11-generic                 1
   4.284634113 = 4.600590848    boot/vmlinuz-2.6.38-8-generic                  1
   1.773106098 = 1.903858176    initrd.img                                     2
   1.335567951 = 1.434055168    initrd.img.old                                 1
   1.241611958 = 1.333170688    vmlinuz                                        1
   4.284634113 = 4.600590848    vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  5a 35 89 e9 74 48 4f 89  2a 2d 4a b1 8a 72 16 7e  |Z5..tHO.*-J..r.~|
00000010  0b e2 b6 14 3b 52 38 e3  27 94 58 c7 97 bb d4 d0  |....;R8.'.X.....|
00000020  75 aa 93 de 39 ba 5c 24  3b 45 90 0d 53 73 c8 19  |u...9.\$;E..Ss..|
00000030  83 5b 5a 19 28 36 81 78  af b2 32 8c 04 46 0c 38  |.[Z.(6.x..2..F.8|
00000040  55 5c 04 4e b8 cd ce 09  e9 d8 0f 72 4e 6b 4d 6d  |U\.N.......rNkMm|
00000050  81 0f a8 1f 52 1a 59 45  eb bf f3 59 8b 37 49 af  |....R.YE...Y.7I.|
00000060  16 f6 f0 6c 3e 7c 71 84  f8 41 79 15 68 4c c6 c0  |...l>|q..Ay.hL..|
00000070  8e d3 1c 21 eb 45 2b 26  70 3d b5 b1 ef cd 95 ca  |...!.E+&p=......|
00000080  fa 4e ff 7f 09 18 7a 91  7b aa 98 cc 0c 2c 6c ab  |.N....z.{....,l.|
00000090  4a 9e 88 8f 69 7a 17 c3  76 02 20 7f b1 2f 20 88  |J...iz..v. ../ .|
000000a0  ef c7 f5 4a 2b 6a 5b 76  5a 90 8c c5 e1 e2 f6 f4  |...J+j[vZ.......|
000000b0  97 24 9a 39 18 56 8a 4f  6e 08 d6 86 6a f5 5d 29  |.$.9.V.On...j.])|
000000c0  63 d7 82 76 de 27 da 89  40 3a e1 b3 c9 28 ce ef  |c..v.'..@:...(..|
000000d0  ba 34 51 0a d0 a3 2d 7d  81 15 33 91 9f 65 32 99  |.4Q...-}..3..e2.|
000000e0  bf 65 f9 0f d6 8f 9b 6c  67 69 13 65 41 52 9d fd  |.e.....lgi.eAR..|
000000f0  fb a6 d1 5e 63 f0 4c 01  b0 b4 d2 0a 51 b0 36 46  |...^c.L.....Q.6F|
00000100  a7 43 cb 38 e8 37 07 3c  f4 f1 c3 4f ca 7a 0c ac  |.C.8.7.<...O.z..|
00000110  d5 8a f7 53 f7 49 34 29  a6 a6 99 3c 7b 48 15 28  |...S.I4)...<{H.(|
00000120  ed ba 4a fd 93 3a 0c f5  55 38 fd 38 96 41 22 c0  |..J..:..U8.8.A".|
00000130  a8 0f e4 e7 2b b4 2a 8e  25 bf 8d 99 62 b0 85 d8  |....+.*.%...b...|
00000140  00 87 9b da 16 89 d7 9c  e6 80 84 2d 5c 9b 62 08  |...........-\.b.|
00000150  53 e6 f5 80 2d 8a b7 ce  49 ba 1b 6d bf 02 72 e8  |S...-...I..m..r.|
00000160  ba c4 f6 91 f1 94 70 81  8e 1b 47 2a dd c0 bc e2  |......p...G*....|
00000170  10 d8 be c9 95 fc 08 61  90 28 f1 6f b8 4d 8e 45  |.......a.(.o.M.E|
00000180  c3 0e 73 db c5 13 6b 96  ec 14 dd f2 ca 9e f0 68  |..s...k........h|
00000190  3b ef 63 4c bd b4 3b 0f  76 7d 7e 58 12 5e ae c0  |;.cL..;.v}~X.^..|
000001a0  7c 3d d8 37 09 68 aa 5e  f0 c3 f8 0f 60 0a c2 48  ||=.7.h.^....`..H|
000001b0  28 d5 59 ad a5 80 20 e5  ee 0a 9a fb c0 bb f4 33  |(.Y... ........3|
000001c0  fc 7d 65 38 d2 1c 15 6b  89 8a 7b cc c7 40 47 a3  |.}e8...k..{..@G.|
000001d0  0d 72 8d af cb 41 0e 47  5d dc 9e a5 1a 05 0f ed  |.r...A.G].......|
000001e0  8e bc 57 18 8c ac 01 38  9b 23 a0 87 79 73 5d 11  |..W....8.#..ys].|
000001f0  3c 10 8e 3c 39 fe 63 a1  73 7f 26 eb 03 ca 53 d8  |<..<9.c.s.&...S.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf sdg

---

### Post by prodigy_ on 2011-10-02
Still doesn't work?

---

### Post by JoshH54 on 2011-10-02
I haven't got the cd to repair grub so cant do it atm sorry. thanks thought, what do you think of using the windows boot menu

---

### Post by prodigy_ on 2011-10-02
You could try [EasyBCD](http://neosmart.net/) for that. It's free for non-commercial use.

---

### Post by JoshH54 on 2011-10-02
awsome. Will try it when i get the chance. cheers mate you make ubuntu even better :)

---

### Post by Blasphemist on 2011-10-02
Little did I know when I was posting about boot-repair that it would have prevented an annoying thing, posting a results file without code tags. Just saying Josh, post the results within code tags (# icon here) so it doesn't display so long.

I can't quite figure this out with one mbr disk and one gpt. I don't feel your going to gain anything by re-installing a working grub2. Not that it looks like everything in grub2 is in the right directories to me but it is working. Just the chainload to windows isn't working right? I can tell that all of the boot files shown on your sda1, sda2 and sda3 are on one partiton in my pc. The partition that I chainload to. It could be as simple as copying all those files to sda3 and chainloading to that partition.

I don't know. I'll keep thinkin.

---

### Post by JoshH54 on 2011-10-02
haha i did the # thing and it said [code][code] so i pasted the code but was i ment to paste it between the 2 codes haha.

so is my grub broken or just weird

cheers mate i will try reading up about it too but for some reason i think I wont get far, this stuff looks insane

Thanks again guys

---

### Post by JoshH54 on 2011-10-02
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   According to the info in the boot sector, sdb2 has 0 
                       sectors.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    39,847,935    39,845,888  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     39,847,936    40,052,735       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          40,052,736 1,484,888,063 1,444,835,328   7 NTFS / exFAT / HPFS
/dev/sda4       1,484,888,064 2,930,274,303 1,445,386,240   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   156,301,487   156,301,487  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2         262,178       301,240        39,063 EFI System partition
/dev/sdb3         301,241   143,898,897   143,597,657 Data partition (Windows/Linux)
/dev/sdb4     143,898,898   156,301,438    12,402,541 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8E6EE1326EE113AD                       ntfs       PQSERVICE
/dev/sda2        8E7EE1BA7EE19B6B                       ntfs       SYSTEM RESERVED
/dev/sda3        C284E2C384E2B8D5                       ntfs       Acer
/dev/sda4        42320C09320C051F                       ntfs       DATA
/dev/sdb2        F166-829F                              vfat       
/dev/sdb3        a77cbd1a-5479-4c09-b2f9-3351d632ba4d   ext4       
/dev/sdb4        f7ffc357-3b42-4675-b493-974dc961c07b   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb2        /boot/efi                vfat       (rw)
/dev/sdb3        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt3)'
search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt3)'
search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt3)'
    search --no-floppy --fs-uuid --set=root a77cbd1a-5479-4c09-b2f9-3351d632ba4d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 8E6EE1326EE113AD
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 8E7EE1BA7EE19B6B
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
--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=a77cbd1a-5479-4c09-b2f9-3351d632ba4d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
UUID=F166-829F  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sdb4 during installation
UUID=f7ffc357-3b42-4675-b493-974dc961c07b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  14.292416096 = 15.346364928   boot/grub/grub.cfg                             1
   1.773106098 = 1.903858176    boot/initrd.img-2.6.38-11-generic              2
   1.335567951 = 1.434055168    boot/initrd.img-2.6.38-8-generic               1
   1.241611958 = 1.333170688    boot/vmlinuz-2.6.38-11-generic                 1
   4.284634113 = 4.600590848    boot/vmlinuz-2.6.38-8-generic                  1
   1.773106098 = 1.903858176    initrd.img                                     2
   1.335567951 = 1.434055168    initrd.img.old                                 1
   1.241611958 = 1.333170688    vmlinuz                                        1
   4.284634113 = 4.600590848    vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  5a 35 89 e9 74 48 4f 89  2a 2d 4a b1 8a 72 16 7e  |Z5..tHO.*-J..r.~|
00000010  0b e2 b6 14 3b 52 38 e3  27 94 58 c7 97 bb d4 d0  |....;R8.'.X.....|
00000020  75 aa 93 de 39 ba 5c 24  3b 45 90 0d 53 73 c8 19  |u...9.\$;E..Ss..|
00000030  83 5b 5a 19 28 36 81 78  af b2 32 8c 04 46 0c 38  |.[Z.(6.x..2..F.8|
00000040  55 5c 04 4e b8 cd ce 09  e9 d8 0f 72 4e 6b 4d 6d  |U\.N.......rNkMm|
00000050  81 0f a8 1f 52 1a 59 45  eb bf f3 59 8b 37 49 af  |....R.YE...Y.7I.|
00000060  16 f6 f0 6c 3e 7c 71 84  f8 41 79 15 68 4c c6 c0  |...l>|q..Ay.hL..|
00000070  8e d3 1c 21 eb 45 2b 26  70 3d b5 b1 ef cd 95 ca  |...!.E+&p=......|
00000080  fa 4e ff 7f 09 18 7a 91  7b aa 98 cc 0c 2c 6c ab  |.N....z.{....,l.|
00000090  4a 9e 88 8f 69 7a 17 c3  76 02 20 7f b1 2f 20 88  |J...iz..v. ../ .|
000000a0  ef c7 f5 4a 2b 6a 5b 76  5a 90 8c c5 e1 e2 f6 f4  |...J+j[vZ.......|
000000b0  97 24 9a 39 18 56 8a 4f  6e 08 d6 86 6a f5 5d 29  |.$.9.V.On...j.])|
000000c0  63 d7 82 76 de 27 da 89  40 3a e1 b3 c9 28 ce ef  |c..v.'..@:...(..|
000000d0  ba 34 51 0a d0 a3 2d 7d  81 15 33 91 9f 65 32 99  |.4Q...-}..3..e2.|
000000e0  bf 65 f9 0f d6 8f 9b 6c  67 69 13 65 41 52 9d fd  |.e.....lgi.eAR..|
000000f0  fb a6 d1 5e 63 f0 4c 01  b0 b4 d2 0a 51 b0 36 46  |...^c.L.....Q.6F|
00000100  a7 43 cb 38 e8 37 07 3c  f4 f1 c3 4f ca 7a 0c ac  |.C.8.7.<...O.z..|
00000110  d5 8a f7 53 f7 49 34 29  a6 a6 99 3c 7b 48 15 28  |...S.I4)...<{H.(|
00000120  ed ba 4a fd 93 3a 0c f5  55 38 fd 38 96 41 22 c0  |..J..:..U8.8.A".|
00000130  a8 0f e4 e7 2b b4 2a 8e  25 bf 8d 99 62 b0 85 d8  |....+.*.%...b...|
00000140  00 87 9b da 16 89 d7 9c  e6 80 84 2d 5c 9b 62 08  |...........-\.b.|
00000150  53 e6 f5 80 2d 8a b7 ce  49 ba 1b 6d bf 02 72 e8  |S...-...I..m..r.|
00000160  ba c4 f6 91 f1 94 70 81  8e 1b 47 2a dd c0 bc e2  |......p...G*....|
00000170  10 d8 be c9 95 fc 08 61  90 28 f1 6f b8 4d 8e 45  |.......a.(.o.M.E|
00000180  c3 0e 73 db c5 13 6b 96  ec 14 dd f2 ca 9e f0 68  |..s...k........h|
00000190  3b ef 63 4c bd b4 3b 0f  76 7d 7e 58 12 5e ae c0  |;.cL..;.v}~X.^..|
000001a0  7c 3d d8 37 09 68 aa 5e  f0 c3 f8 0f 60 0a c2 48  ||=.7.h.^....`..H|
000001b0  28 d5 59 ad a5 80 20 e5  ee 0a 9a fb c0 bb f4 33  |(.Y... ........3|
000001c0  fc 7d 65 38 d2 1c 15 6b  89 8a 7b cc c7 40 47 a3  |.}e8...k..{..@G.|
000001d0  0d 72 8d af cb 41 0e 47  5d dc 9e a5 1a 05 0f ed  |.r...A.G].......|
000001e0  8e bc 57 18 8c ac 01 38  9b 23 a0 87 79 73 5d 11  |..W....8.#..ys].|
000001f0  3c 10 8e 3c 39 fe 63 a1  73 7f 26 eb 03 ca 53 d8  |<..<9.c.s.&...S.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf sdg 


```

---

### Post by JoshH54 on 2011-10-02
Just thought I'd see how you actually did it haha

Happy now Blasphemist haha

cheers

---

### Post by Blasphemist on 2011-10-02
Good work Josh! I promise, knowing how to use the code tags is good. :)

Please do me this favor though. Do install boot-repair and produce its summary. I want to see what it shows differently than the bootinfoscript, like what it would do. I can't say that I know what it would want to do. It might be able to fix the chainload, who knows. But I'd just like to see its summary that would include what it wants to do I think. 

I can think of a number of options but none I'm sure of right now.

---

### Post by JoshH54 on 2011-10-04
Dont have the cd anymore so cant do it sorry mate

---

