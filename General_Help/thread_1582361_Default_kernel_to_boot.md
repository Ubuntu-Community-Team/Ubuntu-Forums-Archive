---
title: "Default kernel to boot"
date: 2010-09-26
forum: General Help
---

### Post by peap on 2010-09-26
I'm running a headless HTPC and have both 2.6.32-22-generic and 2.6.32-24-generic
 kernels installed. Both are recognized by grub but I am not able to choose which one to boot.

By default 2.6.32-24-generic is booted and I have tried to edit /etc/default/grub (setting GRUB_DEFAULT=2) but this does not change the fact that 2.6.32-24 is booted. I ran "update-grub" after editing the file.

I should mention that I have installed xbmc-standalone that added the line below to my /etc/default/grub 

```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet acpi_enforce_resources=lax xbmc=autostart,nodiskmount,setvolume loglevel=0"
```

Even if I comment this line out xbmc STILL starts at boot. This means that /etc/default/grub is disregarded at boot, where is my bootup configured?

I can't get the grub menu to show by pressing ESC either...

I also have a file called /etc/default/grub.ucf-dist. Changing the boot options in this file doesn't seem to change anything, just like /etc/default/grub.

---

### Post by andrewthomas on 2010-09-26
post the output of 
```
cat /etc/default/grub
```

---

### Post by peap on 2010-09-26
Here we go:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=2
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet acpi_enforce_resources=lax xbmc=autostart,nodiskmount,setvolume loglevel=0"
#GRUB_CMDLIME_LINUX_DEFAULT="spash quiet"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1920x1080

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
#GRUB_GFXPAYLOAD_LINUX=1920x1080

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"

```

---

### Post by andrewthomas on 2010-09-26
```
gksu gedit /etc/default/grub
```

and comment out 

```
#GRUB_HIDDEN_TIMEOUT=0
```

then you should get a display of the grub menu

---

### Post by peap on 2010-09-26
That didn't change anything unfortunately. I'm thinking that /etc/default/grub is somehow overridden by some other settings?

---

### Post by drs305 on 2010-09-26
If you run *meierfra's* boot info script and post the results we can see what is happening:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

You might also see if there is anything in /boot/grub/grubenv. Don't worry about the # symbols and don't edit it directly. You are only interested in the first two lines.
```
cat /boot/grub/grubenv
```

Finally, Grub2 changed to the "SHIFT" key rather than "ESC" to reveal the Grub2 menu during boot.

---

### Post by peap on 2010-09-26
Here's the output from the boot info script. /boot/grub/grubenv has no entries. Hitting SHIFT on boot displays "Grub loading" briefly but no menu.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 67387648 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   614,610,943   614,608,896  83 Linux
/dev/sda2         614,612,990   625,141,759    10,528,770   5 Extended
/dev/sda5         614,612,992   625,141,759    10,528,768  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/cryptswap1 30180623-4d06-46cc-9e3d-b12e1ac0b273   swap                                     
/dev/sda1        bb3fde8e-ca40-46f9-a130-7a71b04ccf7b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
cryptswap1
cryptswap1_unformatted

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=bb3fde8e-ca40-46f9-a130-7a71b04ccf7b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bb3fde8e-ca40-46f9-a130-7a71b04ccf7b

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		bb3fde8e-ca40-46f9-a130-7a71b04ccf7b
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=bb3fde8e-ca40-46f9-a130-7a71b04ccf7b ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		bb3fde8e-ca40-46f9-a130-7a71b04ccf7b
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=bb3fde8e-ca40-46f9-a130-7a71b04ccf7b ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid		bb3fde8e-ca40-46f9-a130-7a71b04ccf7b
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=bb3fde8e-ca40-46f9-a130-7a71b04ccf7b ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		bb3fde8e-ca40-46f9-a130-7a71b04ccf7b
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=bb3fde8e-ca40-46f9-a130-7a71b04ccf7b ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Chainload into GRUB 2
root		bb3fde8e-ca40-46f9-a130-7a71b04ccf7b
kernel		/boot/grub/core.img

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		bb3fde8e-ca40-46f9-a130-7a71b04ccf7b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set bb3fde8e-ca40-46f9-a130-7a71b04ccf7b
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
search --no-floppy --fs-uuid --set bb3fde8e-ca40-46f9-a130-7a71b04ccf7b
set locale_dir=($root)/boot/grub/locale
set lang=
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set bb3fde8e-ca40-46f9-a130-7a71b04ccf7b
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=bb3fde8e-ca40-46f9-a130-7a71b04ccf7b ro   splash quiet acpi_enforce_resources=lax xbmc=autostart,nodiskmount,setvolume loglevel=0
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set bb3fde8e-ca40-46f9-a130-7a71b04ccf7b
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=bb3fde8e-ca40-46f9-a130-7a71b04ccf7b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set bb3fde8e-ca40-46f9-a130-7a71b04ccf7b
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=bb3fde8e-ca40-46f9-a130-7a71b04ccf7b ro   splash quiet acpi_enforce_resources=lax xbmc=autostart,nodiskmount,setvolume loglevel=0
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set bb3fde8e-ca40-46f9-a130-7a71b04ccf7b
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=bb3fde8e-ca40-46f9-a130-7a71b04ccf7b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set bb3fde8e-ca40-46f9-a130-7a71b04ccf7b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set bb3fde8e-ca40-46f9-a130-7a71b04ccf7b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bb3fde8e-ca40-46f9-a130-7a71b04ccf7b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=0ee8ace0-1ce7-427e-b157-c7c3a9d07a4f none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

# MyBookWorld
10.0.1.3:/nfs/Public/ /media/mbwsingle nfs rw,hard,intr 0 0
10.0.1.5:/nfs/Public/ /media/mbwdouble nfs rw,hard,intr 0 0

# Lillservern
10.0.1.2:/home/lillservern /media/lillservern nfs rw,hard,intr 0 0
10.0.1.2:/media/usbdrive /media/usb_lillservern nfs rw,hard,intr 0 0


=================== sda1: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
  50.4GB: boot/grub/grub.cfg
  34.5GB: boot/grub/menu.lst
  34.5GB: boot/grub/stage2
   6.1GB: boot/initrd.img-2.6.32-22-generic
  34.6GB: boot/initrd.img-2.6.32-24-generic
  34.6GB: boot/vmlinuz-2.6.32-22-generic
  34.6GB: boot/vmlinuz-2.6.32-24-generic
  34.6GB: initrd.img
   6.1GB: initrd.img.old
  34.6GB: vmlinuz
  34.6GB: vmlinuz.old

```

