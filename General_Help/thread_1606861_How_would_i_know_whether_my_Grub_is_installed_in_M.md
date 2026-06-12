---
title: "How would i know whether my Grub is installed in MBR or where..?"
date: 2010-10-27
forum: General Help
---

### Post by tajiknomi on 2010-10-27
[SIZE=2]*i have **dual-boot** on my Pc (**Ubuntu & Kubuntu)***[/SIZE],[SIZE=2]Both are on different drives.
last time i was trying to remove[/SIZE][SIZE=2] my **Kubuntu-**drive ,after Formatting i reboot my **pc**,, then it shows me the **message** like **grub error** or **similar** error(I forgot..)
now i have again my **Dual-boot**(Gnome=KDE),and if i remove one of them ,what step should i kept in mind(so that i can't lose my Grub again...)...?

moreover,i want to know the ***location of My grub***..in file-sys i found the File name=menu.list and in some tutorial i have studied that this menu help for rearranging the position or 4 Windows boot help,but when i open my MENU.LIST i found no names of my OS as a title...


Sorry 4 my Bad-English..

[/SIZE]

---

### Post by Quackers on 2010-10-27
Run the boot info script from the site below and paste the contents of the results.txt file between code tags. Or just have a look at the very first entry in the file

ttp://bootinfoscript.sourceforge.net/

---

### Post by tajiknomi on 2010-10-27
[SIZE=2][I]Thanks for the meaningful link..:P

**output of Result.text is:-**

 Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

and many more...but i didn't attached anymore...

[/I][/SIZE]

---

### Post by Quackers on 2010-10-27
If you click on New Reply and then on the # symbol in the toolbar you can then paste the whole contents of results.txt file in between the generated CODE tags. This will make a box surrounding your file and include a scroll bar.
It appears that grub is installed in the MBR of /dev/sda (this will be grub2 if you are using Lucid Lynx - which does not use the menu.list file)
If you remove Windows you can just run 
```
sudo update-grub
```
from within Ubuntu. If you remove Ubuntu you would need to repair the Windows MBR with a Windows repair disc as grub is not removed from the MBR with Ubuntu.

---

### Post by tajiknomi on 2010-10-27
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    94,092,704    94,092,642   7 HPFS/NTFS
/dev/sda2          94,092,766   390,716,864   296,624,099   5 Extended
/dev/sda5          94,092,768   198,948,959   104,856,192   7 HPFS/NTFS
/dev/sda6         303,805,278   390,716,864    86,911,587  83 Linux
/dev/sda7         301,443,072   303,804,415     2,361,344  82 Linux swap / Solaris
/dev/sda8         198,950,912   301,426,687   102,475,776  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        71C9C32D0D73D38C                       ntfs       My Data                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        232D470307EF2C88                       ntfs       My Media                      
/dev/sda6        dbbcf002-b08d-4530-b108-8ad7c04f845f   ext3       KDE                           
/dev/sda7        ddb78a4b-357b-48db-a42a-6cc8448fe0f4   swap                                     
/dev/sda8        93a73f23-04a7-4ed2-afb9-bff7fffa66ca   ext3       Gnome                         
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext3       (rw,errors=remount-ro)
/dev/sda5        /media/My Media          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/My Data           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set dbbcf002-b08d-4530-b108-8ad7c04f845f
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
search --no-floppy --fs-uuid --set dbbcf002-b08d-4530-b108-8ad7c04f845f
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set dbbcf002-b08d-4530-b108-8ad7c04f845f
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=dbbcf002-b08d-4530-b108-8ad7c04f845f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set dbbcf002-b08d-4530-b108-8ad7c04f845f
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=dbbcf002-b08d-4530-b108-8ad7c04f845f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set dbbcf002-b08d-4530-b108-8ad7c04f845f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=dbbcf002-b08d-4530-b108-8ad7c04f845f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set dbbcf002-b08d-4530-b108-8ad7c04f845f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=dbbcf002-b08d-4530-b108-8ad7c04f845f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set dbbcf002-b08d-4530-b108-8ad7c04f845f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set dbbcf002-b08d-4530-b108-8ad7c04f845f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda" {
    insmod ext2
    set root='(hd0,'
    search --no-floppy --fs-uuid --set 93a73f23-04a7-4ed2-afb9-bff7fffa66ca
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda" {
    insmod ext2
    set root='(hd0,'
    search --no-floppy --fs-uuid --set 93a73f23-04a7-4ed2-afb9-bff7fffa66ca
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda" {
    insmod ext2
    set root='(hd0,'
    search --no-floppy --fs-uuid --set 93a73f23-04a7-4ed2-afb9-bff7fffa66ca
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda" {
    insmod ext2
    set root='(hd0,'
    search --no-floppy --fs-uuid --set 93a73f23-04a7-4ed2-afb9-bff7fffa66ca
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca ro single
    initrd /boot/initrd.img-2.6.32-21-generic
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
UUID=dbbcf002-b08d-4530-b108-8ad7c04f845f /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ddb78a4b-357b-48db-a42a-6cc8448fe0f4 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 180.7GB: boot/grub/core.img
 180.6GB: boot/grub/grub.cfg
 180.7GB: boot/initrd.img-2.6.32-24-generic
 180.6GB: boot/initrd.img-2.6.32-25-generic
 180.6GB: boot/vmlinuz-2.6.32-24-generic
 180.6GB: boot/vmlinuz-2.6.32-25-generic
 180.6GB: initrd.img
 180.7GB: initrd.img.old
 180.6GB: vmlinuz
 180.6GB: vmlinuz.old

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
set root='(hd0,'
search --no-floppy --fs-uuid --set 93a73f23-04a7-4ed2-afb9-bff7fffa66ca
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
set root='(hd0,'
search --no-floppy --fs-uuid --set 93a73f23-04a7-4ed2-afb9-bff7fffa66ca
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,'
    search --no-floppy --fs-uuid --set 93a73f23-04a7-4ed2-afb9-bff7fffa66ca
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,'
    search --no-floppy --fs-uuid --set 93a73f23-04a7-4ed2-afb9-bff7fffa66ca
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,'
    search --no-floppy --fs-uuid --set 93a73f23-04a7-4ed2-afb9-bff7fffa66ca
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,'
    search --no-floppy --fs-uuid --set 93a73f23-04a7-4ed2-afb9-bff7fffa66ca
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,'
    search --no-floppy --fs-uuid --set 93a73f23-04a7-4ed2-afb9-bff7fffa66ca
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,'
    search --no-floppy --fs-uuid --set 93a73f23-04a7-4ed2-afb9-bff7fffa66ca
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,'
    search --no-floppy --fs-uuid --set 93a73f23-04a7-4ed2-afb9-bff7fffa66ca
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,
    search --no-floppy --fs-uuid --set 93a73f23-04a7-4ed2-afb9-bff7fffa66ca
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set dbbcf002-b08d-4530-b108-8ad7c04f845f
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=dbbcf002-b08d-4530-b108-8ad7c04f845f ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set dbbcf002-b08d-4530-b108-8ad7c04f845f
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=dbbcf002-b08d-4530-b108-8ad7c04f845f ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set dbbcf002-b08d-4530-b108-8ad7c04f845f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=dbbcf002-b08d-4530-b108-8ad7c04f845f ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set dbbcf002-b08d-4530-b108-8ad7c04f845f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=dbbcf002-b08d-4530-b108-8ad7c04f845f ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca /               ext3    errors=remount-ro 0       1
UUID=ddb78a4b-357b-48db-a42a-6cc8448fe0f4 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 146.5GB: boot/grub/core.img
 146.5GB: boot/grub/grub.cfg
 146.6GB: boot/initrd.img-2.6.32-21-generic
 146.6GB: boot/initrd.img-2.6.32-24-generic
 146.6GB: boot/initrd.img-2.6.32-25-generic
 146.5GB: boot/vmlinuz-2.6.32-21-generic
 146.5GB: boot/vmlinuz-2.6.32-24-generic
 146.6GB: boot/vmlinuz-2.6.32-25-generic
 146.6GB: initrd.img
 146.6GB: initrd.img.old
 146.6GB: vmlinuz
 146.5GB: vmlinuz.old
```

---

### Post by tajiknomi on 2010-10-27
[I]After removing kubuntu i will only use Sudo update-grub...?

[/I]

---

### Post by tajiknomi on 2010-10-27
[SIZE=2][I]Sorry i **mistakenly** didn't select #

moreover,m not using win...i am using **dual-boot (ubuntu and kubuntu**
[/I][/SIZE]

---

### Post by Quackers on 2010-10-27
Sorry, I saw 2 Windows partitions and assumed you were using Windows.
If you wanted to delete Ubuntu then you would boot into Kubuntu and delete the Ubuntu partitions then run sudo update grub.
And do it the other way round to delete Kubuntu.

---

### Post by tajiknomi on 2010-10-27
[SIZE=2]*thanks brother..:guitar:*[/SIZE]

---

### Post by Quackers on 2010-10-27
You're welcome :-)
I too was shocked when getting a boot failure after I deleted one of the Ubuntu installations and didn't run sudo update-grub before I rebooted :-)

---

### Post by tajiknomi on 2010-10-27
[SIZE=2]*me too....:P*[/SIZE]

---

