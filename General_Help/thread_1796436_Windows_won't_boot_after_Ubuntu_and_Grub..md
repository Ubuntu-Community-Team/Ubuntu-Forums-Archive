---
title: "Windows won't boot after Ubuntu and Grub."
date: 2011-07-03
forum: General Help
---

### Post by micael3000 on 2011-07-03
Hello,

I have formatted my computer today on the following steps:
(I was an Ubuntu user before, and now I need to install windows too, that is why the formatting)


1) Backup;
2) Installed windows seven professional (and partitioned the disk in 3 + the system tables that windows reserves, installing on the first partition);
3) Installed backtrack (that is also Ubuntu) by partitioning more the hard disk (leaving the first partition intact but creating logical partitions);
4) Installed ubuntu;
5) Restored the backup;


After that I was thinking that everything was OK, until I try booting on windows seven... It stops booting when 'mounting the windows logo' and shows a veeery quick blue screen of death before restarting... I cannot repair using windows dvd because it doesn't recognize my hard disk anymore and when booting on windows (before the loading i have a black screen asking for repair or normal boot) the repair does nothing... It says that wasn't possible to find out what was wrong.

I don't know what to do, I am not very comfortable with the idea of redoing the whole work of backup and formatting (losing the next weekend)... Have anyone experienced this issue and successfully fixed it?

Thanks!!

Attachments:

Disk Utility printscreen:
[http://i56.tinypic.com/2zfs7t3.png](http://i56.tinypic.com/2zfs7t3.png)

Grub / Burg Windows configuration:
```
menuentry "Windows 7 1" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root AEC9002FC8FFF405
    chainloader +1
}
```

Image of the screen that freezes:
[http://marlonpalmas.files.wordpress.com/2008/12/windows-7-boot-for-xp.png](http://marlonpalmas.files.wordpress.com/2008/12/windows-7-boot-for-xp.png)
Note: The windows logo never complete loading, it stops when there are only 3 little dots on screen.

---

### Post by Keypel on 2011-07-03
What program did you use to 'backup'?

---

### Post by oldfred on 2011-07-03
Windows 7 can be installed two ways. The normal install is a 100MB boot/recovery partition and the main install. The other way is to preformat a NTFS partition with the boot flag, then it will install to one partition like Vista did.

If you boot files are in sda1 - a 100MB boot partition, you need to have the boot flag (active partition) on sda1.

If you want to see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Lots of info on how windows works. Review pictures if you just want an overview:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by micael3000 on 2011-07-03
Hello!

Thanks for the answers :)

@Keypel

Manual backup (copying files)

@oldfred

RESULTS.txt:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for /boot/burg.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

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

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 5 - Code Name 
                       Revolution 32 bit
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/grub/core.img /boot/burg/core.img

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       206,847       204,800  42 SFS
/dev/sda3             206,848   105,064,447   104,857,600  42 SFS
/dev/sda4         105,066,494   976,771,071   871,704,578   5 Extended
/dev/sda5         105,066,496   205,064,191    99,997,696  83 Linux
/dev/sda6         205,066,240   405,063,679   199,997,440  83 Linux
/dev/sda7         405,065,728   805,064,703   399,998,976  83 Linux
/dev/sda8         805,066,752   809,064,447     3,997,696  82 Linux swap / Solaris
/dev/sda9         809,066,496   976,771,071   167,704,576  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        AEC9002FC8FFF405                       ntfs       System Reserved
/dev/sda3        42FC9ECBFC9EB91D                       ntfs       Windows7
/dev/sda5        21be3351-a294-4734-98cc-7cc38015c101   ext4       BackTrack5
/dev/sda6        33184d77-97c5-44e6-aa12-99c5cbf5726f   ext4       Ubuntu11.04
/dev/sda7        1B7A135B1F038500                       ntfs       InterSO
/dev/sda8        1b40d842-3218-4c41-9a3f-27ab8b0dc50e   swap       
/dev/sda9        4180C80E4C2F80CA                       ntfs       Nada

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /mnt/Desktop             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /media/UDF Volume        udf        (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set 21be3351-a294-4734-98cc-7cc38015c101
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  set gfxpayload=keep
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
search --no-floppy --fs-uuid --set 21be3351-a294-4734-98cc-7cc38015c101
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
insmod play
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.38' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 21be3351-a294-4734-98cc-7cc38015c101
    linux    /boot/vmlinuz-2.6.38 root=UUID=21be3351-a294-4734-98cc-7cc38015c101 ro  vga=792 splash  text splash nomodeset vga=791
    initrd    /boot/initrd.img-2.6.38
}
menuentry 'Ubuntu, with Linux 2.6.38 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 21be3351-a294-4734-98cc-7cc38015c101
    echo    'Loading Linux 2.6.38 ...'
    linux    /boot/vmlinuz-2.6.38 root=UUID=21be3351-a294-4734-98cc-7cc38015c101 ro single  vga=792 splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 21be3351-a294-4734-98cc-7cc38015c101
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 21be3351-a294-4734-98cc-7cc38015c101
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set AEC9002FC8FFF405
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=21be3351-a294-4734-98cc-7cc38015c101 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=1b40d842-3218-4c41-9a3f-27ab8b0dc50e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  68.267917633 = 73.302118400   boot/grub/core.img                             1
  70.414131165 = 75.606597632   boot/grub/grub.cfg                             1
  50.261970520 = 53.968379904   boot/initrdf.img-2.6.38                        1
  51.498046875 = 55.295606784   boot/initrd.img-2.6.38                         2
  50.291496277 = 54.000082944   boot/initrds.img-2.6.38                        1
  68.230449677 = 73.261887488   boot/vmlinuz-2.6.38                            1
  51.498046875 = 55.295606784   initrd.img                                     2
  68.230449677 = 73.261887488   vmlinuz                                        1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 33184d77-97c5-44e6-aa12-99c5cbf5726f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 33184d77-97c5-44e6-aa12-99c5cbf5726f
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 33184d77-97c5-44e6-aa12-99c5cbf5726f
insmod png
if background_image /boot/grub/science.png; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu 11.04" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 33184d77-97c5-44e6-aa12-99c5cbf5726f
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=33184d77-97c5-44e6-aa12-99c5cbf5726f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_os-prober_proxy ###
menuentry "BackTrack 5" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 21be3351-a294-4734-98cc-7cc38015c101
    linux /boot/vmlinuz-2.6.38 root=UUID=21be3351-a294-4734-98cc-7cc38015c101 ro vga=792 splash text splash nomodeset vga=791
    initrd /boot/initrd.img-2.6.38
}
menuentry "Windows 7" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root AEC9002FC8FFF405
    chainloader +1
}
### END /etc/grub.d/20_os-prober_proxy ###

