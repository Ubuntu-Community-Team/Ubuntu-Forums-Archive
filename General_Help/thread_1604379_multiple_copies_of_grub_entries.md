---
title: "multiple copies of grub entries"
date: 2010-10-23
forum: General Help
---

### Post by Aarnat on 2010-10-23
Hello all,
I am a relative noob with ubuntu.  I dual booted my laptop with Windows 7 and ubuntu 10.04 over the summer, fell in love with ubuntu, and recently upgraded to ubuntu 10.10 two days ago.  

After the upgrade, Grub has multiple entries of all the different operating systems.  Before you start yelling at me that they are older linux kernals and I should read other threads, that is not my problem.  Everything has 2 copies including the Windows 7 entry.  I searched these forums and didn't see anyone else with this problem. I did find a related chunk of terminal command line that shows all the grub entries I have.  Here is a copy of the terminal output: 
> 
aarnat@aarnat-laptop:~$ sudo update-grub
[sudo] password for aaron: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found Windows 7 (loader) on /dev/sda1
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found memtest86+ image: /boot/memtest86+.bin
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
aarnat@aarnat-laptop:~$This is roughly the order of the entries in grub when I start my laptop up.  As you can see there are multiple Linux kernel entries (which I am completely fine with as they are older kernel versions), but entries repeat itself after the Windows 7 entry.

Help would be great!  Thanks, Aarnat.

---

### Post by oldfred on 2010-10-23
Lets post this, but I think it is probably duplicates in the executables or if you edited the grub code something got duplicated.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

run this also as these are the files that generate the list:
```
ls -l  /etc/grub.d
```

---

### Post by Aarnat on 2010-10-24
Oldfred,
Here is the stuff you wanted (First, terminal output):

```

aarnat@aarnat-laptop:~$ ls -l /etc/grub.d
total 72
-rwxr-xr-x 1 root root 6831 2010-10-06 08:22 00_header
-rwxr-xr-x 1 root root 1481 2010-10-06 08:04 05_debian_theme
-rwxr-xr-x 1 root root 4757 2010-10-06 08:22 10_linux
-rwxr-xr-x 1 root root 6605 2010-04-13 09:57 10_os-prober
-rwxr-xr-x 1 root root 4594 2010-04-13 09:57 20_linux
-rwxr-xr-x 1 root root 5028 2010-10-06 08:22 20_linux_xen
-rwxr-xr-x 1 root root 1588 2010-09-24 14:16 20_memtest86+
-rwxr-xr-x 1 root root  918 2010-03-23 05:40 30_memtest86+
-rwxr-xr-x 1 root root 6933 2010-10-06 08:22 30_os-prober
-rwxr-xr-x 1 root root  214 2010-04-13 09:57 40_custom
-rwxr-xr-x 1 root root   95 2010-10-06 08:22 41_custom
-rw-r--r-- 1 root root  483 2010-04-13 09:57 README
aarnat@aarnat-laptop:~$ 

```Then the .txt file from that handy script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

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

/dev/sda1    *             63   314,568,764   314,568,702   7 HPFS/NTFS
/dev/sda2         314,568,765   482,512,274   167,943,510   7 HPFS/NTFS
/dev/sda3         482,512,275   608,349,419   125,837,145  83 Linux
/dev/sda4         608,349,420   625,137,344    16,787,925  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1F7F87340FA109CC                       ntfs       Windows 7                     
/dev/sda2        50AA53C9AA53AA6C                       ntfs       Storage                       
/dev/sda3        d8982b62-a7d2-420e-acf2-440f7840b18c   ext4                                     
/dev/sda4        2e3034a9-827d-49a8-ac1d-ee17325cf429   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/Storage           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/Windows_7         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set d8982b62-a7d2-420e-acf2-440f7840b18c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set d8982b62-a7d2-420e-acf2-440f7840b18c
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

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d8982b62-a7d2-420e-acf2-440f7840b18c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d8982b62-a7d2-420e-acf2-440f7840b18c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d8982b62-a7d2-420e-acf2-440f7840b18c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d8982b62-a7d2-420e-acf2-440f7840b18c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d8982b62-a7d2-420e-acf2-440f7840b18c
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=d8982b62-a7d2-420e-acf2-440f7840b18c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d8982b62-a7d2-420e-acf2-440f7840b18c
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=d8982b62-a7d2-420e-acf2-440f7840b18c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1f7f87340fa109cc
    chainloader +1
}
### END /etc/grub.d/10_os-prober ###

