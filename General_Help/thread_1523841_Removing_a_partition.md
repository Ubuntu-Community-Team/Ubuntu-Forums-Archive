---
title: "Removing a partition"
date: 2010-07-04
forum: General Help
---

### Post by donut123 on 2010-07-04
I have 2 Ubuntu 10.04 on my old computer...along with XP...how do I remove one Ubuntu ?

---

### Post by 91corradotdi on 2010-07-04
Bump on this one. I have Ubuntu and mint side by side. I would like to get rid of Mint and not effect Ubuntu. is this possible or will it require a fresh install

---

### Post by Nytram on 2010-07-04
> **donut123 said:**
> I have 2 Ubuntu 10.04 on my old computer...along with XP...how do I remove one Ubuntu ?

Just to clarify - did you actually install 2 different versions of Ubuntu, or are you referring to 2 menu entries when the computer boots?

---

### Post by gadolinio on 2010-07-04
> **Nytram said:**
> Just to clarify - did you actually install 2 different versions of Ubuntu, or are you referring to 2 menu entries when the computer boots?
Good point.


> **donut123 said:**
> I have 2 Ubuntu 10.04 on my old computer...along with XP...how do I remove one Ubuntu ?
> **91corradotdi said:**
> I have Ubuntu and mint side by side. I would like to get rid of Mint and not effect Ubuntu.
 What do you have installed?
ubuntu + ubuntu + XP ?
ubuntu + mint?

---

### Post by donut123 on 2010-07-04
Someone deleted my post from today...Im posting it again.
How do i remove one Ubuntu from my partitions?
I installed 2 on an emergency...and now I want to remove one.

---

### Post by donut123 on 2010-07-04
I have Windows XP..and then I installed Ubuntu 10.04...then I messed around with the partitions. After that..my machine would not boot. All I thought of was to install another Ubuntu 10.04...so now I have 2 Ubuntus..and XP...How do I remove one Ubuntu?

---

### Post by donut123 on 2010-07-04
I have these on my older computer...I also have Ultimate Edition on my newer machine...2.7 and 2.8 Alpha 1...no one can tel me how to remove one. I am sure there is a way. 
On my older machine  I wish to remove one Ubuntu 10.04..how is it possible?
Thank you

---

### Post by WorMzy on 2010-07-04
Removing a partition is childs play. Making sure it doesn't make your system (temporarily) unbootable is another. Can you post the output of the boot info script (found [here]("http://sourceforge.net/projects/bootinfoscript/"))

---

### Post by donut123 on 2010-07-04
> **donut123 said:**
> I have these on my older computer...I also have Ultimate Edition on my newer machine...2.7 and 2.8 Alpha 1...no one can tel me how to remove one. I am sure there is a way. 
On my older machine  I wish to remove one Ubuntu 10.04..how is it possible?
Thank you
I tried Mint at one time...i didnt like it too well.
I tried many OS..from Linux...i like Ultimate the most.

---

### Post by donut123 on 2010-07-04
> **WorMzy said:**
> Removing a partition is childs play. Making sure it doesn't make your system (temporarily) unbootable is another. Can you post the output of the boot info script (found [here]("http://sourceforge.net/projects/bootinfoscript/")) I will try it thank you

---

### Post by ieee488 on 2010-07-04
removing a partition is easy; Gparted would work
but you will also have to update Grub so that it deletes the other Ubuntu choice; search on updating Grub

---

### Post by lisati on 2010-07-04
Threads merged.

If you want to find your posts, click on the "search"->"find all your posts"

---

### Post by donut123 on 2010-07-04
> **donut123 said:**
> I will try it thank you
it didnt work...what else can i try ?
I mean the partitions...the script did not do anything...

---

### Post by donut123 on 2010-07-04
Im not getting anywhere with this...where else can i go to get a solid answer?
I think I will just leave it on there..since no one knows how to do it... thank you for your efforts...

---

### Post by donut123 on 2010-07-04
I see ones dont know what they are doing on here either..its just trial and error....by the time a dude gets done His whole OS is  a mess.

