---
title: "Merge 2 partitions into 1"
date: 2012-06-26
forum: General Help
---

### Post by pabloikba on 2012-06-26
Ubuntu 12.04 installed on 282gb partition of 500gb drive. The other partition is Ext4 but has nothing on it. I would like to combine both into 1 partition without losing the Ubuntu 12.04 installation and associated files.

Can anyone please help?

Thanks,

Paul

---

### Post by oldfred on 2012-06-26
Are they next to each other? You have to delete empty partition and then expand Ubuntu partition. If not next to each other it gets more complicated.

In all cases have good backups as any partition operations have risks, especially if a power failure or other interruption in the middle and then system is corrupted. Do not run on battery power only as partition moves can take very long times depending on size and amount of data to move. 

Post screenshot from gparted. Use paperclip icon in edit bar above message to attach screenshot to message.

Another alternative is to use space as data or move /home into the new partition. I normally suggest smaller / (root) partitions of 25GB and large /home or /data partition(s). Smaller / is slightly more efficient as all system files are near each other on drive.

Any partition changes have to be from unmounted partitions, so you have to use liveCD to make changes. You can use gparted from working install to look at partitions or change partitions on another drive or unmounted partitions.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by pabloikba on 2012-06-26
Thanks for your reply. 

Screenshot is attached.

Note: Original Ubuntu 10.l0 occupies /sda

Paul

---

### Post by oldfred on 2012-06-26
I would consider making it /home or just a data partition and  store data. 

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you want one large / (root) partition then you have to delete sda1 (is the 3GB used just the reserved space or do you have some data in it?). 
Then you have to move extended partition left and then move sdc5 left which will take a long time as it has lots of data.
 Then you can expand sdc5 right into the unallocated space.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

---

### Post by pabloikba on 2012-06-26
Thank you.

Pablo

---

### Post by ajgreeny on 2012-06-26
I'm confused as you say the original ubuntu is on sda and you have showed us the partitions on sdc.  Is 10.10 on sda no longer needed or will you keep it and dual boot the two, and where is the OS of 12.04?

Your screenshot does not tally with what you have said in your first post, so it would be good to know more about your system.

---

### Post by pabloikba on 2012-06-26
The 10.10 is on sda.....
I installed 12.04 on sdc because I want to be able to move data over once I get it running right.

Pablo

---

### Post by ajgreeny on 2012-06-26
> **pabloikba said:**
> The 10.10 is on sda.....
I installed 12.04 on sdc because I want to be able to move data over once I get it running right.

Pablo
OK, Thanks.

You say the other partition, sdc5 is ext4 but has nothing on it, but in  gparted it shows as having 193GB of data on it, hence my confusion.  I  should hate you to loose 193GB of files that are important to you.

It may be worth getting **boot-info-script** from my signature and  following the instructions to run it etc etc.  It may help with more  detail of what is really going on here, not just for grub, but for all  system info that may help us.

---

### Post by pabloikba on 2012-06-27
ajgreeny - I just did as you suggested and these are the results....what do you suggest?

Thanks

                  ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdh.
 => No boot loader is installed in the MBR of /dev/sdi.
 => No boot loader is installed in the MBR of /dev/sdj.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/mapper/pdc_cbgccdaadg 
    and looks at sector 1 of the same hard drive for core.img. core.img is at 
    this location and looks in partition 1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdh1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdh1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdh1 starts at sector 32.
    Operating System:  
    Boot files:        

sdi1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdi2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdj1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdj2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

pdc_cbgccdaadg1: _______________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

pdc_cbgccdaadg2: _______________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

pdc_cbgccdaadg5: _______________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,881,188,351 1,881,186,304  83 Linux
/dev/sda2       1,881,190,398 1,953,392,639    72,202,242   5 Extended
/dev/sda5       1,881,190,400 1,953,392,639    72,202,240  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   400,500,449   400,500,387  83 Linux
/dev/sdc4         400,500,734   976,771,071   576,270,338   5 Extended
/dev/sdc5         400,500,736   951,623,679   551,122,944  83 Linux
/dev/sdc6         951,625,728   976,771,071    25,145,344  82 Linux swap / Solaris


