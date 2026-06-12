---
title: "grub prompt after ext3 -&gt; ext4"
date: 2011-03-19
forum: General Help
---

### Post by l07 on 2011-03-19
Yesterday, I first moved /home to a new ext4 partition, then I converted ubuntu partition from ext3 to ext4. For the latter I followed all the steps except for
```
sudo grub-install /dev/sda
```because I thought if I already had grub2, I didn't have to do anything. I did, however, run  
```
sudo update-grub
```Then I tried to delete old_home which I left in case something went wrong in the copying process. But delete didn't seem to work (I was in sudo nautilus, I forgot about gksudo) so I right-clicked - moved it to trash. But when I tried checking what's in the trash, it gave me some error about not being able to see some location and just kept displaying the busy cursor. So I tried to reboot, but on reboot I was pressented with a grub prompt, and when I typed boot, it said kernel wasn't loaded.

How do I boot into ubuntu?

---

### Post by l07 on 2011-03-19
After booting live, I'm looking at /boot/grub/grub/grub.cfg and it doesn't mention ext4 anywhere. I think that could mean grub configuration wasn't updated properly, even though the modification stamp is around the time I issued ```
sudo update-grub
```. I can post the contents if necessary.

---

### Post by l07 on 2011-03-19
I still need help. One solution I can think of is from a live cd issue
```
sudo grub-install /dev/sda
```
Would it help?

---

### Post by Rubi1200 on 2011-03-19
Hi,
we need to get a better overview of the current state of your setup.

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by l07 on 2011-03-19
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x84b01726

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,070,079    39,070,017  83 Linux
/dev/sda2          43,266,048    85,207,039    41,940,992  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        c586946d-5781-478d-bef6-f08b997d281f   ext4                                     
/dev/sda2        20750408-b2e2-4299-9562-97c4fd53cd6e   ext4       h                             

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/h                 ext4       (rw,nosuid,nodev,uhelper=hal)
/dev/sda1        /media/disk              ext4       (rw,nosuid,nodev,uhelper=hal)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c586946d-5781-478d-bef6-f08b997d281f

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Chainload into GRUB 2
uuid        c586946d-5781-478d-bef6-f08b997d281f
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 10.10, kernel 2.6.35-24-generic
uuid        c586946d-5781-478d-bef6-f08b997d281f
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro quiet splash
initrd        /boot/initrd.img-2.6.35-24-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid        c586946d-5781-478d-bef6-f08b997d281f
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro single
initrd        /boot/initrd.img-2.6.35-24-generic

title        Ubuntu 10.10, kernel 2.6.35-23-generic
uuid        c586946d-5781-478d-bef6-f08b997d281f
kernel        /boot/vmlinuz-2.6.35-23-generic root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro quiet splash
initrd        /boot/initrd.img-2.6.35-23-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid        c586946d-5781-478d-bef6-f08b997d281f
kernel        /boot/vmlinuz-2.6.35-23-generic root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro single
initrd        /boot/initrd.img-2.6.35-23-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        c586946d-5781-478d-bef6-f08b997d281f
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro quiet splash
initrd        /boot/initrd.img-2.6.35-22-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        c586946d-5781-478d-bef6-f08b997d281f
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, memtest86+
uuid        c586946d-5781-478d-bef6-f08b997d281f
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set default="2"
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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.37-0.dmz.6-liquorix-686' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    linux    /boot/vmlinuz-2.6.37-0.dmz.6-liquorix-686 root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro   quiet splash
    initrd    /boot/initrd.img-2.6.37-0.dmz.6-liquorix-686
}
menuentry 'Ubuntu, with Linux 2.6.37-0.dmz.6-liquorix-686 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    echo    'Loading Linux 2.6.37-0.dmz.6-liquorix-686 ...'
    linux    /boot/vmlinuz-2.6.37-0.dmz.6-liquorix-686 root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.37-0.dmz.6-liquorix-686
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c586946d-5781-478d-bef6-f08b997d281f /               ext4    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

UUID=20750408-b2e2-4299-9562-97c4fd53cd6e  /home    ext4          nodev,nosuid       0       2

=================== sda1: Location of files loaded by Grub: ===================


   7.8GB: boot/grub/core.img
  11.3GB: boot/grub/grub.cfg
   7.8GB: boot/grub/menu.lst
   7.9GB: boot/initrd.img-2.6.35-24-generic
   7.8GB: boot/initrd.img-2.6.35-25-generic
   7.9GB: boot/initrd.img-2.6.37-0.dmz.6-liquorix-686
   7.8GB: boot/vmlinuz-2.6.35-24-generic
   7.7GB: boot/vmlinuz-2.6.35-25-generic
   7.9GB: boot/vmlinuz-2.6.37-0.dmz.6-liquorix-686
   7.9GB: initrd.img
   7.8GB: initrd.img.old
   7.9GB: vmlinuz
   7.7GB: vmlinuz.old
```

