---
title: "Ubuntu-CentOS dual boot problem"
date: 2011-09-30
forum: General Help
---

### Post by mansourk on 2011-09-30
Hi all,
today i installed centos6 on my laptop, which already had an ubuntu 10.04 installed on it. during installation i resized the ubuntu partition, to install centos on the resulting space. the installion completed and i was nowhere asked where to install grub. my problem is that now i can't boot into ubuntu. please help me to fix this problem.
best

---

### Post by oldfred on 2011-09-30
Just to know where everything is installed:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by mansourk on 2011-09-30
Hi,
thanks for your quick reply. i logged into centos and  did what you said.
the contents of generated RESULT.TXT file:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy0.97 is installed in the MBR of /dev/sda and looks at sector 
    376870128 on boot drive #1 for the stage2 file.  A stage2 file is at this 
    location on /dev/sda.  Stage2 looks on partition #3 for /grub/grub.conf..

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  FAT16
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda4: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

vg_mansour-lv_root': ___________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

vg_mansour-lv_home': ___________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg_mansour-lv_swap': ___________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   376,834,047   376,832,000  83 Linux
/dev/sda2         602,572,798   625,141,759    22,568,962   5 Extended
/dev/sda5         602,572,800   625,141,759    22,568,960  82 Linux swap / Solaris
/dev/sda3         376,834,048   377,858,047     1,024,000  83 Linux
/dev/sda4         377,858,048   602,570,751   224,712,704  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/vg_mansour-lv_home ca27ceee-60a6-407d-b05b-6f3b798e2a61   ext4       
/dev/mapper/vg_mansour-lv_root 04ad6468-27de-4cb4-befe-847553df3390   ext4       _CentOS-6.0-x86_
/dev/mapper/vg_mansour-lv_swap 55ddac5a-0444-49a8-8153-575af15d1afe   swap       
/dev/sda1        f0174ff7-a873-49be-a8aa-68cbd18d2f08   ext4       
/dev/sda3        6c00caef-6f0b-41ca-9b55-7225a694f00a   ext4       
/dev/sda4        0yD458-W3h6-pab0-qv67-a8Fs-jJRP-eAu7ts LVM2_member 
/dev/sda5        e6739359-2c3a-4914-bbf5-bd8199844a52   swap       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
vg_mansour-lv_home
vg_mansour-lv_root
vg_mansour-lv_swap

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/vg_mansour-lv_home /home                    ext4       (rw)
/dev/mapper/vg_mansour-lv_root /                        ext4       (rw)
/dev/sda3        /boot                    ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
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
search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=f0174ff7-a873-49be-a8aa-68cbd18d2f08 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=f0174ff7-a873-49be-a8aa-68cbd18d2f08 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=f0174ff7-a873-49be-a8aa-68cbd18d2f08 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
    echo    'Loading Linux 2.6.32-32-generic ...'
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=f0174ff7-a873-49be-a8aa-68cbd18d2f08 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=f0174ff7-a873-49be-a8aa-68cbd18d2f08 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=f0174ff7-a873-49be-a8aa-68cbd18d2f08 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=f0174ff7-a873-49be-a8aa-68cbd18d2f08 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=f0174ff7-a873-49be-a8aa-68cbd18d2f08 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=f0174ff7-a873-49be-a8aa-68cbd18d2f08 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=f0174ff7-a873-49be-a8aa-68cbd18d2f08 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f0174ff7-a873-49be-a8aa-68cbd18d2f08 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f0174ff7-a873-49be-a8aa-68cbd18d2f08 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0174ff7-a873-49be-a8aa-68cbd18d2f08
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# Commented out by Dropbox
# /dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e6739359-2c3a-4914-bbf5-bd8199844a52 none            swap    sw              0       0
/dev/sda1 / ext4 errors=remount-ro,user_xattr 0 1
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  21.303474426 = 22.874431488   boot/grub/core.img                             1
 160.822071075 = 172.681383936  boot/grub/grub.cfg                             2
  21.314998627 = 22.886805504   boot/initrd.img-2.6.32-21-generic              1
  68.918895721 = 74.001100800   boot/initrd.img-2.6.32-29-generic              1
   5.514598846 = 5.921255424    boot/initrd.img-2.6.32-30-generic              2
   6.051174164 = 6.497398784    boot/initrd.img-2.6.32-31-generic              2
 163.438426971 = 175.490674688  boot/initrd.img-2.6.32-32-generic              1
  22.127922058 = 23.759675392   boot/initrd.img-2.6.32-33-generic              3
  21.303081512 = 22.874009600   boot/vmlinuz-2.6.32-21-generic                 1
  21.335330963 = 22.908637184   boot/vmlinuz-2.6.32-29-generic                 1
  21.341556549 = 22.915321856   boot/vmlinuz-2.6.32-30-generic                 1
  21.443710327 = 23.025008640   boot/vmlinuz-2.6.32-31-generic                 1
  21.345836639 = 22.919917568   boot/vmlinuz-2.6.32-32-generic                 1
  21.999004364 = 23.621251072   boot/vmlinuz-2.6.32-33-generic                 1
  22.127922058 = 23.759675392   initrd.img                                     3
 163.438426971 = 175.490674688  initrd.img.old                                 1
  21.999004364 = 23.621251072   vmlinuz                                        1
  21.345836639 = 22.919917568   vmlinuz.old                                    1

