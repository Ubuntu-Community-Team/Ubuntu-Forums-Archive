---
title: "Hello everyone..Can I have some help please"
date: 2010-12-04
forum: General Help
---

### Post by Sumato on 2010-12-04
Hello everyone,
I installed edubuntu 10.10 today on my daughters laptop side by side with Vista,
the laptop shut off unexpectedly during the install of edubuntu,when I restarted the laptop,
the vista came right up..the live-cd does not load from her auto-play,
so I installed it again via livecd boot first,
it completed the install,yet when it rebooted,there was no choice of OS's to pick,went right into vista,when I went into my computer it showed the lack of space in the partitions,yet no other partitions.

Is there a way I can uninstall the bad install..keep the good install..and have it show a choice boot menu to pick edubuntu - and - vista ?

Thank You !!

---

### Post by wangsuda on 2010-12-04
sounds like a GRUB error. Can you boot into GRUB? If you can, you can see how many OSs you have installed and then choose which OS to boot in to. Once you determine which ones you want to keep, you can use G-Parted to delete the unwanted OSs. 

PLEASE - before you try deleting partitions, see if others have better advice. 

BTW, I also run Edubuntu.

---

### Post by Sumato on 2010-12-04
thanks for the quick reply !

Nope,
cant boot into grub at all..tried the live disk and still tries to install or do live-cd.

---

### Post by wangsuda on 2010-12-04
OK, try this: when your computer starts to boot, hold down the "SHIFT" key the second the BIOS screen appears. Keep holding it until the words "GRUB LOADING" appear. Then post what you see.

---

### Post by wilee-nilee on 2010-12-04
Lets try this always sounds promising, but without some key information it is difficult at best follow this bit oh instructions.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

### Post by Sumato on 2010-12-04
thanks for the help..
( holding the shift key did nada}

ok this is what came up when I ran the script.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 320016088 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    24,563,384    24,563,322  27 Hidden HPFS/NTFS
/dev/sda2    *     24,563,712   256,700,415   232,136,704   7 HPFS/NTFS
/dev/sda3         256,700,416   315,241,437    58,541,022   7 HPFS/NTFS
/dev/sda4         315,242,494   488,396,799   173,154,306   5 Extended
/dev/sda5         372,856,832   483,586,047   110,729,216  83 Linux
/dev/sda6         483,588,096   488,396,799     4,808,704  82 Linux swap / Solaris
/dev/sda7         315,242,496   370,386,943    55,144,448  83 Linux
/dev/sda8         370,388,992   372,852,735     2,463,744  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8640A9BFE49BED2A                       ntfs       PQSERVICE                     
/dev/sda2        18E4938EE4936CAE                       ntfs       ACER                          
/dev/sda3        0C22D71822D7061C                       ntfs       DATA                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        db09bb9e-7505-454c-a8e8-b404af5d0d47   ext4                                     
/dev/sda6        6f021397-2981-4d96-adb9-26dfdeeb4c08   swap                                     
/dev/sda7        d171f81b-c827-4193-a5bf-d5f66939a757   ext4                                     
/dev/sda8        760180ae-eb8b-442d-88da-2d5269e5ffd1   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
UUID=db09bb9e-7505-454c-a8e8-b404af5d0d47 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6f021397-2981-4d96-adb9-26dfdeeb4c08 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 240.5GB: boot/vmlinuz-2.6.35-22-generic
 240.5GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set d171f81b-c827-4193-a5bf-d5f66939a757
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set d171f81b-c827-4193-a5bf-d5f66939a757
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set d171f81b-c827-4193-a5bf-d5f66939a757
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d171f81b-c827-4193-a5bf-d5f66939a757 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set d171f81b-c827-4193-a5bf-d5f66939a757
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d171f81b-c827-4193-a5bf-d5f66939a757 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set d171f81b-c827-4193-a5bf-d5f66939a757
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set d171f81b-c827-4193-a5bf-d5f66939a757
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8640a9bfe49bed2a
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 18e4938ee4936cae
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set db09bb9e-7505-454c-a8e8-b404af5d0d47
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=d171f81b-c827-4193-a5bf-d5f66939a757 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=760180ae-eb8b-442d-88da-2d5269e5ffd1 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 163.8GB: boot/grub/core.img
 174.7GB: boot/grub/grub.cfg
 170.7GB: boot/initrd.img-2.6.35-22-generic
 163.8GB: boot/vmlinuz-2.6.35-22-generic
 170.7GB: initrd.img
 163.8GB: vmlinuz