### BEGIN /etc/grub.d/30_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 33184d77-97c5-44e6-aa12-99c5cbf5726f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 33184d77-97c5-44e6-aa12-99c5cbf5726f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/30_memtest86+ ###

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

=========================== sda6/boot/burg/burg.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=ubuntu
set gfxmode=640x480
if [ -s $prefix/burgenv ]; then
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
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
    save_env gfxmode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'
  load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'
  load_string '+theme_menu { -burg { command="set theme_name=burg" }}'
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 33184d77-97c5-44e6-aa12-99c5cbf5726f
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry 'Ubuntu 11.04' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 33184d77-97c5-44e6-aa12-99c5cbf5726f
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=33184d77-97c5-44e6-aa12-99c5cbf5726f ro  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/30_os-prober ###
menuentry "Windows 7 1" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root AEC9002FC8FFF405
    chainloader +1
}
menuentry "Windows 7 2" --class windows --class os {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aec9002fc8fff405
    chainloader +1
}
menuentry "BackTrack 5" --class debian --class os --group group_/dev/sda5 {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 21be3351-a294-4734-98cc-7cc38015c101
    linux /boot/vmlinuz-2.6.38 root=UUID=21be3351-a294-4734-98cc-7cc38015c101 ro vga=792 splash text splash nomodeset vga=791
    initrd /boot/initrd.img-2.6.38
}
menuentry 'Ubuntu 11.04 (recovery)' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 33184d77-97c5-44e6-aa12-99c5cbf5726f
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=33184d77-97c5-44e6-aa12-99c5cbf5726f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
#menuentry "BackTrack 5 (recovery mode)" --class debian --class os --group group_/dev/sda5 {
#    insmod ext2
#    set root='(hd0,5)'
#    search --no-floppy --fs-uuid --set 21be3351-a294-4734-98cc-7cc38015c101
#    linux /boot/vmlinuz-2.6.38 root=UUID=21be3351-a294-4734-98cc-7cc38015c101 ro single vga=792 splash
#    initrd /boot/initrd.img-2.6.38
#}
### END /etc/burg.d/30_os-prober ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=33184d77-97c5-44e6-aa12-99c5cbf5726f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=1b40d842-3218-4c41-9a3f-27ab8b0dc50e none            swap    sw              0       0
# custom
/dev/sda7    /mnt/Desktop    ntfs    defaults    0    0--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 174.153228760 = 186.995605504  boot/burg/burg.cfg                             1
 121.963256836 = 130.957049856  boot/burg/core.img                             1
 121.917739868 = 130.908176384  boot/grub/core.img                             1
 144.112506866 = 154.739625984  boot/grub/grub.cfg                             1
 100.162624359 = 107.548798976  boot/initrd.img-2.6.38-8-generic               2
 121.916019440 = 130.906329088  boot/vmlinuz-2.6.38-8-generic                  1
 100.162624359 = 107.548798976  initrd.img                                     2
 121.916019440 = 130.906329088  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  6c a2 f9 0e 65 0a bc 67  1c bf 50 82 e2 78 cf fd  |l...e..g..P..x..|
