---
title: "Help!! Grub2 Loads the Recovery Partition of Win7"
date: 2011-03-07
forum: General Help
---

### Post by tripialos on 2011-03-07
Hello everyone

As a big supporter of Ubuntu, after installing Ubuntu 10.10 on my mums laptop i decided to also install it on my sisters Acer Aspire one netbook.

The specific netbook had pre-installed Win7 starter. Everything went really smooth with the installation with ubuntu 10.10, Grub menu was also loading pretty well but when i chose to load on windows it loads the recovery partition of the hard drive.

The issue is that the netbook, like most netbooks and laptops, has a hidden partition which is used to recover Windows on the system. My Grub2 loader added this partition as an option to load windows with result me not be able to boot on windows ...well i do can load but it loads the recovery of windows.

Any ideas how to change that?

Much appreciate

Thanks

---

### Post by Quackers on 2011-03-07
Do you have 2 entries for Windows Loader in the grub menu?
Please quote the exact names and details. Thanks.

---

### Post by tripialos on 2011-03-07
No there is only one

---

### Post by tripialos on 2011-03-07
1. Ubuntu GNU/Linux, with Linux 2.6.35-22-generic
2. Ubuntu GNU/Linux, with Linux 2.6.35-22-generic (recovery mode)
3. Windows Vista (loader)(on /dev/sda1)

---

### Post by Quackers on 2011-03-07
Sorry, I was somewhere else.
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by tripialos on 2011-03-07
```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/burg.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2          25,176,062   100,485,119    75,309,058   f W95 Ext d (LBA)
/dev/sda5          25,176,064    33,576,959     8,400,896   7 HPFS/NTFS
/dev/sda6          33,579,008    98,531,327    64,952,320  83 Linux
/dev/sda7          98,533,376   100,485,119     1,951,744  82 Linux swap / Solaris
/dev/sda4         100,486,575   488,392,064   387,905,490   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AE70D3A370D37097                       ntfs       PQSERVICE                     
/dev/sda2: PTTYPE="dos" 
/dev/sda4        DEE62720E626F883                       ntfs       Windows7                      
/dev/sda5        D20A80DC0A80BF4B                       ntfs       System                        
/dev/sda6        b0326fd4-1bd6-4457-9402-1b0880860736   ext4                                     
/dev/sda7        925b03f1-402f-456c-9af0-cb66a229369f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /media/System            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set b0326fd4-1bd6-4457-9402-1b0880860736
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set b0326fd4-1bd6-4457-9402-1b0880860736
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set b0326fd4-1bd6-4457-9402-1b0880860736
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b0326fd4-1bd6-4457-9402-1b0880860736 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set b0326fd4-1bd6-4457-9402-1b0880860736
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b0326fd4-1bd6-4457-9402-1b0880860736 ro single 
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set b0326fd4-1bd6-4457-9402-1b0880860736
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set b0326fd4-1bd6-4457-9402-1b0880860736
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set ae70d3a370d37097
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
# / was on /dev/sdb6 during installation
UUID=b0326fd4-1bd6-4457-9402-1b0880860736 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=925b03f1-402f-456c-9af0-cb66a229369f none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  28.1GB: boot/grub/core.img
  30.3GB: boot/grub/grub.cfg
  34.5GB: boot/initrd.img-2.6.35-22-generic
  28.1GB: boot/vmlinuz-2.6.35-22-generic
  34.5GB: initrd.img
  28.1GB: vmlinuz


```

---