Drive: sdh _____________________________________________________________________

Disk /dev/sdh: 16.0 GB, 16001269760 bytes
64 heads, 32 sectors/track, 15260 cylinders, total 31252480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdh1                  32    31,252,479    31,252,448   c W95 FAT32 (LBA)


Drive: sdi _____________________________________________________________________

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdi1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdi1              34   976,762,583   976,762,550 Data partition (Windows/Linux)
/dev/sdi2     976,762,584 1,953,525,134   976,762,551 Data partition (Windows/Linux)

Drive: sdj _____________________________________________________________________

Disk /dev/sdj: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdj1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdj1              34   976,762,583   976,762,550 Data partition (Windows/Linux)
/dev/sdj2     976,762,584 1,953,525,134   976,762,551 Data partition (Windows/Linux)

Drive: pdc_cbgccdaadg _____________________________________________________________________

Disk /dev/mapper/pdc_cbgccdaadg: 1000.1 GB, 1000137752576 bytes
255 heads, 63 sectors/track, 121593 cylinders, total 1953394048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/pdc_cbgccdaadg1   *          2,048 1,881,188,351 1,881,186,304  83 Linux
/dev/mapper/pdc_cbgccdaadg2      1,881,190,398 1,953,392,639    72,202,242   5 Extended
/dev/mapper/pdc_cbgccdaadg5      1,881,190,400 1,953,392,639    72,202,240  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/pdc_cbgccdaadg1 e911687d-2267-440c-acf8-3fb988291496   ext4       Ubuntu1010
/dev/mapper/pdc_cbgccdaadg5 3abd980c-4fd0-4812-bcb0-8d24a833ea14   swap       
/dev/sda                                                promise_fasttrack_raid_member 
/dev/sdb                                                promise_fasttrack_raid_member 
/dev/sdc1        78c926c7-d727-48de-a9b7-a7ba8f7f49ca   ext4       Extra
/dev/sdc5        d8b17d7e-b52f-4e26-b3e2-f3f39c340acb   ext4       
/dev/sdc6        9b5d706a-e0fb-405b-863c-e86529a81f23   swap       
/dev/sdh1        85E0-DC76                              vfat       MemStickB
/dev/sdi1        d13f6c20-5411-4d0c-8b7a-d00434d1798e   ext4       Videos_1
/dev/sdi2        c6a2bf16-e918-427a-b597-41b1e6dbe9ca   ext4       Videos_2
/dev/sdj1        f8769d04-6933-4ae5-bfb8-b43a1cd2171e   ext4       TV_Current
/dev/sdj2        41dfa0dd-c27f-4f77-ba82-9a3be638ce81   ext4       Movies_Current

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
pdc_cbgccdaadg
pdc_cbgccdaadg1
pdc_cbgccdaadg2
pdc_cbgccdaadg5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdc1        /media/Extra             ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc5        /                        ext4       (rw,errors=remount-ro)
/dev/sdh1        /media/MemStickB         vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdi1        /media/Videos_1          ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdi2        /media/Videos_2          ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdj1        /media/TV_Current        ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdj2        /media/Movies_Current    ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root d8b17d7e-b52f-4e26-b3e2-f3f39c340acb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos5)'
  search --no-floppy --fs-uuid --set=root d8b17d7e-b52f-4e26-b3e2-f3f39c340acb
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set=root d8b17d7e-b52f-4e26-b3e2-f3f39c340acb
    linux    /boot/vmlinuz-3.2.0-25-generic root=UUID=d8b17d7e-b52f-4e26-b3e2-f3f39c340acb ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set=root d8b17d7e-b52f-4e26-b3e2-f3f39c340acb
    echo    'Loading Linux 3.2.0-25-generic ...'
    linux    /boot/vmlinuz-3.2.0-25-generic root=UUID=d8b17d7e-b52f-4e26-b3e2-f3f39c340acb ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-25-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set=root d8b17d7e-b52f-4e26-b3e2-f3f39c340acb
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=d8b17d7e-b52f-4e26-b3e2-f3f39c340acb ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set=root d8b17d7e-b52f-4e26-b3e2-f3f39c340acb
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=d8b17d7e-b52f-4e26-b3e2-f3f39c340acb ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set=root d8b17d7e-b52f-4e26-b3e2-f3f39c340acb
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=d8b17d7e-b52f-4e26-b3e2-f3f39c340acb ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set=root d8b17d7e-b52f-4e26-b3e2-f3f39c340acb
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=d8b17d7e-b52f-4e26-b3e2-f3f39c340acb ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set=root d8b17d7e-b52f-4e26-b3e2-f3f39c340acb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set=root d8b17d7e-b52f-4e26-b3e2-f3f39c340acb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu, with Linux 2.6.35-32-generic (on /dev/mapper/pdc_cbgccdaadg1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd5,msdos1)'
    search --no-floppy --fs-uuid --set=root e911687d-2267-440c-acf8-3fb988291496
    linux /boot/vmlinuz-2.6.35-32-generic root=UUID=e911687d-2267-440c-acf8-3fb988291496 ro quiet splash
    initrd /boot/initrd.img-2.6.35-32-generic
}
menuentry "Ubuntu, with Linux 2.6.35-32-generic (recovery mode) (on /dev/mapper/pdc_cbgccdaadg1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd5,msdos1)'
    search --no-floppy --fs-uuid --set=root e911687d-2267-440c-acf8-3fb988291496
    linux /boot/vmlinuz-2.6.35-32-generic root=UUID=e911687d-2267-440c-acf8-3fb988291496 ro single
    initrd /boot/initrd.img-2.6.35-32-generic
}
### END /etc/grub.d/30_os-prober_proxy ###

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

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=d8b17d7e-b52f-4e26-b3e2-f3f39c340acb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=9b5d706a-e0fb-405b-863c-e86529a81f23 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 413.687164307 = 444.193210368  boot/grub/core.img                             1
 413.255123138 = 443.729309696  boot/grub/grub.cfg                             1
 206.904933929 = 222.162481152  boot/initrd.img-3.2.0-23-generic               2
 206.799503326 = 222.049275904  boot/initrd.img-3.2.0-24-generic               1
 209.017082214 = 224.430383104  boot/initrd.img-3.2.0-25-generic               2
 299.107162476 = 321.163870208  boot/vmlinuz-3.2.0-23-generic                  1
 200.208728790 = 214.972485632  boot/vmlinuz-3.2.0-24-generic                  2
 195.122795105 = 209.511505920  boot/vmlinuz-3.2.0-25-generic                  2
 209.017082214 = 224.430383104  initrd.img                                     2
 206.799503326 = 222.049275904  initrd.img.old                                 1
 195.122795105 = 209.511505920  vmlinuz                                        2
 200.208728790 = 214.972485632  vmlinuz.old                                    2