00000010  b9 c0 18 89 25 ed 6a 87  22 7c 29 2b 6b cc 9c f2  |....%.j."|)+k...|
00000020  f4 94 07 e6 0f 70 f9 74  f5 47 09 c3 8b 74 ce a8  |.....p.t.G...t..|
00000030  1b c1 aa 69 77 5d 16 0c  f2 fc ef b1 40 e2 9e 45  |...iw]......@..E|
00000040  50 68 57 71 8f e6 16 42  ea df 60 04 f6 b4 b1 d9  |PhWq...B..`.....|
00000050  27 fa 29 b6 41 7e 24 c3  97 39 57 ff 15 2f c0 ba  |'.).A~$..9W../..|
00000060  3e 49 2e 34 53 74 1a af  58 4b c6 da 12 29 ca 54  |>I.4St..XK...).T|
00000070  3c ba a3 1f 3f 0f 0f 87  3d 31 90 61 c5 0a b8 f3  |<...?...=1.a....|
00000080  e2 bf 35 67 13 b8 ea 09  47 b4 72 74 df be 8a c1  |..5g....G.rt....|
00000090  24 8e 33 d6 b5 a3 31 ed  65 74 fe 11 b7 b1 a5 ea  |$.3...1.et......|
000000a0  a6 bd cd 45 a8 d1 dc 5f  57 33 38 9d ea b0 a6 30  |...E..._W38....0|
000000b0  0d f6 40 59 11 4c 24 13  b7 e6 bc 71 c2 6e 2e d8  |..@Y.L$....q.n..|
000000c0  e0 b6 5f aa 71 c2 89 33  e1 1f 2e 25 8e 3f c3 b3  |.._.q..3...%.?..|
000000d0  b3 74 e3 a7 fa 2e 8e 59  ec 67 bc e7 ee cf 8e 3c  |.t.....Y.g.....<|
000000e0  88 9c 64 2b ec 71 b7 91  de 3e f0 eb df 18 26 2a  |..d+.q...>....&*|
000000f0  16 fa e8 01 5f 70 83 f5  59 aa 17 d7 02 37 ae a8  |...._p..Y....7..|
00000100  c4 bd 31 0e 7a cb e5 dc  da 7c d1 e3 78 a4 cf 22  |..1.z....|..x.."|
00000110  5f 32 49 c7 fa 00 bd 04  73 61 aa 9b e1 25 7c ea  |_2I.....sa...%|.|
00000120  48 b1 8d 8a 73 d9 62 b9  bf ec aa 50 0c 18 91 ab  |H...s.b....P....|
00000130  bc c5 63 55 01 2f a6 48  b8 bb 26 7d 87 46 cf 3b  |..cU./.H..&}.F.;|
00000140  ee f8 89 84 df 2e 41 b1  d8 f0 9d bd 92 5d 23 f9  |......A......]#.|
00000150  85 7c af 81 bd 7e 34 b9  d5 e9 0c 18 6b 68 4a f9  |.|...~4.....khJ.|
00000160  09 1f d1 56 32 47 ee 10  26 a9 a6 53 b8 80 45 b2  |...V2G..&..S..E.|
00000170  39 bf 85 a3 da 6b 59 59  6b f8 3c a0 91 52 12 ef  |9....kYYk.<..R..|
00000180  c4 c5 e0 ea d0 44 6d b9  31 64 c5 7b 54 ae ec 2d  |.....Dm.1d.{T..-|
00000190  b0 aa ea 76 00 a4 a1 50  25 fb 92 e7 e3 e4 a3 e6  |...v...P%.......|
000001a0  81 d2 73 de 49 36 87 88  50 c6 b8 3d 9b 27 d9 01  |..s.I6..P..=.'..|
000001b0  5a cb c1 b6 1b 2b 5e a4  b1 fd bd 96 f8 50 6a 06  |Z....+^......Pj.|
000001c0  51 5c 4a 09 26 36 c8 db  50 ac ab 25 ab 4f 40 ef  |Q\J.&6..P..%.O@.|
000001d0  61 77 eb 96 56 da 80 4e  cb 2e fd 59 ff e2 a8 a0  |aw..V..N...Y....|
000001e0  2c 62 7d a0 74 9e 28 01  56 60 84 99 75 8d fa 53  |,b}.t.(.V`..u..S|
000001f0  8a 67 00 d1 34 f0 39 38  b6 34 11 88 a6 b9 bc 5d  |.g..4.98.4.....]|
00000200