============================= sda3/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_mansour-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title CentOS Linux (2.6.32-71.el6.x86_64)
    root (hd0,2)
    kernel /vmlinuz-2.6.32-71.el6.x86_64 ro root=/dev/mapper/vg_mansour-lv_root rd_LVM_LV=vg_mansour/lv_root rd_LVM_LV=vg_mansour/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us crashkernel=128M rhgb quiet
    initrd /initramfs-2.6.32-71.el6.x86_64.img
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 179.700130463 = 192.951545856  grub/grub.conf                                 1
 179.700130463 = 192.951545856  grub/menu.lst                                  1
 179.705786705 = 192.957619200  grub/stage2                                    1
 179.719180107 = 192.972000256  initramfs-2.6.32-71.el6.x86_64.img             3
 179.705680847 = 192.957505536  vmlinuz-2.6.32-71.el6.x86_64                   2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on vg_mansour-lv_root'


Unknown BootLoader on vg_mansour-lv_home'


Unknown BootLoader on vg_mansour-lv_swap'



========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg_mansour-lv_root': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/vg_mansour-lv_root': No such file or directory
hexdump: /dev/mapper/vg_mansour-lv_root': Bad file descriptor
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg_mansour-lv_home': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/vg_mansour-lv_home': No such file or directory
hexdump: /dev/mapper/vg_mansour-lv_home': Bad file descriptor
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg_mansour-lv_swap': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/vg_mansour-lv_swap': No such file or directory
hexdump: /dev/mapper/vg_mansour-lv_swap': Bad file descriptor
mdadm: No arrays found in config file or automatically

```

---

### Post by oldfred on 2011-09-30
I do not know lvm. In Ubuntu to get boot script to parse the lvm:
sudo apt-get install lvm2

Try pasting these into your grub.conf, both should work, but I am not positive:

```
title    Most Current Ubuntu on sda1
root    (hd0,0)
kernel   /vmlinuz root=/dev/sda1 ro quiet splash
initrd  /initrd.img

title Ubuntu 11.04
root (hd0,0)
kernel /grub/core.img
boot

```I have not seen an extended partiiton reported as FAT16. Is script confused or me?

---

### Post by mansourk on 2011-12-04
Hi Oldfred,

Thanks a lot for your help. I added the following lines to /boot/grub/grub.conf and /boot/grub/menu.lst files and the problem solved.
```
title Ubuntu (2.6.32-33-generic)
    root (hd0,0)
kernel    /boot/vmlinuz-2.6.32-33-generic root=UUID=f0174ff7-a873-49be-a8aa-68cbd18d2f08 ro   quiet splash
initrd    /boot/initrd.img-2.6.32-33-generic
```

---

