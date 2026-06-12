---
title: "URGENT - GRUB 2 cannot load XP - Dual boot"
date: 2011-02-10
forum: General Help
---

### Post by Jim Hornet on 2011-02-10
Please need help

On reboot the GRUB2 installer shows me the options for OS - I select Windows XP and then I get a blank screen with a flashing cursor - and nothing..

I CTRL ALT DEL and it reboots back to GRUB2 and I select UBUNTU and I log in.

This is the first time I have tried to reboot Windows XP after fresh install of UBUNTU

What can I do I have tried a few options but did not help

[http://linux.koolsolutions.com/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://linux.koolsolutions.com/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)

> fdisk -l /dev/sda

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x92dd92dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13380   107473952    7  HPFS/NTFS
/dev/sda2           13381       30402   136723457    5  Extended
/dev/sda5           13381       30019   133652480   83  Linux
/dev/sda6           30020       30402     3069952   82  Linux swap / Solaris

> # update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done

so I dont understand why I cant get into my XP?

---

### Post by MiKOTRON on 2011-02-10
Could you post your menu.lst for us.
```
gedit /boot/grub/menu.lst
```

---

### Post by Jim Hornet on 2011-02-10
Hi Mikotron

I tried what you suggested  and it opened an empty folder

---

### Post by MiKOTRON on 2011-02-10
Hang on a sec while I try to find your grub configuration file.  I use the old grub you use the new one.



Okay try this
```
*gedit /etc/default/grub
```*

---

### Post by Jim Hornet on 2011-02-10
> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

There it is

---

### Post by MiKOTRON on 2011-02-10
I'm sorry bud, but I don't have much experience with GRUB2.  Check this link out, it might help.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Jim Hornet on 2011-02-10
Thanks Mikotron I will give it a go

> grub-install -v
grub-install (GRUB) 1.98+20100804-5ubuntu3


does anybody know if there is a command to start XP or how to uninstall GRUB2 interface - I need to get into XP to finish school project  - I have two hours ARGGG lol

---

### Post by ajgreeny on 2011-02-10
Please click on the boot-info-script in my signature, follow the instructions to download, using ubuntu, of course, and run the script, then paste the RESULTS.txt file back here between code tags (click the # in the toolbar of the text box when you reply).

PS:  What's the school project that you can't do in ubuntu?  Perhaps there is a way to use ubuntu instead of WinXP.

---

### Post by Jim Hornet on 2011-02-10
Edit Thanks AJGreeny - I have a Powerpoint presentaion I need to edit - but if I use OpenOffice it will mess with its structure when I save edits I am reading your link now

---

### Post by Jim Hornet on 2011-02-10
```
       Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   214,947,966   214,947,904   7 HPFS/NTFS
/dev/sda2         214,949,886   488,396,799   273,446,914   5 Extended
/dev/sda5         214,949,888   482,254,847   267,304,960  83 Linux
/dev/sda6         482,256,896   488,396,799     6,139,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1       1,433,656,665 1,945,680,344   512,023,680   7 HPFS/NTFS
/dev/sdb2              16,065 1,433,656,664 1,433,640,600   f W95 Ext d (LBA)
/dev/sdb5              16,128   204,828,749   204,812,622   7 HPFS/NTFS
/dev/sdb6         204,828,813   409,641,434   204,812,622   7 HPFS/NTFS
/dev/sdb7         409,641,498   921,649,049   512,007,552   7 HPFS/NTFS
/dev/sdb8         921,649,113 1,433,656,664   512,007,552   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        10046CC0046CAA84                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        78448ec1-c310-4f3e-b152-1b5e7839ece6   ext4                                     
/dev/sda6        18d51d93-96cb-4e8e-95ef-bbd10bfcdb5f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C264FB0F64FB04C7                       ntfs       FREE                          
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        2CBC56F6BC56B9D2                       ntfs       MUSIC                         
/dev/sdb6        18D8981DD897F6EA                       ntfs       GAMES                         
/dev/sdb7        A074BDAA74BD8416                       ntfs       MOVIES                        
/dev/sdb8        BC3C300F3C2FC2EE                       ntfs       DOWNLOADS                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 78448ec1-c310-4f3e-b152-1b5e7839ece6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 78448ec1-c310-4f3e-b152-1b5e7839ece6
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78448ec1-c310-4f3e-b152-1b5e7839ece6
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=78448ec1-c310-4f3e-b152-1b5e7839ece6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78448ec1-c310-4f3e-b152-1b5e7839ece6
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=78448ec1-c310-4f3e-b152-1b5e7839ece6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78448ec1-c310-4f3e-b152-1b5e7839ece6
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=78448ec1-c310-4f3e-b152-1b5e7839ece6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78448ec1-c310-4f3e-b152-1b5e7839ece6
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=78448ec1-c310-4f3e-b152-1b5e7839ece6 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78448ec1-c310-4f3e-b152-1b5e7839ece6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78448ec1-c310-4f3e-b152-1b5e7839ece6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 10046cc0046caa84
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
UUID=78448ec1-c310-4f3e-b152-1b5e7839ece6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=18d51d93-96cb-4e8e-95ef-bbd10bfcdb5f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 178.9GB: boot/grub/core.img
 213.6GB: boot/grub/grub.cfg
 213.6GB: boot/initrd.img-2.6.35-22-generic
 213.7GB: boot/initrd.img-2.6.35-25-generic
 178.9GB: boot/vmlinuz-2.6.35-22-generic
 179.0GB: boot/vmlinuz-2.6.35-25-generic
 213.7GB: initrd.img
 213.6GB: initrd.img.old
 179.0GB: vmlinuz
 178.9GB: vmlinuz.old
```

---

### Post by ajgreeny on 2011-02-10
At a quick look I can't see anything wrong there; gub.cfg seems to be pointing to the right windows partition, and it all seems totally normal.

I will keep looking and see if I can find anything else.

---

### Post by wilee-nilee on 2011-02-10
If you have a XP install disc you can boot it to the repair command line to run fixmbr.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Or you can load the lilo bootloader to load XP with these two commands from a booted Ubuntu cd.
Restore basic windows boot loader - universe enabled in software sources.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Both of these methods restore a MS bootloader. I think your problems with grub though may be as simple as running a chkdsk /r on XP to get it back in line after having re-sized it.

---

### Post by Jim Hornet on 2011-02-10
Thanks Guys 

I don't get why I am having this problem, I tried rebooting and same thing again. Thanks AJ for the help - at least I know the boot script is right.

Wilee-Nilee giving your suggestion a go right now Thanks

---

### Post by Jim Hornet on 2011-02-10
Thanks guys I got in using the XP recovery disk method and repaired MBR but had to delete LINUX partitions,

I dont know If I can go through the dual boot thing again I will have to get a separate PC for just LINUX only

Thanks again for your help

---

### Post by oldfred on 2011-02-10
The fixmbr is just a windows command line to reinstall the windows bootloader. 

You ran the full reinstall of windows from the vendors reinstall partition/DVD. This erases drive and reformats it to the same as the day you bought it. That is why you lost the Linux partitions.

---

