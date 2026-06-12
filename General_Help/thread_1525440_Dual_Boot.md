---
title: "Dual Boot"
date: 2010-07-06
forum: General Help
---

### Post by crackpotfox on 2010-07-06
Well, this isn't your usual windows and Ubuntu dual boot question. I would like to dual boot Ubuntu 10.04 and Fedora 13. I have 20 GB set aside for Fedora and Ubuntu is already installed. I know that I need to not install the boot loader in Fedora (GRUB) and I have done that. Fedora is not detected in my grub from Ubuntu.

How to I get Fedora to be detected by Grub. Do I need to reinstall Fedora?

Also, I deleted Windows, but my grub still has Visa on the boot menu.

---

### Post by ScarletWyvern on 2010-07-06
You need to update your menu.

```
sudo update-grub
```

---

### Post by crackpotfox on 2010-07-06
Ok, i ran that command and it got rid of windows, but didn't detect fedora... I did restart my comp, btw

---

### Post by lordofhumankind on 2010-07-06
I have a similar problem, with Arch and Ubuntu. The issue is that in this case they are on different hard drives, and I cannot access the drive of the one from the other. So far I have been just changing the priority in BIOS, but that is a clumsy workaround.

---

### Post by oldfred on 2010-07-06
Grub2's osprober finds it and supposedly the newest finds it correctly.

this is older info:
 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)
menuentry "Fedora 2.6.31.5 on sda7" {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a2cb340e-b3df-44e3-a602-52d0cb1201c5
    linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=a2cb340e-b3df-44e3-a602-52d0cb1201c5 ro         quiet splash
    initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
}

---

### Post by crackpotfox on 2010-07-06
well, i tried osprober and update grub... nothing works. i wish that people would just give straight answers instead of links that give no help... i've been searching for days all over google for help...

---

### Post by wilee-nilee on 2010-07-06
> **lordofhumankind said:**
> I have a similar problem, with Arch and Ubuntu. The issue is that in this case they are on different hard drives, and I cannot access the drive of the one from the other. So far I have been just changing the priority in BIOS, but that is a clumsy workaround.

There is a key prompt to choose the boot device it's a f key or esc just look up your computer model on Google or test keys. You don't have to go into bios to choose the boot.

---

### Post by crackpotfox on 2010-07-06
yes, but that gives me hard drive, cd, and network. i have been booting from hard drive since it is the only bootable thing i have

---

### Post by wilee-nilee on 2010-07-06
> **crackpotfox said:**
> yes, but that gives me hard drive, cd, and network. i have been booting from hard drive since it is the only bootable thing i have

Sorry, I was answering another post.

---

### Post by crackpotfox on 2010-07-06
ah... makes sense;)

---

### Post by oldfred on 2010-07-06
Did you try either of the suggestions I posted. Linkd gave info on details:
1. Custom entry into 40_custom
2. Chainboot to Fedora's boot loader in the Fedora partition boot sector.

To see if you installed it:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by emanresu on 2010-07-07
i don't know if 10.4 uses GRUB, but i'm guessing it does? if that's the case, you can use a disk partitioning utility. forgot the name, but do an Internet search for disk partitioning and you'll find a couple of utilities. those are good to have in case your computer gets whacked by something bad anyway. 

you'll have to delete one of your existing master partitions like everyone else has said to do, but the disk partition utility (dpu) will let change the deleted partition to an extended partition. once you've set up the new extended partitions where you want them, you can then use an Ubuntu disc to install Ubuntu to one of the new partitions. you might have to tweak your grub list to get your partitions to show. 

i don't know everything about this, i only know enough to be dangerous ;) , in this case, how to set up my laptop to dual boot XP and Ubuntu. i've copied part of my grub menu ([_**I]UBUNTU 9.04[/I]**_ /boot/grub/menu.lst) for you to see something how you'll want grub to offer you your boot options once you've installed the other OSes you want.

```
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
# kopt=root=UUID=2948729c-1ca0-4451-8cda-ed8a35746614 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2948729c-1ca0-4451-8cda-ed8a35746614
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
#title           Other operating systems:
#root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            2948729c-1ca0-4451-8cda-ed8a35746614
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=2948729c-1ca0-4451-8cda-ed8a35746614 ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            2948729c-1ca0-4451-8cda-ed8a35746614
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=2948729c-1ca0-4451-8cda-ed8a35746614 ro  single
initrd          /boot/initrd.img-2.6.28-11-generic
#title          Ubuntu 9.04, kernel 2.6.24-22-generic
#uuid           2948729c-1ca0-4451-8cda-ed8a35746614
#kernel         /boot/vmlinuz-2.6.24-22-generic root=UUID=2948729c-1ca0-4451-8cda-ed8a35746614 ro quiet splash

title           Ubuntu 9.04, memtest86+
uuid            2948729c-1ca0-4451-8cda-ed8a35746614
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title          Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title          Microsoft Windows XP Home Edition
#rootnoverify   (hd0,0)
#savedefault
#makeactive
#chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title          Windows NT/2000/XP
#rootnoverify   (hd0,1)
#savedefault
#makeactive
#chainloader    +1

```

---