===================== pdc_cbgccdaadg1/boot/grub/grub.cfg: ======================

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
set default="Ubuntu, with Linux 2.6.35-32-generic"
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
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(/dev/mapper/pdc_cbgccdaadg,msdos1)'
search --no-floppy --fs-uuid --set e911687d-2267-440c-acf8-3fb988291496
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/mapper/pdc_cbgccdaadg,msdos1)'
search --no-floppy --fs-uuid --set e911687d-2267-440c-acf8-3fb988291496
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry 'Ubuntu, with Linux 2.6.35-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/pdc_cbgccdaadg,msdos1)'
    search --no-floppy --fs-uuid --set e911687d-2267-440c-acf8-3fb988291496
    linux    /boot/vmlinuz-2.6.35-32-generic root=UUID=e911687d-2267-440c-acf8-3fb988291496 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/pdc_cbgccdaadg,msdos1)'
    search --no-floppy --fs-uuid --set e911687d-2267-440c-acf8-3fb988291496
    echo    'Loading Linux 2.6.35-32-generic ...'
    linux    /boot/vmlinuz-2.6.35-32-generic root=UUID=e911687d-2267-440c-acf8-3fb988291496 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-32-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/pdc_cbgccdaadg,msdos1)'
    search --no-floppy --fs-uuid --set e911687d-2267-440c-acf8-3fb988291496
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/pdc_cbgccdaadg,msdos1)'
    search --no-floppy --fs-uuid --set e911687d-2267-440c-acf8-3fb988291496
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu, with Linux 3.2.0-24-generic (on /dev/sdc5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set d8b17d7e-b52f-4e26-b3e2-f3f39c340acb
    linux /boot/vmlinuz-3.2.0-24-generic root=UUID=d8b17d7e-b52f-4e26-b3e2-f3f39c340acb ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-24-generic
}
menuentry "Ubuntu, with Linux 3.2.0-24-generic (recovery mode) (on /dev/sdc5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set d8b17d7e-b52f-4e26-b3e2-f3f39c340acb
    linux /boot/vmlinuz-3.2.0-24-generic root=UUID=d8b17d7e-b52f-4e26-b3e2-f3f39c340acb ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-24-generic
}
### END /etc/grub.d/30_os-prober_proxy ###

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