### Post by Quackers on 2011-03-07
Again, sorry for my absence.
Ok, the Windows loader is pointing at sda1, which has a couple of boot files in it, but they appear to be for a recovery partition and are not in the correct format to boot your main Win 7 system, which is on sda4.
The boot flag is on sda1 at the moment, so your Windows loader appears to be trying to boot the recovery partition.
What I would suggest is to move the boot flag to sda4, then boot from a Windows 7 repair cd (or installation disc) and run the repair console.
Do you have a Win 7 repair/installation disc (NOT a set of recovery dvd's)?

---

### Post by tripialos on 2011-03-07
Please, you dont have to apologise for anything, i really appreciate your immediate responses, its more than enough.

:-(, how did it get so messed up with the partitions.....unfortunately i dont have recovery DVDs nor i can make any from the recovery menu.

Is there any other way to do this without the cds??

---

### Post by tripialos on 2011-03-07
Emm, just in case i didn't understand , i do have a windows 7 installation disk but it is not the one for the netbook. The CD i have is Windows 7 Enterprise, will that do the work (the version of win7 on the netbook is the starter one)

---

### Post by Quackers on 2011-03-07
It may be enough. I don't actually know whether that disc has the repair functions.
Two more questions.
Do you have gparted installed in your Ubuntu system
and
do you have access to another Win 7 (or vista) machine?

---

### Post by Quackers on 2011-03-07
> **tripialos said:**
>  how did it get so messed up with the partitions.....unfortunately i dont have recovery DVDs nor i can make any from the recovery menu.

Is there any other way to do this without the cds??

It may be that you have deleted a small partition (maybe only 100MB) which had your Win7 boot files in it. Could that be?

---

### Post by tripialos on 2011-03-07
i used paragon partition manager to merge the main C drive and create the 30gb partition for the ubuntu install.When the partition manager finished the merge i then began the ubuntu installation and followed the usual procedure.

I do have access to another windows 7 machine and also to another machine with  windows XP

Gparted..hmm no i dont think i have gparted..i do tho have installed burg manager.

Could be possible paragon partition manager to accidental erased those 100 mb? i really dont know :-S

---

### Post by Quackers on 2011-03-07
Maybe it disappeared in the merge. It really isn't important. The main thing is that 2 boot files need to be put on the sda4 partition so that Win 7 can boot. I hope the resizing of the partition ran ok. Windows 7 doesn't like to be resized by anything other than Windows disk management.
We'll see.
If the other Win 7 machine has a cd drive and you have a spare empty cd, we're in business.
But first, in Ubuntu open up a terminal and copy/paste this in ```
sudo apt-get install gparted
``` then enter your password at the prompt. The program should install quickly.
Then go to System > Admin > gparted.
When the window opens it will take a few seconds to scan your hard drive for partitions.
When it's done right-click on the /dev/sda4 partition and select "manage flags" and in the little window that appears click on the box next to "boot" and OK that window.
Then on the right side of the /dev/sda4 partition you will see the word "boot" appear in a column. If you don't see that, click on the green tick in the toolbar to apply the change. When boot appears on the right side you can close gparted.
Then
start up the other pc and go to Control Panel > Backup & Restore centre then in the left pane there will be an option to "make a recovery cd". Put a cd in the drive and click on that option. It will take no more than a few minutes. Then you can boot from that cd (after selecting the cd drive as the first boot device in your computer's bios.

Depending on the disc you may need to press a key during boot to enter the recovery console.
When the recovery console opens up (ignore the startup repair) and select the "Command Prompt" option (if necessary clicking on the advanced or other options bottom left of the screen).
When the command prompt opens, type in ```
bootrec.exe /fixmbr
```
NOTE there is a space between exe and /fixmbr
Press enter.
Hopefully it will run reporting no errors. If it does, reboot. 
Now, Windows 7 should boot directly as grub has just been over-written!
If it does that's ok as long as you have an Ubuntu live cd/usb.
Then shutdown again and this time boot from the Ubuntu live cd or usb and select "try ubuntu" NOT "install ubuntu"!
When the desktop loads open up a terminal and copy/paste these commands in, one line at a time, pressing enter after each line
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
If that reports no errors you can then reboot and Ubuntu should boot up automatically.
If it does, open up a terminal and run
```
sudo update-grub
```
and watch as grub.cfg is run. It should pick up a Windows loader for /dev/sda1 and a new one for /dev/sda4.
If it does, reboot and your new grub menu should then boot Windows (from the /dev/sda4 entry).

If you get stuck just holler.
Good luck :-)

---

### Post by tripialos on 2011-03-09
Ok..it really got messed up...when i tried to mount sda6 i was having an error that this device did not existed...when i "ls|grep sd"  i had sda,sda1,sdb1,sdb2,sdb3,sdb,4...sdb6...so i changed the mounting to sdb6......

After finishing all the steps above i rebooted and windows gave me an error (that couldn't boot ntdlr...something like that)....the grub menu was only coming back only if i had the usb on (i run the grub installation from a usb not a cd)

Anyway, i saw that things where pretty messed up and i decided to restore the netbook to factory settings by using the recovery partition. I then did the installation of Ubuntu and now everything works perfect.

Thanks alot for you help..once again!

Much appreciated

---

### Post by YesWeCan on 2011-03-09
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/**[COLOR="Red"]burg[/COLOR]**.
```

Curious.

---