### BEGIN /etc/grub.d/20_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d8982b62-a7d2-420e-acf2-440f7840b18c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d8982b62-a7d2-420e-acf2-440f7840b18c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d8982b62-a7d2-420e-acf2-440f7840b18c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d8982b62-a7d2-420e-acf2-440f7840b18c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d8982b62-a7d2-420e-acf2-440f7840b18c
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=d8982b62-a7d2-420e-acf2-440f7840b18c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d8982b62-a7d2-420e-acf2-440f7840b18c
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=d8982b62-a7d2-420e-acf2-440f7840b18c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/20_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d8982b62-a7d2-420e-acf2-440f7840b18c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d8982b62-a7d2-420e-acf2-440f7840b18c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d8982b62-a7d2-420e-acf2-440f7840b18c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d8982b62-a7d2-420e-acf2-440f7840b18c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/30_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1f7f87340fa109cc
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda3    /    ext4    errors=remount-ro    0    1
/dev/sda2    /media/Storage    ntfs-3g    defaults,locale=en_US.utf8    0    0
/dev/sda1    /media/Windows_7    ntfs-3g    defaults,locale=en_US.utf8    0    0
/dev/sda4    none    swap    sw    0    0



=================== sda3: Location of files loaded by Grub: ===================


 255.7GB: boot/grub/core.img
 283.7GB: boot/grub/grub.cfg
 248.2GB: boot/initrd.img-2.6.32-25-generic
 250.0GB: boot/initrd.img-2.6.35-22-generic
 256.0GB: boot/vmlinuz-2.6.32-25-generic
 256.0GB: boot/vmlinuz-2.6.35-22-generic
 250.0GB: initrd.img
 248.2GB: initrd.img.old
 256.0GB: vmlinuz
 256.0GB: vmlinuz.old
```


Thanks!

---

### Post by oldfred on 2010-10-24
This is my list of files:

```
fred@fred-LucidDT:/media$ ls -l /media/Maverick/etc/grub.d
total 52
-rwxr-xr-x 1 root root 6831 2010-10-06 07:22 00_header
-rwxr-xr-x 1 root root 1481 2010-10-06 07:04 05_debian_theme
-rwxr-xr-x 1 root root 4757 2010-10-06 07:22 10_linux
-rwxr-xr-x 1 root root 5028 2010-10-06 07:22 20_linux_xen
-rwxr-xr-x 1 root root 1588 2010-09-24 13:16 20_memtest86+
-rwxr-xr-x 1 root root 6933 2010-10-06 07:22 30_os-prober
-rwxr-xr-x 1 root root  214 2010-10-06 07:22 40_custom
-rwxr-xr-x 1 root root   95 2010-10-06 07:22 41_custom
-rw-r--r-- 1 root root  483 2010-10-06 07:22 README

```You seem to have several duplicates with different versions.
You can turn off the executable bit to stop the duplicates from working. But why or how did you get duplicates? Did you want to move osprober to make windows first? Or did you install a customized grub2? I bet you customized it and then grub2 on the upgrade put the standard files back in.

sudo chmod a-x /etc/grub.d/10_os-prober
sudo chmod a-x /etc/grub.d/30_memtest86+


More info on grub and changing titles:
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

---

### Post by Aarnat on 2010-10-24
oldfred,
  Your second guess was correct.  My friend renamed the files so that they would load in a different order because I wanted Windows to open up first. I forgot that we did that, I will have him help me fix it.  Thanks for all the help!

Aarnat

---

### Post by garvinrick4 on 2010-10-24
Arnatt, under Thread tools in upper right of your thread please mark as solved.

---