---

### Post by l07 on 2011-03-19
Ok?

---

### Post by Rubi1200 on 2011-03-20
The results look fairly normal except for the fact that you seem to have a mix of GRUB-legacy and GRUB2.

My advice would be to purge and reinstall GRUB following the instructions in this fantastic guide by drs305:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You need to do this from a LiveCD and use the chroot method.

---

### Post by l07 on 2011-03-20
I'm following the procedure, but when I ran
```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet.
sudo chroot /mnt/temp
```The first line generated an error: mount: invalid option -- 'B.' The other two ran fine. Is there something I should change to make it run without errors? Note that I'm using a live cd of 9.04 which may have a different versioni of mount. If necessary, I can update it if you tell me how.

---

### Post by Rubi1200 on 2011-03-21
I think you need to try and get hold of either a 10.04 or 10.10 LiveCD to make this work. Version 9.04 used a different file-system than later versions which is possibly why you got this error.

---

### Post by l07 on 2011-03-28
I used 10.10 live cd to perform chroot procedure, but on reboot I had the same grub prompt. In addition, 10.10 live cd has issues: when booting, it might accept no password or might say "authentication failure". So I had to use the 9.04 to login and run the boot script again.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x84b01726

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,070,079    39,070,017  83 Linux
/dev/sda2          43,266,048    85,207,039    41,940,992  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        c586946d-5781-478d-bef6-f08b997d281f   ext4                                     
/dev/sda2        20750408-b2e2-4299-9562-97c4fd53cd6e   ext4       h                             

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.37-0.dmz.6-liquorix-686' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    linux    /boot/vmlinuz-2.6.37-0.dmz.6-liquorix-686 root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro   quiet splash
    initrd    /boot/initrd.img-2.6.37-0.dmz.6-liquorix-686
}
menuentry 'Ubuntu, with Linux 2.6.37-0.dmz.6-liquorix-686 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    echo    'Loading Linux 2.6.37-0.dmz.6-liquorix-686 ...'
    linux    /boot/vmlinuz-2.6.37-0.dmz.6-liquorix-686 root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.37-0.dmz.6-liquorix-686
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=c586946d-5781-478d-bef6-f08b997d281f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c586946d-5781-478d-bef6-f08b997d281f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c586946d-5781-478d-bef6-f08b997d281f /               ext4    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

UUID=20750408-b2e2-4299-9562-97c4fd53cd6e  /home    ext4          nodev,nosuid       0       2

=================== sda1: Location of files loaded by Grub: ===================


   7.8GB: boot/grub/core.img
  11.5GB: boot/grub/grub.cfg
   7.9GB: boot/initrd.img-2.6.35-24-generic
   7.8GB: boot/initrd.img-2.6.35-25-generic
   7.9GB: boot/initrd.img-2.6.37-0.dmz.6-liquorix-686
   7.8GB: boot/vmlinuz-2.6.35-24-generic
   7.7GB: boot/vmlinuz-2.6.35-25-generic
   7.9GB: boot/vmlinuz-2.6.37-0.dmz.6-liquorix-686
   7.9GB: initrd.img
   7.8GB: initrd.img.old
   7.9GB: vmlinuz
   7.7GB: vmlinuz.old
