---
title: "HELP!!! I can't boot into windows and ubuntu"
date: 2011-06-05
forum: General Help
---

### Post by link15 on 2011-06-05
so I installed ubuntu 11.04 wubi on windows xp recently, and everything was working great until I tried to install burg with [http://www.omgubuntu.co.uk/2011/05/super-boot-manager-eases-burg-grub-plymouth-tweaking-pains/]("http://www.omgubuntu.co.uk/2011/05/super-boot-manager-eases-burg-grub-plymouth-tweaking-pains/") super boot manager and it gave me two places to install to, /dev/sda and something else (sorry I can't remember), so I installed it on both of them, one of them succeeded and the other didn't so I restarted to see if it worked and it told me this : Grub Loading. error: no such device: 186d9774-2f9b-411b-b6b8. entering rescue mode... and then it gives me a grub rescue prompt I've tried the xp recovery console but it asks for an administrator password wich I don't know, so I tried lilo (sudo apt-get install lilo, sudo lilo -M /dev/sda mbr) from the live cd but that didn't do anything, so is there some way to restore it?

---

### Post by TeoBigusGeekus on 2011-06-05
[https://help.ubuntu.com/community/Grub2#ChRoot]("https://help.ubuntu.com/community/Grub2#ChRoot")
I hope you have a live cd/usb.

---

### Post by link15 on 2011-06-05
that didn't do anything and I'm not sure if i did it quite right because I didn't understand any of it, I just copied and pasted it in, modifying it as it asked, and also it used to go through the windows bootloader and then grub, and, yes I have access to both

---

### Post by link15 on 2011-06-05
any other suggestions?

---

### Post by drs305 on 2011-06-05
I would boot a LiveCD, download, extract and run the Boot Info Script, and make a post in the Wubi megathread:
[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

Explain what happened, and post the contents of RESULTS.txt. It will give a good indication of the status of your boot files.

You can get to the boot info script page by clicking the BIS link in my signature line.

It sounds like you have overwritten the Windows info in the MBR to point to Ubuntu, which won't work as it's accessible via the Windows bootloader. The readers of that thread are experienced users of both Ubuntu and Windows and can probably help you out.

---

### Post by link15 on 2011-06-05
I'm using a dell dimension 3000 and when I boot a livecd and click try ubuntu and it starts the gui is COMPLETELY messed up and it flashes, it was doing this with the install until I switched to Ubuntu classic (no effects) so is there any way to boot the livecd with no effects so it's usable? I was accessing the terminal through ctrl+alt+f2

---

### Post by drs305 on 2011-06-05
To obtain and run the boot info script it doesn't really matter which LiveCD you use, so if you have the one you originally installed Ubuntu with it should work. (It does make a difference for some repairs, but that's for later.)

If you only have the one CD, you can try pressing F6 as soon as you see the 2 icons in the bottom center of the screen. You may have to press ESC if you get the language screen, but pressing F6 a second time should show a menu from which you can turn off certain elements during the boot (such as nomodeset). Here is a link explaining it. Perhaps selecting one or more of the options will help it boot.
[https://help.ubuntu.com/community/LiveCDBootOptions]("https://help.ubuntu.com/community/LiveCDBootOptions")

---

### Post by link15 on 2011-06-05
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 256 for /boot/burg.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/burg/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>....... ......0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 5176384 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064     7,827,455     7,819,392   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       f067c3bc-7497-48e7-a7d2-84988a0d8b84   ext3       
/dev/sda1        A6787938787907F7                       ntfs       
/dev/sdb1        92F2-9B97                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------

======================== sda1/Wubi/boot/grub/grub.cfg: =========================

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
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root A6787938787907F7
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root A6787938787907F7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=A6787938787907F7 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root A6787938787907F7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=A6787938787907F7 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root A6787938787907F7
    drivemap -s (hd0) ${root}
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

======================== sda1/Wubi/boot/burg/burg.cfg: =========================

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
  load_string '+theme_menu { -fortune { command="set theme_name=fortune" }}'
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
set root='(/dev/loop0)'
search --no-floppy --fs-uuid --set 186d9774-2f9b-411b-b6b8-07366b847037
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry 'Ubuntu GNU/Linux, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(/dev/loop0)'
    search --no-floppy --fs-uuid --set 186d9774-2f9b-411b-b6b8-07366b847037
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=186d9774-2f9b-411b-b6b8-07366b847037 ro  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu GNU/Linux, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(/dev/loop0)'
    search --no-floppy --fs-uuid --set 186d9774-2f9b-411b-b6b8-07366b847037
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=186d9774-2f9b-411b-b6b8-07366b847037 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a6787938787907f7
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/burg.d/30_os-prober ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
--------------------------------------------------------------------------------

============================= sda1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  14.353637695 = 15.412101120   boot/burg/burg.cfg                             1
   6.134361267 = 6.586720256    boot/burg/core.img                             1
   4.767959595 = 5.119557632    boot/grub/grub.cfg                             1
   1.402565002 = 1.505992704    boot/initrd.img-2.6.38-8-generic               1
   4.767955780 = 5.119553536    boot/vmlinuz-2.6.38-8-generic                  1
   1.402565002 = 1.505992704    initrd.img                                     1
   4.767955780 = 5.119553536    vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by drs305 on 2011-06-05
Grub is installed in the sda MBR as suspected. What happened when you installed lilo? It appears to me that should have returned you to the Windows bootloader/menu, so if they both wouldn't boot at least you would have Windows...

 I'm not a Windows guy, which is why suggested you post this in the Wubi megathread. Or if you get Windows booting again, find a BURG thread to help restore BURG if that's what you want to use instead of Grub. 

If you end up in another thread please stay there and just link this thread if necessary. That will prevent duplicate posts/threads.

---

### Post by link15 on 2011-06-05
the lilo thing made it work, when I was doing it frome the command line in the gui instead of ctrl+alt+f1 but windows doesn't work and I don't know the password to my login, and I think it was caused by this [http://blog.ryantadams.com/2008/05/10/use-the-recovery-console-without-a-password/]("http://blog.ryantadams.com/2008/05/10/use-the-recovery-console-without-a-password/")

---

### Post by link15 on 2011-06-05
any suggestions for getting windows working so I can login, ubuntu works just fine

---

### Post by link15 on 2011-06-06
I got it to work thanks to this guide [http://www.psychocats.net/ubuntucat/resetwindowspassword/]("http://www.psychocats.net/ubuntucat/resetwindowspassword/"):popcorn::D;)

---

### Post by drs305 on 2011-06-06
:-)

That's a nice link. I'm not that familiar with Windows but it's a good one to save.

If you don't have any more related issues, would you please mark the thread SOLVED via the 'Thread Tools' link at the top right of the first post.

Happy Ubuntu-ing !

---