========================== pdc_cbgccdaadg1/etc/fstab: ==========================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/pdc_cbgccdaadg1 /               ext4    errors=remount-ro 0       1
/dev/mapper/pdc_cbgccdaadg5 none            swap    sw              0       






--------------------------------------------------------------------------------

============== pdc_cbgccdaadg1: Location of files loaded by Grub: ==============

           GiB - GB             File                                 Fragment(s)

 310.132297516 = 333.002018816  boot/grub/core.img                             1
 730.146144867 = 783.988453376  boot/grub/grub.cfg                             2
   1.140487671 = 1.224589312    boot/initrd.img-2.6.35-22-generic              2
   1.277088165 = 1.371262976    boot/initrd.img-2.6.35-27-generic              1
   0.904178619 = 0.970854400    boot/initrd.img-2.6.35-28-generic              2
  45.756896973 = 49.131094016   boot/initrd.img-2.6.35-30-generic              2
 845.540039062 = 907.891703808  boot/initrd.img-2.6.35-31-generic              2
 865.461914062 = 929.282654208  boot/initrd.img-2.6.35-32-generic              2
 310.138854980 = 333.009059840  boot/vmlinuz-2.6.35-22-generic                 1
 310.145854950 = 333.016576000  boot/vmlinuz-2.6.35-27-generic                 1
   0.547851562 = 0.588251136    boot/vmlinuz-2.6.35-28-generic                 2
 310.505615234 = 333.402865664  boot/vmlinuz-2.6.35-30-generic                 1
 310.382213593 = 333.270364160  boot/vmlinuz-2.6.35-31-generic                 1
 310.388454437 = 333.277065216  boot/vmlinuz-2.6.35-32-generic                 1
 865.461914062 = 929.282654208  initrd.img                                     2
 845.540039062 = 907.891703808  initrd.img.old                                 2
 310.388454437 = 333.277065216  vmlinuz                                        1
 310.382213593 = 333.270364160  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda5


Unknown BootLoader on sdc4