---

### Post by drs305 on 2010-09-26
update-grub may be updating grub legacy instead of grub2. Try running the following command. Use the third command to see if grub.cfg's default changed from 0 to 2.

```

grep "set default="  /boot/grub/grub.cfg  # probably displays 0
sudo grub-mkconfig -o /boot/grub/grub.cfg
grep "set default="  /boot/grub/grub.cfg # hopefully now displays 2

```

---

### Post by peap on 2010-09-26
That did the trick!

Thank you both for helping me (and hopefully others too) out.

---

### Post by drs305 on 2010-09-26
peap,

Glad your issue is solved. This still leaves the issue of dual grubs (legacy and 2) on your machine.

If you are ready to take a leap of faith, you can remove all traces of grub legacy by purging and installing Grub. Normally, you could run "upgrade-from-grub-legacy" but it doesn't look like you have a complete grub install.

If you want to do this, here is a link:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")
Since a chroot isn't necessary from a normal boot, you would run only steps 2-5, and need to use "sudo" at the start of the commands. I would probably also run the purge commands separately - first for just "grub" (it may say not installed) and then for grub-common / grub-pc.

Whether you want to alter a working system is up to you.

If you are content with what you have, and don't have any more questions, would you please mark the thread SOLVED via the "Thread Tools" link near the top right of the first post? Thanks.

---

### Post by peap on 2010-09-26
Normally I would like to go all the way with this kind of thing but in this case the system will stay static for a long time without any altering (HTPC of a friend) so I will mark the thread as solved.

Thanks for the link and information. Should I change my mind or run into similar problems again I'm sure it will be helpful.

---

### Post by peap on 2010-09-27
Just wanted to add that I followed your advice after giving it some thought and now my grub behaves like I expect it to do. (i.e. "update-grub" now works)

Thanks again.

---

