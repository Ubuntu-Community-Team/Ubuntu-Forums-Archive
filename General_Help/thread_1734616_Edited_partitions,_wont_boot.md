---
title: "Edited partitions, wont boot"
date: 2011-04-20
forum: General Help
---

### Post by kingbirdy on 2011-04-20
My windows install (dual boot windows 7 and natty beta 2) had two partitions on it, a C and D drive. I emptied the D drive, and put in my beta 2 live cd to edit partitions. I deleted the partition corresponding to the D drive, and resized my ubuntu partition to utilize the available space. now, when I try and boot, I get an error, and am prompted for a rescue command. I am currently operating off of my live CD, but I need to get back to normal. Any help?

---

### Post by timgood on 2011-04-20
You may need to re-install Grub. Instructions are available [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

Let me know how you get on.

---

### Post by kingbirdy on 2011-04-20
followed the instructions, but now I get a screen telling me the grub version, and it tells me to press tab for a command list or to autocomplete. I tried a few commands, like boot and linux, but was told there was no kernel selected.

---

### Post by Ad@m on 2011-04-20
Follow method 3 - chroot.

But in your case you also need to edit or check the /etc/fstab file and make sure it is pointing to the correct partitions.

---

### Post by kingbirdy on 2011-04-20
I got to the unmounting bit, and it says
```
sudo: unmount: command not found
```

---

### Post by timgood on 2011-04-20
Can you post your fstab file...

---

### Post by drs305 on 2011-04-20
the command is "umount" not "unmount".

If you aren't able to fix things, please download the boot info script. Run it from the LiveCD and post the contents of RESULTS.txt
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by kingbirdy on 2011-04-20
where would that be?

---

### Post by kingbirdy on 2011-04-20
> **drs305 said:**
> the command is "umount" not "unmount".

If you aren't able to fix things, please download the boot info script. Run it from the LiveCD and post the contents of RESULTS.txt
[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)
ah, thank you! It worked well, except I can only boot into windows. There is no Ubuntu option. Should I just do the whole thing over and see if it adds ubuntu this time?

---

### Post by drs305 on 2011-04-20
> **kingbirdy said:**
> ah, thank you! It worked well, except I can only boot into windows. There is no Ubuntu option. Should I just do the whole thing over and see if it adds ubuntu this time?

We really can't give you good advice since we don't know the status of your system without seeing the RESULTS.txt contents...

---

### Post by kingbirdy on 2011-04-20
If you can tell me where to find it, I shall surely share!

---

### Post by drs305 on 2011-04-20
> **kingbirdy said:**
> If you can tell me where to find it, I shall surely share!

It's the link in Post #7. When you copy the contents, click the # icon in the post's menu bar. This will generate 'code' tags. Paste the contents between the tags. It's helps us read the contents, which are fairly lengthy.

---

### Post by kingbirdy on 2011-04-20
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for #l.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /bootmgr /Boot/BCD /grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30942895 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       411,647       409,600   7 HPFS/NTFS
/dev/sda2             411,648   104,445,987   104,034,340   7 HPFS/NTFS
/dev/sda3         104,450,046   281,638,911   177,188,866   f W95 Ext d (LBA)
/dev/sda5         279,916,544   281,638,911     1,722,368  82 Linux swap / Solaris
/dev/sda6         104,452,096   274,141,183   169,689,088  83 Linux
/dev/sda7         274,143,232   279,900,159     5,756,928  82 Linux swap / Solaris
/dev/sda4         281,638,912   312,581,807    30,942,896  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        40ECE936ECE926BE                       ntfs                                     
/dev/sda2        F47EE8667EE8235A                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        5E7CA5607CA53425                       ntfs       LENOVO_PART                   
/dev/sda5        e966d3c8-7a74-4151-894b-2801868134b5   swap                                     
/dev/sda6        7ecd34f3-9b34-4505-a17b-8f663e6a2874   ext4                                     
/dev/sda7        e7db3fb3-d8b0-42fc-a595-2ae6a2e8e464   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set=root 7ecd34f3-9b34-4505-a17b-8f663e6a2874
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 40ECE936ECE926BE
set locale_dir=($root)/grub/locale
set lang=en_US
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 40ECE936ECE926BE
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 5E7CA5607CA53425
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

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: grub/core.img
    ??GB: grub/grub.cfg

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 7ecd34f3-9b34-4505-a17b-8f663e6a2874
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 7ecd34f3-9b34-4505-a17b-8f663e6a2874
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 7ecd34f3-9b34-4505-a17b-8f663e6a2874
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=7ecd34f3-9b34-4505-a17b-8f663e6a2874 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 7ecd34f3-9b34-4505-a17b-8f663e6a2874
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=7ecd34f3-9b34-4505-a17b-8f663e6a2874 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 7ecd34f3-9b34-4505-a17b-8f663e6a2874
    linux    /boot/vmlinuz-2.6.38-7-generic root=UUID=7ecd34f3-9b34-4505-a17b-8f663e6a2874 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 7ecd34f3-9b34-4505-a17b-8f663e6a2874
    echo    'Loading Linux 2.6.38-7-generic ...'
    linux    /boot/vmlinuz-2.6.38-7-generic root=UUID=7ecd34f3-9b34-4505-a17b-8f663e6a2874 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-7-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 7ecd34f3-9b34-4505-a17b-8f663e6a2874
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 7ecd34f3-9b34-4505-a17b-8f663e6a2874
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 40ECE936ECE926BE
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 5E7CA5607CA53425
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e7db3fb3-d8b0-42fc-a595-2ae6a2e8e464 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  64.3GB: boot/grub/core.img
  57.1GB: boot/grub/grub.cfg
  57.2GB: boot/initrd.img-2.6.38-7-generic
  63.1GB: boot/initrd.img-2.6.38-8-generic
  64.5GB: boot/vmlinuz-2.6.38-7-generic
  61.1GB: boot/vmlinuz-2.6.38-8-generic
  63.1GB: initrd.img
  57.2GB: initrd.img.old
  61.1GB: vmlinuz
  64.5GB: vmlinuz.old

```

---

### Post by drs305 on 2011-04-20
Thanks for posting the results.

Grub2 was installed in the Windows partition. We need to point it to the Ubuntu partition.

From the LiveCD:

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
Don't use the partition number in the second command.

After rebooting into your normal installation, if you didn't see an option for Windows in the Grub2 menu, run:
```
sudo update-grub
```

---

### Post by kingbirdy on 2011-04-20
haha! you fixed it! thank you much!

---

