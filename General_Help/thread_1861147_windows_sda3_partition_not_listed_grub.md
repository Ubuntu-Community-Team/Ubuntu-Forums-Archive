---
title: "windows sda3 partition not listed: grub"
date: 2011-10-15
forum: General Help
---

### Post by linux_ent on 2011-10-15
I am using ubuntu 10.04.
Windows sda3 is not listed.

It lists only sda2 partiotion.

I ran boot_info_script.sh. Please find the o/p below

                Boot Info Script 0.55    dated February 15th, 2010

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
                       /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:

Type  :quit<Enter>  to exit Vim

---

### Post by Quackers on 2011-10-15
Welcome to UF :-)
What do you mean by "it's not listed"?
Do you mean in the grub menu? Have you opened up a terminal and run ```
sudo update-grub
```
Is the Windows Loader for sda3 recognised?

---

### Post by linux_ent on 2011-10-15
hey,

Thanks :)

Its not listed in the grub menu.
I tried update-grub but it doesn't recognize sda3.

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
Found Windows 7 (loader) on /dev/sda2
done

---

### Post by Quackers on 2011-10-15
Did you install grub to sda3 by any chance?
Please enclose the full output of the boot script in code tags in your next post. That will give us a clue.

---

### Post by linux_ent on 2011-10-15
Full o/p:                

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda4: _________________________________________________________________________

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
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

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

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2             206,848    30,926,847    30,720,000   7 HPFS/NTFS
/dev/sda3    *     30,926,848   360,858,287   329,931,440   7 HPFS/NTFS
/dev/sda4         360,861,694   625,141,759   264,280,066   f W95 Ext d (LBA)
/dev/sda5         360,861,696   594,421,759   233,560,064   7 HPFS/NTFS
/dev/sda6         594,423,808   621,234,175    26,810,368  83 Linux
/dev/sda7         621,236,224   625,141,759     3,905,536  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DELLUTILITY                   
/dev/sda2        CC70378A703779F2                       ntfs       Recovery                      
/dev/sda3        AC7C4EC27C4E86D4                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3248D99748D95A65                       ntfs       Sowmya's Docs                 
/dev/sda6        2cfb834d-0327-438e-adc9-1f728160300e   ext4                                     
/dev/sda7        1a8485db-a90c-42d4-a8ec-aff00bbb3c90   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /edrive                  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=================== sda3: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set 2cfb834d-0327-438e-adc9-1f728160300e
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
search --no-floppy --fs-uuid --set 2cfb834d-0327-438e-adc9-1f728160300e
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2cfb834d-0327-438e-adc9-1f728160300e
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=2cfb834d-0327-438e-adc9-1f728160300e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2cfb834d-0327-438e-adc9-1f728160300e
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=2cfb834d-0327-438e-adc9-1f728160300e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2cfb834d-0327-438e-adc9-1f728160300e
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=2cfb834d-0327-438e-adc9-1f728160300e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2cfb834d-0327-438e-adc9-1f728160300e
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=2cfb834d-0327-438e-adc9-1f728160300e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2cfb834d-0327-438e-adc9-1f728160300e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2cfb834d-0327-438e-adc9-1f728160300e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set CC70378A703779F2
    chainloader +1
}
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
UUID=2cfb834d-0327-438e-adc9-1f728160300e /               ext4    errors=remount-ro 0       1
# /edrive was on /dev/sda5 during installation
UUID=3248D99748D95A65 /edrive         ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda7 during installation
UUID=1a8485db-a90c-42d4-a8ec-aff00bbb3c90 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 309.1GB: boot/grub/core.img
 309.4GB: boot/grub/grub.cfg
 309.5GB: boot/initrd.img-2.6.32-28-generic
 310.0GB: boot/initrd.img-2.6.32-33-generic
 309.2GB: boot/vmlinuz-2.6.32-28-generic
 309.5GB: boot/vmlinuz-2.6.32-33-generic
 310.0GB: initrd.img
 309.5GB: initrd.img.old
 309.5GB: vmlinuz
 309.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 d8 eb 0d 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 d8  eb 0d 00 20 99 01 00 00  |........... ....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Quackers on 2011-10-15
Thanks.
As you can see, in sda3 the entry in red should not be there. ```
sda3: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe
[COLOR="Red"]/boot/grub/core.img[/COLOR]
```
It may be enough if you boot into Ubuntu and then navigate to the root of your Windows partition and delete the folder named "boot", which will have the folder called "grub" in it which will have the file called "core.img" in it. This "boot" folder may be inside the "Boot" folder, or maybe not.

*** NOTE ***
DO NOT delete the folder Boot - only the folder named boot (no capital B).

Then try running sudo update-grub again and see if the Windows Loader for sda3 is recognised.
If it isn't you will need to repair the Windows bootloader with a Vista repair disc or installation disc, then, once Windows is booting normally, re-install grub to the mbr of the drive.

---

### Post by linux_ent on 2011-10-15
Thanks a lot [I]Quackers.
Deleting boot folder worked.

Thanks again!
[/I]

---

### Post by Quackers on 2011-10-15
Excellent, and well done  :-)
I thought it might be enough as the partition type had remained as NTFS.

Please mark the thread as solved using Thread Tools near the top of the page.

---