---

### Post by WorMzy on 2010-07-04
What do you mean it didn't work? Run the script and post the contents of results.txt here.

The instructions for running the script are found [here]("http://bootinfoscript.sourceforge.net/").

The output of the script will help us tell you exactly how to proceed. Without it, we're flying blind. Randomly throwing commands at partitions and hoping it'll all work out okay is not a good idea.

---

### Post by donut123 on 2010-07-05
see it doent work..
steven@Donut123:~$  sudo bash boot_info_script055.sh
bash: boot_info_script055.sh: No such file or directory
steven@Donut123:~$ su -
Password: 
su: Authentication failure
steven@Donut123:~$ sudo bash boot_info_script055.sh
bash: boot_info_script055.sh: No such file or directory
steven@Donut123:~$ #     sudo bash boot_info_script055.sh
steven@Donut123:~$ 


> **WorMzy said:**
> What do you mean it didn't work? Run the script and post the contents of results.txt here.

The instructions for running the script are found [here]("http://bootinfoscript.sourceforge.net/").

The output of the script will help us tell you exactly how to proceed. Without it, we're flying blind. Randomly throwing commands at partitions and hoping it'll all work out okay is not a good idea.

---

### Post by donut123 on 2010-07-05
the contents isint allowed on here..
> **WorMzy said:**
> What do you mean it didn't work? Run the script and post the contents of results.txt here.

The instructions for running the script are found [here]("http://bootinfoscript.sourceforge.net/").

The output of the script will help us tell you exactly how to proceed. Without it, we're flying blind. Randomly throwing commands at partitions and hoping it'll all work out okay is not a good idea.

---

### Post by libssd on 2010-07-05
Is re-installing Ubuntu (or whatever version of Linux you like) an option? If so, during the install, choose manual partitioning, delete the unwanted partition, and reinstall Linux with as much space as you desire. Unless XP needs the space, I would not try to resize the XP partition; either dedicate the extra space to Linux, or leave it as free space.

In my experience, 8gb is the minimum practical; I normally use 32gb, with 2gb of swap if I want to use hibernate, otherwise 256mb swap.

---

### Post by donut123 on 2010-07-05
Look///I just want to remove both Ubuntus now.
And gparted is not showing windows..it just shows uallocated...
I want to remove both Ubuntus...how do i do it?
I just want XP on here...how do I do it ?


> **donut123 said:**
> the contents isint allowed on here..

---

### Post by donut123 on 2010-07-05
How do i remove both ubuntus and have xp only ?
I dont know all this...swap and things...the last time...i was not able to boot...this is how i ended up with 2 ubuntus... HOW DO I DO IT ? That is the question... please can you write it in simple form ?
I hope I did not outsult you...when i finish with this I promis I wont ask another question...and I will go away..
Thank you


> **libssd said:**
> is re-installing ubuntu (or whatever version of linux you like) an option? If so, during the install, choose manual partitioning, delete the unwanted partition, and reinstall linux with as much space as you desire. Unless xp needs the space, i would not try to resize the xp partition; either dedicate the extra space to linux, or leave it as free space.

In my experience, 8gb is the minimum practical; i normally use 32gb, with 2gb of swap if i want to use hibernate, otherwise 256mb swap.

---

### Post by libssd on 2010-07-05
If you have XP backup or reinstall discs, just reinstall XP. If you didn't make a restorable XP backup before installing Ubuntu, I don't know enough about XP to provide any advice; you may need to ask in a Windows forum.

---

### Post by donut123 on 2010-07-05
> **libssd said:**
> If you have XP backup or reinstall discs, just reinstall XP. If you didn't make a restorable XP backup before installing Ubuntu, I don't know enough about XP to provide any advice; you may need to ask in a Windows forum.
Well its too far gone into it...I have alot of files and programs on it. And Wndows is killing XP...I dont trust it right now to do that..thanks..

---