00000000  74 6d 31 7a 2b 74 4e 6b  2b 37 51 53 2f 77 2f 4a  |tm1z+tNk+7QS/w/J|
00000010  6f 4b 30 58 50 55 36 33  75 51 42 77 34 47 76 63  |oK0XPU63uQBw4Gvc|
00000020  46 70 78 46 68 51 56 62  46 37 45 52 6e 6b 6a 6f  |FpxFhQVbF7ERnkjo|
00000030  50 41 4f 62 4d 6f 53 73  4c 33 0a 66 4e 78 37 38  |PAObMoSsL3.fNx78|
00000040  4a 54 54 33 75 44 79 72  48 46 32 69 6f 33 31 2b  |JTT3uDyrHF2io31+|
00000050  38 34 34 31 51 53 62 65  6e 62 51 30 31 55 50 63  |8441QSbenbQ01UPc|
00000060  6e 39 64 5a 6a 68 64 35  72 4b 43 78 47 71 43 74  |n9dZjhd5rKCxGqCt|
00000070  6b 65 76 72 76 5a 64 6c  2f 36 46 57 6d 6d 43 59  |kevrvZdl/6FWmmCY|
00000080  42 67 61 35 46 7a 47 0a  57 2f 66 4b 76 62 6d 36  |Bga5FzG.W/fKvbm6|
00000090  6d 74 7a 72 49 31 33 37  74 6b 76 48 41 30 4f 78  |mtzrI137tkvHA0Ox|
000000a0  6d 32 6a 4b 54 6a 32 39  35 71 4e 63 4c 69 37 6c  |m2jKTj295qNcLi7l|
000000b0  49 30 6b 76 4f 31 4a 71  49 51 6c 30 54 42 63 46  |I0kvO1JqIQl0TBcF|
000000c0  30 64 78 39 69 32 71 38  64 31 4e 59 6b 48 4c 54  |0dx9i2q8d1NYkHLT|
000000d0  4d 51 58 38 0a 79 50 4f  65 6d 73 7a 6f 31 43 4a  |MQX8.yPOemszo1CJ|
000000e0  5a 49 78 7a 55 52 4d 38  32 44 49 4e 59 6c 73 4b  |ZIxzURM82DINYlsK|
000000f0  62 7a 64 30 37 76 64 77  2b 42 48 76 67 59 61 30  |bzd07vdw+BHvgYa0|
00000100  33 33 7a 2f 5a 73 49 6c  70 47 64 50 42 42 2f 64  |33z/ZsIlpGdPBB/d|
00000110  6d 45 75 6e 78 54 69 46  59 59 4f 4d 47 4b 79 36  |mEunxTiFYYOMGKy6|
00000120  51 0a 72 30 71 69 77 6d  73 2b 37 51 32 48 48 70  |Q.r0qiwms+7Q2HHp|
00000130  79 73 4d 5a 61 77 30 45  71 38 30 61 67 61 77 58  |ysMZaw0Eq80agawX|
00000140  44 73 57 62 4d 79 7a 61  66 62 36 37 47 78 53 36  |DsWbMyzafb67GxS6|
00000150  38 47 4b 4d 6f 55 42 46  33 48 65 6c 50 45 64 53  |8GKMoUBF3HelPEdS|
00000160  35 49 43 47 74 71 33 71  47 2b 61 75 69 61 0a 68  |5ICGtq3qG+auia.h|
00000170  54 32 51 36 36 46 4a 55  47 63 72 30 50 56 49 6d  |T2Q66FJUGcr0PVIm|
00000180  47 75 73 46 31 55 31 6a  30 4d 7a 61 49 4d 34 32  |GusF1U1j0MzaIM42|
00000190  79 67 5a 45 78 61 6f 75  43 43 48 67 63 6c 75 36  |ygZExaouCCHgclu6|
000001a0  5a 4a 73 53 2f 72 32 44  70 31 4b 6b 6e 74 46 33  |ZJsS/r2Dp1KkntF3|
000001b0  63 6b 6e 46 33 4a 55 6f  50 5a 35 0a 53 4e 00 fe  |cknF3JUoPZ5.SN..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 78 d9 20 00 fe  |...........x. ..|
000001d0  ff ff 05 fe ff ff 02 78  d9 20 00 b8 7f 01 00 00  |.......x. ......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
```

---

### Post by oldfred on 2012-06-27
Added code tags. Please use code tags for any long data post to make it easier to review. You can just highlight data and click on # in the edit panel above your message.

It looks like you have promise RAID, but sdc is just a separate hard drive. As such I still prefer smaller / (root) partitions somewhat for minor efficiency as all system files are near each other on drive, and separate /home or other data partitions.

---

### Post by pabloikba on 2012-06-28
Thanks for all the help. It is appreciated.

Pablo

---

