---
title: "Cant boot vista after 10.04 upgrade. Vista ubuntu dual boot."
date: 2010-06-30
forum: General Help
---

### Post by indrewjones0870 on 2010-06-30
Hi There, im kinda a noob at linux but am decent with computers. I
recently booted into linux from 9.10 and upgraded to 10.04.  i was
running a vista dual boot with 9.10 and everything worked fine. When
linux asked where to install grub it said "if you dont know check all partitions "or something.so i did. i tried to boot back into windows and now it wont work, all i get is a blinking cursor. Any help would be greatly appreciated.
Thanks

---

### Post by oldfred on 2010-06-30
No the instructions said to install to all drives and do not install to any partitions but then presented a confusing list mixing drives and partitions.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Kansasnoob bug report:
[http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)
[https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.1](https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.1)

---

### Post by indrewjones0870 on 2010-06-30
Hi, Thanks for the reply. Unfortunately i have already tried that with no luck. I have seen a lot of people posting outputs of boot info script. Im not sure how to run this....

---

### Post by drs305 on 2010-06-30
> **indrewjones0870 said:**
> Hi, Thanks for the reply. Unfortunately i have already tried that with no luck. I have seen a lot of people posting outputs of boot info script. Im not sure how to run this....

Have you been to the site and downloaded the boot info script file? It's located here, as well as instructions:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

If your Downloads go to your Desktop, the commands to run it would be:
Open a terminal (Applications, Accessories, Terminal).
```

cd ~/Desktop
sudo bash ~/Desktop/boot_info_script055.sh 

```

Post the results here. Click on the # icon in the post's menu to generate [noparse]**```

