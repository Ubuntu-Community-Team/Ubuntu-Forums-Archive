---
title: "can't reinstall grub after reinstall of win 7"
date: 2010-12-05
forum: General Help
---

### Post by TeeRoy32 on 2010-12-05
hi i have ubuntu 10.04 64 bit installed and configured and working sweet. I have reinstalled windows 7 and now i can't boot ubuntu i've tried easybcd to add ubuntu to win boot loader which failed and tried to follow the instructions to reinstall grub through a live cd which i am in at the moment. i go to a terminal and type sudo grub and it brings up the grub prompt. i have mounted all discs and entered the command find /boot/grub/stage1 and it keeps spitting this back at me Error 15: File not found
my hd is a 80gb with partions like this
/dev/sda1 105mb ntfs system reserved
/dev/sda2 45gb ntfs win 7 home premium 64 bit
/dev/sda3 34gb ext4 ubuntu 10.04 64 bit
/dev/sda4 1.5gb linux swap
please help i'm a noob but can cut and paste into terminal and am unafraid

---

### Post by wilee-nilee on 2010-12-05
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

When and if we get to repairs no partitions should be mounted, so lets remember that you have had them mounted and your on the live cd as of now.

---

### Post by TeeRoy32 on 2010-12-06
g day done that heres the results

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    87,844,863    87,638,016   7 HPFS/NTFS
/dev/sda3          87,844,864   153,391,103    65,546,240  83 Linux
/dev/sda4         153,393,152   156,301,295     2,908,144  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B8C8CBC6C8CB80DC                       ntfs       System Reserved               
/dev/sda2        1EA0CE22A0CDFFEF                       ntfs                                     
/dev/sda3        7291a579-49b0-4f68-9d5f-8458ecd52621   ext4                                     
/dev/sda4        e28c5aed-1e1c-46c1-99ec-0b4b40df0e47   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D622DEFC22DEE113                       ntfs       Troys Stuff                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Troys Stuff       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/1EA0CE22A0CDFFEF  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/7291a579-49b0-4f68-9d5f-8458ecd52621 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 7291a579-49b0-4f68-9d5f-8458ecd52621
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
search --no-floppy --fs-uuid --set 7291a579-49b0-4f68-9d5f-8458ecd52621
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7291a579-49b0-4f68-9d5f-8458ecd52621
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7291a579-49b0-4f68-9d5f-8458ecd52621 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7291a579-49b0-4f68-9d5f-8458ecd52621
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7291a579-49b0-4f68-9d5f-8458ecd52621 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7291a579-49b0-4f68-9d5f-8458ecd52621
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7291a579-49b0-4f68-9d5f-8458ecd52621
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0e96cbe407a15bc4
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
    insmod fat
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 7e02-69d7
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7291a579-49b0-4f68-9d5f-8458ecd52621 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e28c5aed-1e1c-46c1-99ec-0b4b40df0e47 none            swap    sw              0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  49.4GB: boot/grub/core.img
  62.4GB: boot/grub/grub.cfg
  49.4GB: boot/initrd.img-2.6.32-21-generic
  49.4GB: boot/vmlinuz-2.6.32-21-generic
  49.4GB: boot/vmlinuz-2.6.32-26-generic
  49.4GB: initrd.img
  49.4GB: vmlinuz
```

---

### Post by TeeRoy32 on 2010-12-06
sdb is my storage drive

---

### Post by wilee-nilee on 2010-12-06
From this link here are the commands, from the live cd all partitions unmounted just running on the cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

```
sudo mount /dev/sda3 /mnt
```

then run

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

reboot to the Ubuntu install and open a terminal and run
```
sudo update-grub
```

---

### Post by TeeRoy32 on 2010-12-06
hi did what you said and i rebooted and it loaded to a command line with a grub prompt help!!!!!!!!!

---

### Post by TeeRoy32 on 2010-12-06
please any one

---

### Post by wilee-nilee on 2010-12-06
> **TeeRoy32 said:**
> hi did what you said and i rebooted and it loaded to a command line with a grub prompt help!!!!!!!!!

Just out of curiosity have you looked at gparted on the live cd to see if the sda3 partition looks normal?

the script looks normal and the commands should have worked if everything was in order. Problem I do see though is this line.
# / was on /dev/sda5 during installation

There is no sda5 anymore

If you have removed or added partitions while installing can you give a description of when and where.
> **TeeRoy32 said:**
> please any one
Just for the record here your not supposed to bump a thread for 24hrs so this last post makes me wonder of your panic may be a factor here as the commands should have worked.

---

### Post by TeeRoy32 on 2010-12-06
i looked in g parted and its all fine except theres a 1 meg unallocated space at the start and a 1 meg unallocated space between sda3 and sda 4

---

### Post by TeeRoy32 on 2010-12-06
i am panicing a little sorry i've been at it for 4 days trying to set up dual boot wiped my storage drive by mistake. so last night i wiped my boot drive and fresh installed ubuntu and reinstalled windows this morning

---

### Post by wilee-nilee on 2010-12-06
> **TeeRoy32 said:**
> i am panicing a little sorry i've been at it for 4 days trying to set up dual boot wiped my storage drive by mistake. so last night i wiped my boot drive and fresh installed ubuntu and reinstalled windows this morning

It is alright I would be a little stressed in your situation as well.;) There are other exsperienced user online and if they saw something they would post, and I am not hesitant to ask for their help as well, and always like good input.

Post the boot script again and please use the code tags this time. When you open the reply click on the # in the reply panel then paste the text between the tags.

---

### Post by sikander3786 on 2010-12-06
I would also be interested to see a fresh output of bootinfoscript as things must have changed a bit after **wilee-nilee's** commands for Grub re-install :-)

---

### Post by mr.farenheit on 2010-12-06
i had this happen once. windows installer likes to delete things its not familiar with. when i had this problem, i decreased the windows partition a bit and then did a clean reinstall of ubuntu. don't know how it worked exactly but it did. could try in the ubuntu installer to delete the partition with windows loader. then with the clean install of ubuntu allow grub to take over.

---

### Post by wilee-nilee on 2010-12-06
> **mr.farenheit said:**
> i had this happen once. windows installer likes to delete things its not familiar with. when i had this problem, i decreased the windows partition a bit and then did a clean reinstall of ubuntu. don't know how it worked exactly but it did. could try in the ubuntu installer to delete the partition with windows loader. then with the clean install of ubuntu allow grub to take over.

I had to use a super grub disc about a month ago to get my Maverick going again, none of the commands even brought me to more then a black screen, and I know this little bit pretty well.

---

### Post by TeeRoy32 on 2011-06-05
I'm gonna kill this thread, I've been away, problem solved, I use Bios to boot different O.S, disconnect unwanted drive on install so ubuntu and windows completely seperate installs no sharing, storage drive seperate and accessed by both

---