```

---

### Post by l07 on 2011-03-29
Is there something else I can try?

---

### Post by drs305 on 2011-03-29
> **l07 said:**
> Is there something else I can try?

The default is set to boot "Ubuntu, with Linux 2.6.37-0.dmz.6-liquorix-686". I know the regular kernels are 2.6.35... for Maverick. Have you tried booting one of them?

If you don't see the menu when you boot, hold down the SHIFT key until the menu appears.

---

### Post by coffeecat on 2011-03-29
> **l07 said:**
> I used 10.10 live cd to perform chroot procedure, but on reboot I had the same grub prompt. In addition, 10.10 live cd has issues: when booting, it might accept no password or might say "authentication failure". So I had to use the 9.04 to login and run the boot script again.

Did the chroot procedure complete without error? You don't say.

If the 10.10 CD has issues you need to burn another one. The live CD session should not prompt you for a password; if it does that often means a faulty CD. Make sure your ISO's md5sum is correct and try burning another CD.

---

### Post by l07 on 2011-03-31
I tried holding down the shift key but the menu doesn't appear no matter how I press it. If changing the kernel would help, can I edit some grub config file to set the kernel?
The cd boots fine on another, newer computer but I also checked it for errors using the menu on bootup - none were found. However, on that newer pc, after logging out, I had the same problem when trying to log back in - it didn't say "authentication failure," but required several attempts with an empty password nonetheless.

---

### Post by drs305 on 2011-03-31
> **l07 said:**
> I tried holding down the shift key but the menu doesn't appear no matter how I press it. If changing the kernel would help, can I edit some grub config ffile to set the kernel?
The cd works fine on another, newer computer but I also checked it for errors using the menu on bootup - none were found.

If you can get the LiveCD booted, you can mount your Ubuntu partition and change the grub.cfg file:

```
sudo mount /dev/sda1 /mnt
gksu gedit +71 /mnt/boot/grub/grub.cfg
```
It should open at line 71. Change **set default="0"** to 
> set default="2"
Save the file and reboot. This change will work until you update-grub so if it boots open /etc/default/grub, make the same change, and update-grub.

---

### Post by l07 on 2011-03-31
Booted 9.04. grub.cfg opens as read-only so I cannot save changes.

---

### Post by drs305 on 2011-03-31
> **l07 said:**
> Booted 9.04. grub.cfg opens as read-only so I cannot save changes.

Did you open it with "gksu gedit"  (as root)?

Also, if you were doing it from a LiveCD, you have to mount the partition with the real file and mount that one, otherwise you are trying to edit the CD's files.Change XY to the appropriate values (for you, sda1)
```

sudo mount /dev/sd**XY** **/mnt**
gksu gedit **/mnt**/boot/grub/grub.cfg
```

---

### Post by l07 on 2011-03-31
I did, I ran the code you posted.

---

### Post by drs305 on 2011-03-31
> **l07 said:**
> I did, I ran the code you posted.

Try using this code to change the properties:
```
sudo chmod +w /mnt/boot/grub/grub.cfg
```
In the earliest versions of G2 the file was marked as read-only. I remember there was a discussion at the time whether that applied to root as well. It shouldn't apply to recent Grub files in any case, unless you are installing Grub 1.97.

---

### Post by l07 on 2011-03-31
That worked. Going to reboot now.

---

### Post by l07 on 2011-03-31
I was able to boot properly. Thanks very much for your help. So why did the liquorix kernel not work now if it worked before?
 Grub version seems to be: grub-install (GRUB) 1.98+20100804-5ubuntu3

---

### Post by drs305 on 2011-03-31
Glad you eventually worked this out. 

Perhaps there was an update in something else that caused the kernel to fail. Since it isn't a standard kernel it probably isn't tested with other Ubuntu packages as thoroughly, if at all.

You could try to update the initrd file with *update-initramfs* just to see if it starts working again if you are really interested. It's a bit out of my knowledge area.

When you are finished with this thread please mark it solved via the 'Thread Tools' link near the top right of the first post.

Happy Ubuntu-ing !

---

