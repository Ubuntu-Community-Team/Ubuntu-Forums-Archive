---
title: "Windows 7 not booting"
date: 2010-06-16
forum: General Help
---

### Post by raptor1770 on 2010-06-16
Hello all, 
having a minor crises here, thank you in advance for help. I upgraded ubuntu to 10.04 using the built in upgrade client. Before the upgrade I had a dual boot option setup using grub to choose ubuntu or windows 7 64 bit. 

During the upgrade process I was presented with options concerning the grub loader and where it should be installed/upgraded. I have a bad feeling that my options in that menu may have cause my current problem, which is that when I select Windows 7 from the grub menu, it doesn't load. It shows a black screen with a cursor blinking in the top left and never loads. 

Everything was working fine until I upgraded about an hour ago and ubuntu is loading just fine. (I'm using to make this post now) I dont want to make any changes without advice lest I make the situation worse. How do I fix this?

Thanks again.

---

### Post by raptor1770 on 2010-06-16
Would reinstalling grub help?

If so, what settings should I use to make sure it works and I don't kill my ability to boot ubuntu?

Really need help on this, I'm afraid to do anything that will make things worse.

Edit:
I'm following some guides on reinstalling grub however when I enter the command

```
 sudo grub 
```

it returns an error 

```
 sudo: grub: command not found 
```

---

### Post by piratebill on 2010-06-16
It does sound like you borked your grub.  I would reinstall it, but I'd use the Ubuntu boot Cd to do it.  Boot into the live environment and then follow those instructions you found.  Should fix it really easy.

---

### Post by wilee-nilee on 2010-06-16
Post the script in my sig with the code tags as described. at this point **don't reload anything** just post the script.

---

### Post by oldfred on 2010-06-16
If in your upgrade you installed grub to the partitions (not drives) then you over wrote the part of windows that is in the windows partition's boot sector.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If that does not work post the boot script info that wilee-nilee recommended.

---

### Post by raptor1770 on 2010-06-17
> **wilee-nilee said:**
> Post the script in my sig with the code tags as described. at this point **don't reload anything** just post the script.

Here is the RESULTS.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 708338791 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 708311039 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

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

/dev/sda1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   708,016,679   708,014,632   7 HPFS/NTFS
/dev/sdb2         708,016,680   976,768,064   268,751,385   5 Extended
/dev/sdb5         708,016,743   965,763,539   257,746,797  83 Linux
/dev/sdb6         965,763,603   976,768,064    11,004,462  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D84CCA7D4CCA55C2                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7AF2A47BF2A43D6F                       ntfs       Disk                          
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        7a88c54e-d6a2-4613-9c39-df937267fed3   ext4                                     
/dev/sdb6        89126291-0d44-495c-9b8f-b0bdc5da0251   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 7a88c54e-d6a2-4613-9c39-df937267fed3
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
search --no-floppy --fs-uuid --set 7a88c54e-d6a2-4613-9c39-df937267fed3
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
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 7a88c54e-d6a2-4613-9c39-df937267fed3
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=7a88c54e-d6a2-4613-9c39-df937267fed3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 7a88c54e-d6a2-4613-9c39-df937267fed3
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=7a88c54e-d6a2-4613-9c39-df937267fed3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 7a88c54e-d6a2-4613-9c39-df937267fed3
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=7a88c54e-d6a2-4613-9c39-df937267fed3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 7a88c54e-d6a2-4613-9c39-df937267fed3
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=7a88c54e-d6a2-4613-9c39-df937267fed3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 7a88c54e-d6a2-4613-9c39-df937267fed3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 7a88c54e-d6a2-4613-9c39-df937267fed3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d84cca7d4cca55c2
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=7a88c54e-d6a2-4613-9c39-df937267fed3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=89126291-0d44-495c-9b8f-b0bdc5da0251 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 362.6GB: boot/grub/core.img
 365.1GB: boot/grub/grub.cfg
 363.4GB: boot/initrd.img-2.6.31-20-generic
 363.4GB: boot/initrd.img-2.6.32-22-generic
 363.1GB: boot/vmlinuz-2.6.31-20-generic
 363.3GB: boot/vmlinuz-2.6.32-22-generic
 363.4GB: initrd.img
 363.4GB: initrd.img.old
 363.3GB: vmlinuz
 363.1GB: vmlinuz.old
```Thx for your help guys.

---

### Post by oldfred on 2010-06-17
You installed grub to the windows partitions, which it needs to boot windows.

Boot sector info:  Grub 2 is installed in the boot sector of sda1 

See my previous post for the fix. If that does not work then there are some windows repairs that may work.

---

### Post by raptor1770 on 2010-06-17
> **oldfred said:**
> If in your upgrade you installed grub to the partitions (not drives) then you over wrote the part of windows that is in the windows partition's boot sector.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If that does not work post the boot script info that wilee-nilee recommended.

This fixed it.

Thanks again for everyones help. Now that everything is working again I can say that this was a fun learning experience :).

Peace

---