### Post by crackpotfox on 2010-07-07
all right, i did the boot script and here are the results:

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    192,653,312   193,677,311     1,024,000  83 Linux
/dev/sda2               2,046   192,651,479   192,649,434   5 Extended
/dev/sda5               2,048   191,687,579   191,685,532  83 Linux
/dev/sda6         191,687,643   192,651,479       963,837  82 Linux swap / Solaris
/dev/sda3         193,677,312   234,440,703    40,763,392  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        eacd2f90-a788-4974-89a6-52edaeef2839   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        rZNu7N-q1jH-KSUl-auX6-QNgV-eIFF-ZC1wh1 LVM2_member                               
/dev/sda5        a3ae514f-2e55-44a0-8209-ca65f8a6aa5a   ext4                                     
/dev/sda6        e9f0f542-b654-4d24-a694-ce69c2f7995b   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=================== sda1: Location of files loaded by Grub: ===================


  98.6GB: initramfs-2.6.33.3-85.fc13.i686.img
  98.6GB: vmlinuz-2.6.33.3-85.fc13.i686

=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set a3ae514f-2e55-44a0-8209-ca65f8a6aa5a
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
search --no-floppy --fs-uuid --set a3ae514f-2e55-44a0-8209-ca65f8a6aa5a
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a3ae514f-2e55-44a0-8209-ca65f8a6aa5a
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=a3ae514f-2e55-44a0-8209-ca65f8a6aa5a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a3ae514f-2e55-44a0-8209-ca65f8a6aa5a
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=a3ae514f-2e55-44a0-8209-ca65f8a6aa5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a3ae514f-2e55-44a0-8209-ca65f8a6aa5a
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a3ae514f-2e55-44a0-8209-ca65f8a6aa5a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a3ae514f-2e55-44a0-8209-ca65f8a6aa5a
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a3ae514f-2e55-44a0-8209-ca65f8a6aa5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a3ae514f-2e55-44a0-8209-ca65f8a6aa5a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a3ae514f-2e55-44a0-8209-ca65f8a6aa5a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a3ae514f-2e55-44a0-8209-ca65f8a6aa5a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a3ae514f-2e55-44a0-8209-ca65f8a6aa5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a3ae514f-2e55-44a0-8209-ca65f8a6aa5a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a3ae514f-2e55-44a0-8209-ca65f8a6aa5a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a3ae514f-2e55-44a0-8209-ca65f8a6aa5a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e9f0f542-b654-4d24-a694-ce69c2f7995b none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   2.4GB: boot/grub/core.img
   2.6GB: boot/grub/grub.cfg
   2.4GB: boot/initrd.img-2.6.32-21-generic
   2.5GB: boot/initrd.img-2.6.32-22-generic
  11.8GB: boot/initrd.img-2.6.32-23-generic
   2.4GB: boot/vmlinuz-2.6.32-21-generic
   2.4GB: boot/vmlinuz-2.6.32-22-generic
  11.5GB: boot/vmlinuz-2.6.32-23-generic
  11.8GB: initrd.img
   2.5GB: initrd.img.old
  11.5GB: vmlinuz
   2.4GB: vmlinuz.old
```

---

### Post by oldfred on 2010-07-07
=================== sda1: Location of files loaded by Grub: ===================


  98.6GB: initramfs-2.6.33.3-85.fc13.i686.img
  98.6GB: vmlinuz-2.6.33.3-85.fc13.i686

 If sda1 is Fedora boot then it looks like it is missing:
 /grub/menu.lst or  /grub/grub.conf
The osprober uses the grub file to know what to boot. But I do not know if it is grub legacy's menu.lst or grub2's grub.cfg or perhaps with Fedora they use grub.conf.

Other theads with Fedora issues. 
[http://ubuntuforums.org/showthread.php?t=1494063&highlight=Fedora](http://ubuntuforums.org/showthread.php?t=1494063&highlight=Fedora)
[http://ubuntuforums.org/showthread.php?t=1370222&highlight=Fedora](http://ubuntuforums.org/showthread.php?t=1370222&highlight=Fedora)
[http://ubuntuforums.org/showthread.php?t=1463437&highlight=Fedora](http://ubuntuforums.org/showthread.php?t=1463437&highlight=Fedora)

---

### Post by alesserfate on 2010-07-07
Haha I am trying to do the same thing as you are (dual boot ubuntu fedora and ended up destroying both my installs and grub so started from scratch).

I have

/dev/sda1 - ubuntu 9.1
/dev/sda2 - fedora 13

MBR is on /dev/sda1 obv. i didnt make a boot partition

the new GRUB loader was written by fedora onto /dev/sda1

I got the fedora to load from the grub, I've edited it a few times but can't seem to get the right syntax for ubuntu to load and keeping getting invalid argument errors.

Anyone have a sample of code needed to load ubuntu from menu conf file of the boot loader ?

edit: both are installed already, /dev/sda1 is my old ubuntu install., /dev/sda2 is a fresh fedora install

---

### Post by oldfred on 2010-07-07
alesserfate
This has an example but you have to adjust to your current versions & partitions. I do not think you can have fedora's boot in the Ubuntu partition without the potential of conflict.

[http://ubuntuforums.org/showthread.php?t=1505897&highlight=fedora](http://ubuntuforums.org/showthread.php?t=1505897&highlight=fedora)

---

### Post by alesserfate on 2010-07-08
> **oldfred said:**
> alesserfate
This has an example but you have to adjust to your current versions & partitions. I do not think you can have fedora's boot in the Ubuntu partition without the potential of conflict.

[http://ubuntuforums.org/showthread.php?t=1505897&highlight=fedora](http://ubuntuforums.org/showthread.php?t=1505897&highlight=fedora)

thanks..still at it though :@

---