### Post by 91corradotdi on 2010-07-05
here is mine on removing mint and leaving ubuntu. it was not difficult getting this info I just don't want to mess up my ubuntu trying to get rid of Mint. sorry to hack into your thread but it was close to my question. after looking at mine it looks like there is a windows system. if so delete it to. it does not show in boot up menu. 

      Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 603711 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
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
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 273783 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    47,651,575    47,651,513  83 Linux
/dev/sda2          47,652,862    78,156,224    30,503,363   5 Extended
/dev/sda5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris
/dev/sda6          47,652,864    73,621,503    25,968,640  83 Linux
/dev/sda7          73,623,552    74,862,591     1,239,040  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059349504 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1977 MB, 1977614336 bytes
64 heads, 63 sectors/track, 957 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 135     3,858,623     3,858,489   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e2d3a558-886c-4805-8e38-cc8a3502924a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        4bb0de8e-7819-4e42-b5c9-8c6ef940a905   swap                                     
/dev/sda6        e0dc9454-e3ac-4df8-baea-a00223bbd3de   ext4                                     
/dev/sda7        b09e235c-7c3d-412f-a89a-1b0d143068e9   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        30F47686F4764E5A                       ntfs       SimpleDrive                   
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        6661-3430                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/SimpleDrive       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/usb0              vfat       (rw,noexec,nodev,sync,noatime,nodiratime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e2d3a558-886c-4805-8e38-cc8a3502924a
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e2d3a558-886c-4805-8e38-cc8a3502924a
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e2d3a558-886c-4805-8e38-cc8a3502924a
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=e2d3a558-886c-4805-8e38-cc8a3502924a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e2d3a558-886c-4805-8e38-cc8a3502924a
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=e2d3a558-886c-4805-8e38-cc8a3502924a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e2d3a558-886c-4805-8e38-cc8a3502924a
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=e2d3a558-886c-4805-8e38-cc8a3502924a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e2d3a558-886c-4805-8e38-cc8a3502924a
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=e2d3a558-886c-4805-8e38-cc8a3502924a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e2d3a558-886c-4805-8e38-cc8a3502924a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e2d3a558-886c-4805-8e38-cc8a3502924a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e2d3a558-886c-4805-8e38-cc8a3502924a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e2d3a558-886c-4805-8e38-cc8a3502924a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e2d3a558-886c-4805-8e38-cc8a3502924a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e2d3a558-886c-4805-8e38-cc8a3502924a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda6) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set e0dc9454-e3ac-4df8-baea-a00223bbd3de
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e0dc9454-e3ac-4df8-baea-a00223bbd3de ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda6) -- recovery mode (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set e0dc9454-e3ac-4df8-baea-a00223bbd3de
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e0dc9454-e3ac-4df8-baea-a00223bbd3de ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e2d3a558-886c-4805-8e38-cc8a3502924a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4bb0de8e-7819-4e42-b5c9-8c6ef940a905 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .3GB: boot/grub/core.img
   2.6GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.32-21-generic
   1.1GB: boot/initrd.img-2.6.32-22-generic
   1.2GB: boot/initrd.img-2.6.32-23-generic
   1.0GB: boot/vmlinuz-2.6.32-21-generic
   1.1GB: boot/vmlinuz-2.6.32-22-generic
   1.2GB: boot/vmlinuz-2.6.32-23-generic
   1.2GB: initrd.img
   1.1GB: initrd.img.old
   1.2GB: vmlinuz
   1.1GB: vmlinuz.old

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
search --no-floppy --fs-uuid --set e0dc9454-e3ac-4df8-baea-a00223bbd3de
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
search --no-floppy --fs-uuid --set e0dc9454-e3ac-4df8-baea-a00223bbd3de
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set e0dc9454-e3ac-4df8-baea-a00223bbd3de
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
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda6)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set e0dc9454-e3ac-4df8-baea-a00223bbd3de
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e0dc9454-e3ac-4df8-baea-a00223bbd3de ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda6) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set e0dc9454-e3ac-4df8-baea-a00223bbd3de
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e0dc9454-e3ac-4df8-baea-a00223bbd3de ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set e0dc9454-e3ac-4df8-baea-a00223bbd3de
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set e0dc9454-e3ac-4df8-baea-a00223bbd3de
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e2d3a558-886c-4805-8e38-cc8a3502924a
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=e2d3a558-886c-4805-8e38-cc8a3502924a ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e2d3a558-886c-4805-8e38-cc8a3502924a
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=e2d3a558-886c-4805-8e38-cc8a3502924a ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e2d3a558-886c-4805-8e38-cc8a3502924a
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e2d3a558-886c-4805-8e38-cc8a3502924a ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e2d3a558-886c-4805-8e38-cc8a3502924a
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e2d3a558-886c-4805-8e38-cc8a3502924a ro single
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
UUID=e0dc9454-e3ac-4df8-baea-a00223bbd3de /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=b09e235c-7c3d-412f-a89a-1b0d143068e9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  26.6GB: boot/grub/core.img
  36.3GB: boot/grub/grub.cfg
  27.2GB: boot/initrd.img-2.6.32-21-generic
  26.9GB: boot/vmlinuz-2.6.32-21-generic
  27.2GB: initrd.img
  26.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  d8 7c 02 83 90 a4 00 00  00 0a 69 a7 96 e0 cb 9a  |.|........i.....|