```Now whats it mean ?

---

### Post by wilee-nilee on 2010-12-04
So to get the grub menu to give to a choice it is missing right now, so which is the install you want to keep sda5 or sda7.

To be honest if it was me I would just boot the live install cd or thumb whatever your using and just delete sda4,5,6,7,8 and just do the install again to the free space, just be sure that the grub bootloader is pointed at sda not a partition which is sda with a number after it.

Use gparted on the live cd to just delete all the Linux, and reinstall.

Ask more questions, if needed, as it is Vista is working as the acer bootloader is in the mbr.

---

### Post by Sumato on 2010-12-04
The vista partition needs to stay..
so I will use the partition manager in the live install to delete the partitions that are not ntfs..then install the good one on the new clear partition.
how can I make sure it doesnt happen again ?

---

### Post by wilee-nilee on 2010-12-04
> **Sumato said:**
> The vista partition needs to stay..
so I will use the partition manager in the live install to delete the partitions that are not ntfs..then install the good one on the new clear partition ?

Yeah that is the easiest fix here, it is possible we could spend time on fixing the double installs but a reinstall will be much faster.

If your using a thumb to install every once in a wile it will put grub in its mbr, loading the mbr is really easy so the main thing is just cleaning out the debris and reinstalling.

---

### Post by Sumato on 2010-12-04
ok I am init now and I see locks..that wont let me delete anything without unmounting,
yet I dont see how to unmount it from the gparted ?

---

### Post by wilee-nilee on 2010-12-05
> **Sumato said:**
> ok I am init now and I see locks..that wont let me delete anything without unmounting,
yet I dont see how to unmount it from the gparted ?

So if your using the live cd right click on the two swaps and turn them off, in gparted

---

### Post by Sumato on 2010-12-05
hmm,
doesnt give me that option when i right click,
on the swaps I get the option to swap or info..
the ext4 I get options to ,delete,move to,format,etc etc

---

### Post by deserthowler on 2010-12-05
I am embarrassed :redface: to admit this but I have installed different versions of Ubuntu about 50 times and have never figured out the partition manager.](*,)

Boot in the live CD, go to synaptic, and install gparted.  (this will install gparted in memory).  Remove all of the unwanted partitions using gparted from the menu.  Then reboot and install edubuntu.

Earl

---

### Post by wilee-nilee on 2010-12-05
> **Sumato said:**
> hmm,
doesnt give me that option when i right click,
on the swaps I get the option to swap or info..
the ext4 I get options to ,delete,move to,format,etc etc

So take a screen shot of gparted and post it. Here is what you should be seeing with a right click on the swaps.
[ATTACH]177442[/ATTACH]

I guess I had mine turned off but I think you get the idea, this can only be done from the Live cd/thumb environment as far as deleting.

---

### Post by Sumato on 2010-12-05
> **deserthowler said:**
> 

Boot in the live CD, go to synaptic, and install gparted.  (this will install gparted in memory).  Remove all of the unwanted partitions using gparted from the menu.  Then reboot and install edubuntu.

Earl

Thank You,
but I am far too new into this to even try synaptic..let alone know what it is .

---

### Post by Sumato on 2010-12-05
Oi..

I think I might have figured this with your help..
I will try it out and see what happens real quick

---

### Post by wilee-nilee on 2010-12-05
> **Sumato said:**
> Thank You,
but I am far too new into this to even try synaptic..let alone know what it is .

You should be on the booted live Ubuntu cd gparted is on there already.
I recognize your goal is edubuntu I'm just not familiar with its live booted cd enviroment.

Are we on the same page your using the booted live cd, or a loaded thumb correct?

---

### Post by Sumato on 2010-12-05
That did the trick guys,
Gparted took care of it after I "swappedON" the partitions..

Thank You for all the help !!

---