Unknown BootLoader on sda4

00000000  f8 2c 76 1f 24 60 3e f1  1e 45 b5 33 31 cd 02 27  |.,v.$`>..E.31..'|
00000010  a6 55 38 db 1b 90 08 5f  41 5f a6 41 26 eb 0b 63  |.U8...._A_.A&..c|
00000020  d8 68 38 81 4d 85 52 db  30 38 19 aa 61 0e d4 b0  |.h8.M.R.08..a...|
00000030  3a 84 34 4c ac 58 3d 6b  20 82 23 c6 7e 0b e3 1d  |:.4L.X=k .#.~...|
00000040  38 06 c7 ef c2 ff 3e c6  d9 f7 41 52 7b b4 87 83  |8.....>...AR{...|
00000050  0b d3 33 8f 80 76 3d 54  80 1f 16 40 a3 42 bd 87  |..3..v=T...@.B..|
00000060  89 9e 85 3a e5 88 cd 19  a2 df 18 5e c4 44 84 21  |...:.......^.D.!|
00000070  28 9b 9a 33 32 9f 53 d5  2e 07 0d 56 44 8d 65 0b  |(..32.S....VD.e.|
00000080  8f 65 b3 c6 e2 f4 d8 cb  1a 6b 21 8d 8d 5f 77 56  |.e.......k!.._wV|
00000090  1b 24 e3 5f 0a fe a5 e2  5f 1a fe f5 c0 bf 9e 91  |.$._...._.......|
000000a0  e1 fb 83 8e e9 6a 5c ce  1a b0 c3 79 48 e5 b5 b8  |.....j\....yH...|
000000b0  ac 75 90 0a e7 43 2f b8  20 8a f2 6e 6b 4a 49 6f  |.u...C/. ..nkJIo|
000000c0  c9 ac 89 b2 69 27 e8 2f  32 a0 4d 55 5c 15 d5 91  |....i'./2.MU\...|
000000d0  85 3b 06 8e dc 71 7d cc  8e c1 23 77 dc 14 b3 63  |.;...q}...#w...c|
000000e0  f3 91 3b de 1a b3 e3 d2  23 77 bc 23 66 c7 65 e1  |..;.....#w.#f.e.|
000000f0  8e df 59 82 b4 2b 6b 1b  f4 da 07 09 c9 ee 9d d0  |..Y..+k.........|
00000100  7b fe 76 e8 d5 0a 36 ac  d9 06 7d a8 b2 af 59 d9  |{.v...6...}...Y.|
00000110  47 55 f6 69 83 7e 5d 41  f7 a7 ca 01 66 65 7f 55  |GU.i.~]A....fe.U|
00000120  d9 ff 30 d0 e9 54 39 d0  ac 4c 57 95 e9 87 81 1e  |..0..T9..LW.....|
00000130  44 95 83 cd ca 41 aa 72  10 42 47 16 dc 03 d9 0f  |D....A.r.BG.....|
00000140  60 3b 32 ff bd 70 0a b4  c1 9f 60 27 fe b7 3b 8a  |`;2..p....`'..;.|
00000150  00 bb c2 72 b9 9c ad b0  08 b0 09 59 55 e0 d7 93  |...r.......YU...|
00000160  95 73 1f 64 64 e5 b4 c1  31 59 39 3b 60 08 e5 86  |.s.dd...1Y9;`...|
00000170  52 92 99 75 2f 24 b5 c1  b0 16 14 cf 36 c8 6a 05  |R..u/$......6.j.|
00000180  3b d5 66 53 92 43 49 6e  47 b1 fb 3b e2 f1 24 8a  |;.fS.CInG..;..$.|
00000190  c4 53 90 00 4f 23 8f 3e  03 6e 78 0e 06 c3 f3 a8  |.S..O#.>.nx.....|
000001a0  4d 5e 84 3c 78 05 c6 c0  ab 70 1c bc a6 30 4b 37  |M^.<x....p...0K7|
000001b0  67 0f 8b 8a 87 ad 64 67  2b 6c 3d ca be 70 00 fe  |g.....dg+l=..p..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d8 f5 05 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 d8  f5 05 00 c0 eb 0b 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by micael3000 on 2011-07-03
For the records, I found on this log the grub configuration for windows and used it... Still getting BSOD at the loading part.