00000010  53 5b 02 96 25 f1 88 5d  8a 7a b3 ba 77 98 24 d4  |S[..%..].z..w.$.|
00000020  6d 94 27 41 20 12 e1 ff  a2 36 09 f9 28 38 4a 1e  |m.'A ....6..(8J.|
00000030  4b 92 65 21 e0 64 4a 92  42 37 f2 70 c0 26 51 18  |K.e!.dJ.B7.p.&Q.|
00000040  70 e7 0f a3 90 7a 97 3f  19 63 06 4c 25 0b 85 c1  |p....z.?.c.L%...|
00000050  e4 54 6c 56 92 ff 8f 01  ce 1c b1 2b 1e 05 f3 7a  |.TlV.......+...z|
00000060  68 9c 31 ff e9 09 e0 c8  13 32 fa 63 90 e9 2e 92  |h.1......2.c....|
00000070  4b 7d 68 ff f9 28 4c 25  04 cc dd 48 2c dc 4c 0b  |K}h..(L%...H,.L.|
00000080  84 a2 8d ca 89 c8 17 ce  9a 12 66 7f ff d8 be f3  |..........f.....|
00000090  74 dc b8 85 76 37 4d 34  8c 92 40 c0 a0 9b 1e 62  |t...v7M4..@....b|
000000a0  f9 0e 49 ff ff ff f9 ac  01 17 57 12 80 00 01 0a  |..I.......W.....|
000000b0  7b 6d 75 17 16 90 5e f9  61 cc 22 d5 86 66 a8 ab  |{mu...^.a."..f..|
000000c0  cb 69 63 f0 e3 f3 1a 75  61 f1 11 50 a1 2a 9c 21  |.ic....ua..P.*.!|
000000d0  0f be 6a 60 3d 05 21 08  01 99 22 71 5b 34 07 01  |..j`=.!..."q[4..|
000000e0  20 e5 89 8e d2 a3 69 e9  4d 65 89 8d b6 a4 fd 6e  | .....i.Me.....n|
000000f0  2d 2e e5 fd 35 65 e2 f4  6b 83 3d 34 4f 9e ae ea  |-...5e..k.=4O...|
00000100  f1 94 a9 8c 58 74 e1 78  6a 66 8e e3 b1 b7 fb 45  |....Xt.xjf.....E|
00000110  f7 5a 47 68 d5 53 6a 64  c2 38 9d c8 8b e6 1f 4b  |.ZGh.Sjd.8.....K|
00000120  9a eb fe aa 25 e9 06 9a  46 f2 c3 ff fc c3 58 ff  |....%...F.....X.|
00000130  fa 92 44 83 8f e3 00 04  c5 5d 5b ee 3e 01 06 a6  |..D......][.>...|
00000140  2c cb 7c cc 34 22 91 a9  91 5d 99 94 00 02 a4 43  |,.|.4"...].....C|
00000150  2b bb 32 80 00 4b fe 2a  11 16 e8 00 04 35 48 71  |+.2..K.*.....5Hq|
00000160  23 02 00 20 10 25 20 41  02 2e 6e 06 b7 50 dc 11  |#.. .% A..n..P..|
00000170  92 e2 fd 52 db ad 2d 76  da 66 a0 07 46 1b 11 06  |...R..-v.f..F...|
00000180  91 05 8e 61 08 7b 4b a5  40 72 0e 84 20 2c c9 0b  |...a.{K.@r.. ,..|
00000190  2b a8 3c 11 08 2c 36 2d  8c aa ee 75 95 85 f8 76  |+.<..,6-...u...v|
000001a0  a8 a4 57 49 66 64 d9 de  2a 35 b5 fb e9 98 83 1e  |..WIfd..*5......|
000001b0  d2 aa a9 9d aa da 4e c8  e6 98 89 47 57 47 00 fe  |......N....GWG..|
000001c0  ff ff 82 fe ff ff 75 31  9f 01 4e 40 32 00 00 fe  |......u1..N@2...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 40 8c 01 00 00  |...........@....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by 2hot6ft2 on 2010-07-05
For donut
Here's both ways. Removing UE will leave it unbootable so read it all before you begin, you'll need your xp disc.

Boot the 2.7 livedvd and go to
System > Administration > GParted
Right click on the swap partition and select swapoff
Select any other partition that is locked and select unmount

Now delete what you want to delete. Then

[COLOR="DarkGreen"][SIZE="3"]To remove one of the UE's and still have a dual boot.[/SIZE][/COLOR]
Here assuming the UE partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).

run:
```
sudo -i
```
To find out you partitions run
```
fdisk -l
```
Use that info for the following
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if you don't have a separate /boot partition
```
You'll want to install grub to the drive that is first in the boot order in the BIOS
```
grub-install --root-directory=/mnt/ /dev/sda
```
Reboot removing the livecd in the process and once you're back in ubuntu run
```
sudo update-grub
```

[COLOR="DarkGreen"][SIZE="3"]Now if all you want is windows left[/SIZE][/COLOR] delete all but the windows partition.
At this point your pc is unbootable. So before you do it make sure you have your xp disc then

Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

That will fix XP right up :)

Now once you're in xp you can resize the partition to take up the whole drive or whatever you want to do. Naturally you will have to reboot and wait for it to do the resizing.


Take care donut.
:popcorn:

---

### Post by donut123 on 2010-07-05
Hey man you didnt have to do this. However ..if i do all this... first it is the default Ubuntus i have on it...2 10.04..and xp..it is my older machine. i use it to store things. To recover does it mean all that will still be on? If not I probably would be better off to reinstall the xp. If i can keep all the files I have it would be good. If not i will have to remove all the files and dont have a place for them. i do have a machine with windows 98..but the hard drive is small..so small it wont even hold the first ubuntu...very poor ..but it will hold some files.
Will the xp restore the files I already have on it? That is the question..?
Thanks 2hot6ft2...I appreciate it..and I owe you another cool gif....:KS

---

### Post by donut123 on 2010-07-05
> **2hot6ft2 said:**
> Here's both ways. Removing UE will leave it unbootable so read it all before you begin, you'll need your xp disc.

Boot the 2.7 livedvd and go to
System > Administration > GParted
Right click on the swap partition and select swapoff
Select any other partition that is locked and select unmount

Now delete what you want to delete. Then

[COLOR=DarkGreen][SIZE=3]To remove one of the UE's and still have a dual boot.[/SIZE][/COLOR]
Here assuming the UE partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).