```**[/noparse] tags. Then paste the contents of the RESULTS.txt between the tags.

---

### Post by indrewjones0870 on 2010-07-01
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 405983253 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

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

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 405994981 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    23,246,054    23,245,992   7 HPFS/NTFS
/dev/sda2    *     23,246,055   327,950,909   304,704,855   7 HPFS/NTFS
/dev/sda3         327,950,910   488,392,064   160,441,155   5 Extended
/dev/sda5         359,309,853   483,042,419   123,732,567  83 Linux
/dev/sda6         483,042,483   488,392,064     5,349,582  82 Linux swap / Solaris
/dev/sda7         327,951,036   357,896,069    29,945,034  83 Linux
/dev/sda8         357,896,133   359,309,789     1,413,657  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3A043E77043E366B                       ntfs       RECOVERY                      
/dev/sda2        FCF81A6AF81A2384                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        65337ef6-5a0c-424a-b753-27bb0ea3a1e2   ext4                                     
/dev/sda6        418c9ef8-298f-4df9-b35c-0c85a8bab911   swap                                     
/dev/sda7        b773b520-03e6-4221-a129-1be281ad67b5   ext4                                     
/dev/sda8        83c09a0f-3e55-451c-9e84-e1d472c1c155   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        C02CD60C2CD5FD7A                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /media/b773b520-03e6-4221-a129-1be281ad67b5 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/FCF81A6AF81A2384_ fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/C02CD60C2CD5FD7A_ fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
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
search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
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
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3a043e77043e366b
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set fcf81a6af81a2384
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set b773b520-03e6-4221-a129-1be281ad67b5
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b773b520-03e6-4221-a129-1be281ad67b5 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set b773b520-03e6-4221-a129-1be281ad67b5
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b773b520-03e6-4221-a129-1be281ad67b5 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=418c9ef8-298f-4df9-b35c-0c85a8bab911 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 190.9GB: boot/grub/core.img
 184.4GB: boot/grub/grub.cfg
 184.9GB: boot/initrd.img-2.6.31-14-generic
 185.0GB: boot/initrd.img-2.6.32-22-generic
 184.5GB: boot/vmlinuz-2.6.31-14-generic
 184.7GB: boot/vmlinuz-2.6.32-22-generic
 185.0GB: initrd.img
 184.9GB: initrd.img.old
 184.7GB: vmlinuz
 184.5GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set b773b520-03e6-4221-a129-1be281ad67b5
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set b773b520-03e6-4221-a129-1be281ad67b5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b773b520-03e6-4221-a129-1be281ad67b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set b773b520-03e6-4221-a129-1be281ad67b5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b773b520-03e6-4221-a129-1be281ad67b5 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 3a043e77043e366b
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set fcf81a6af81a2384
    chainloader +1
}
menuentry "'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=b773b520-03e6-4221-a129-1be281ad67b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=83c09a0f-3e55-451c-9e84-e1d472c1c155 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 170.3GB: boot/grub/core.img
 170.4GB: boot/grub/grub.cfg
 170.3GB: boot/initrd.img-2.6.31-14-generic
 170.3GB: boot/vmlinuz-2.6.31-14-generic
 170.3GB: initrd.img
 170.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by oldfred on 2010-07-01
If sda2 is your main windows partition, then you are missing:
/Windows/System32/winload.exe Or was this in another partition?

Please check that the windows and under windows the system32 partitions are still there.

---

### Post by indrewjones0870 on 2010-07-03
Ok. Windows is on my sda2 partition im pretty sure. And how might i  check that windows under the system32 partitions are still there?

---

### Post by lindsay7 on 2010-07-03
This fixed a similar issue with my comp.

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by Seanlol on 2010-07-03
> **indrewjones0870 said:**
> Ok. Windows is on my sda2 partition im pretty sure. And how might i  check that windows under the system32 partitions are still there?

The easy way is booting into a Live CD and trying to access your system32 files.

---

### Post by oldfred on 2010-07-03
From the liveCD you can look at your windows partition sda2 and drill down to the windows then the windows/system32 and look for the winload.exe file. If the folders are missing then you have even bigger problems.

---

### Post by indrewjones0870 on 2010-07-06
What would be the best way to do that?...I was running vista first, then installed Linux. I updated Linux to 10.04 and when it asked where to install grub, i didn't know so i checked all partitions.(STUPID!) Im guessing that it overwrote something that windows needs to boot. Now when i try to boot into windows, all i get is a blinking cursor on the top left of the screen.Iv re-installed grub, but i think i need to replace whatever got overwritten in windows.Any help or tips on this?

---

### Post by oldfred on 2010-07-06
I do not know if this will replace a missing .exe file, if that is the case or did the script not show it. That has not been a normal repair issue.

Vista or 7 repair
Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by indrewjones0870 on 2010-07-07
Ok.....so i have already done this, but i did it again just to see if it would work.....no luck. I have a few things to say.... So, when i went into recovery mode or whatever.. where it asks to select your operating system, mine wasnt there...before when i tried this, it was. i am also not able to load the drivers.Thats number one. When i was in command prompt, the /fixboot and /rebuildbcd commands were not working. Also the bcdedit /export c:\bcd_backup command did not work. i think they all said no element found after hitting enter. I also tried the bootsect command with no luck.On a side note, when i boot into linux it only works in failsafe gnome mode. I am booting into linux from a super grub disk as well. Anyhelp would be appreciated, if anyone needs more info on my problem just ask because im not sure what you need to know.
Thanks.

---

### Post by indrewjones0870 on 2010-07-07
Ok.....so i have already done this, but i did it again just to see if it would work.....no luck. I have a few things to say.... So, when i went into recovery mode or whatever.. where it asks to select your operating system, mine wasnt there...before when i tried this, it was. i am also not able to load the drivers.Thats number one. When i was in command prompt, the /fixboot and /rebuildbcd commands were not working. Also the bcdedit /export c:\bcd_backup command did not work. i think they all said no element found after hitting enter. I also tried the bootsect command with no luck.On a side note, when i boot into linux it only works in failsafe gnome mode. I am booting into linux from a super grub disk as well. Anyhelp would be appreciated, if anyone needs more info on my problem just ask because im not sure what you need to know.
Thanks.

---

### Post by oldfred on 2010-07-07
When in Ubuntu do you see the rest of your windows install in sda2? Particularly the /windows and /windows/system32 folders?

If supergrub is getting you to boot you should boot and then reinstall grub from inside Ubuntu.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

---

### Post by indrewjones0870 on 2010-07-08
Yes i have already done this... When i try to fix windows it overwrites grub. so i boot Linux from supergrub then i just re-install grub. this whole problem was caused by a lack of understanding when installing grub for the 10.04 update.

---