---

### Post by oldfred on 2011-07-03
The SFS is dynamic partitions in windows. You tried to create more than 4 partitions and windows automatically converts to a logical volume  manager. Windows is supposed to work with SFS.

Some have said the LVM or RAID drivers may let your read SFS.
sudo apt-get install lvm2
sudo apt-get install mdadm

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

One user used these two:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

---

### Post by micael3000 on 2011-07-10
Hello, thanks for the answer.

That is not my problem... Ubuntu and BackTrack works fine! The windows is the one that doesn't boot... These guides you posted are for fixing inside windows to be able to install ubuntu - which is not my case.

I have created the logical volumes from Ubuntu, Windows gave me no option to do that. :(

Help?

---

### Post by oldfred on 2011-07-10
SFS is windows only. It only is recently that some tools even show them.

Grub only chainloads to windows. That is what the windows boot loader does from the MBR. The MBR windows bootloader looks for the active partition (boot flag) and jumps to that partition to continue to boot. Grub just jumps to the windows boot partition in the same way. So if windows does not work, windows repairs are required.

---

### Post by micael3000 on 2011-07-10
It is weird, because Windows was working just fine before I install ubuntu... That is why I am here (otherwise I would go to microsoft's support).

This is the blue screen that shows up: [http://lh3.ggpht.com/_XsZ00KcDpnU/S_tvjtB5FGI/AAAAAAAAAPg/T4p87rB-j-s/image_thumb%5B6%5D.png](http://lh3.ggpht.com/_XsZ00KcDpnU/S_tvjtB5FGI/AAAAAAAAAPg/T4p87rB-j-s/image_thumb%5B6%5D.png) but it is showing just up to "newly installed".

---

### Post by micael3000 on 2011-07-19
Hi, I have - again - reinstalled all of the OS (aka format the computer) and now its working just fine with grub.

Thank you all.

---