run:
```
sudo -i
```To find out you partitions run
```
fdisk -l
```Use that info for the following
```
mount /dev/sda8 /mnt
``````
mount /dev/sda6 /mnt/boot  #skip this one if you don't have a separate /boot partition
```You'll want to install grub to the drive that is first in the boot order in the BIOS
```
grub-install --root-directory=/mnt/ /dev/sda
```Reboot removing the livecd in the process and once you're back in ubuntu run
```
sudo update-grub
```[COLOR=DarkGreen][SIZE=3]Now if all you want is windows left[/SIZE][/COLOR] delete all but the windows partition.
At this point your pc is unbootable. So before you do it make sure you have your xp disc then

Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

That will fix XP right up :)

Now once you're in xp you can resize the partition to take up the whole drive or whatever you want to do. Naturally you will have to reboot and wait for it to do the resizing.


Take care donut.
:popcorn:
hey buddy..i got this for you...hope you like it..

---

### Post by 2hot6ft2 on 2010-07-05
No problem you wanted to know how to do it and that's what I do. I like this gif and I don't know how you could top it.

You mean doing this part?
> Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.
It will just repair the MBR so xp will boot and it will eliminate grub. It wont reinstall xp so everything should still be there and working.
You should always backup everything you can, no matter what OS you use or work on it can't be said enough. Backup, backup, backup.
:popcorn:
I would take that 98 machine and install Lubuntu on it and sell it to someone cheap for them to learn on. That's what I did with mine a few months ago but Lubuntu wasn't out yet so it went with Xubuntu.;)

LOL, someone has their name on that gif. Looks cool but it may be copyrighted. Thanks anyway I saved it. Might use it in an email or something.

---

### Post by WorMzy on 2010-07-05
Unfortunately, 91corradotdi, you will need to reinstall grub to the mbr before or after removing Mint if you want to boot Ubuntu (or any other OS.

This is fairly simple procedure, so lets do it before you remove Mint. Have a LiveCD handy in case something goes wrong.

[LIST]
[*]Boot into Ubuntu
[*]Open a terminal
[*]Run the following: ```
sudo grub-install /dev/sda
```
[LIST]
[*]If you get errors, then run ```
sudo grub-install --recheck /dev/sda
```
[/LIST]
[*]Then run the following ```
sudo update-grub
```
[/LIST]

Reboot your PC to verify that everything is working correctly, then boot into Ubuntu again.

Now, to remove Mint, run:
```
sudo apt-get install gparted && gksu gparted
```

You should be presented with a GUI listing all your partitions on sda, you want to right-click on /dev/sda6, then click delete, then click Apply.

If you get told to unmount any logical devices with a number higher than six, then right click on /dev/sda7, and choose Swapoff, then try again. You don't need two swaps anyway, not even when you used Mint. One swap partition can be used for multiple Linux installs. So feel free to delete /dev/sda7 too.

---

### Post by 91corradotdi on 2010-07-06
thank you so much it looks simple. i will let you know how it works when i get back in town.

---

### Post by donut123 on 2010-07-06
I deleted all the partitions...it would not boot...so i unstalled Ubuntu 10.04...again...now I have Ubuntu and XP ...Im happy with that. On this machine I have Ultimate 2.7...and Ultimate 2.8 Alpha..Im happy with that..im happy  so far. Thanks all...):P

---

### Post by donut123 on 2010-07-06
)

---

### Post by 91corradotdi on 2010-07-09
tried this and it boots up to ubuntu now just fine. why do I have unallocated space? can I free up this

---

### Post by audiomick on 2010-07-09
Hi.
The unallocated space will be where you have deleted partitions. The simple fix is to boot into the live cd, and start gparted from the. You should do this from the live cd because you can't resize partitions that are mounted, and you need to resize the partition that your linux is in.

When you have gparted running from the live cd, simply shrink the extended partition down to the size of the swap partition, then grow the ext4 partition, where your linux is, to take up the empty space.

---

### Post by donut123 on 2010-07-14
ok...think i did that...i have an unusal method...i do things wromg and then it comes out right !  #-o

---

