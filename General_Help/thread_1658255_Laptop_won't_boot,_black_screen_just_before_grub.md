---
title: "Laptop won't boot, black screen just before grub"
date: 2011-01-02
forum: General Help
---

### Post by danbaark on 2011-01-02
I installed Ubuntu 10.10 to dual boot alongside Windows 7 on a Dell Inspiron. This worked fine and after restarting it seemed to be working normally, after the first boot into windows though when I tried to restart the laptop again I just get a blank screen with a blinking cursor in the top left instead of the grub screen.

I'm still able to boot the LiveCD fine and tried to reinstall Ubuntu but the exact same thing happened? Anyone know what's going on/how to fix this? 

Thanks very much for any help

---

### Post by Foxheadz on 2011-01-02
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) in this guide scroll down to reinstalling grub. This should

---

### Post by Quackers on 2011-01-02
Do you have Dell Data Safe, by any chance?

---

### Post by danbaark on 2011-01-02
@Foxheadz thanks will try that now

@Quackers not sure but I have a dell utilities partition if that helps? Does it make a difference?

---

### Post by danbaark on 2011-01-02
@Foxheadz tried to follow those instructions and reinstall grub2 into the partition that windows boots from but now just get error: file not found 
grub rescue>

Where do I need to install it to/what files do I need to tweak for grub to find both Ubuntu and Windows bootloaders?

Thanks very much

---

### Post by SirDeBoben on 2011-01-02
> **danbaark said:**
> I installed Ubuntu 10.10 to dual boot alongside Windows 7 on a Dell Inspiron. This worked fine and after restarting it seemed to be working normally, after the first boot into windows though when I tried to restart the laptop again I just get a blank screen with a blinking cursor in the top left instead of the grub screen.

I'm still able to boot the LiveCD fine and tried to reinstall Ubuntu but the exact same thing happened? Anyone know what's going on/how to fix this? 

Thanks very much for any help
Do you have any peripherals plugged in? I had the same problem when my 2 TB external hard drive was plugged in. The screen may have been due to the bios searching for something bootable in the hard drive (I think), for doesn't the bios kick in before grub?

---

### Post by danbaark on 2011-01-02
No I don't, thanks though

---

### Post by Quackers on 2011-01-02
Presumably nothing boots now, is that correct?
If so, please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Rubi1200 on 2011-01-02
+1 for the boot script!

Also, please post the _full_ specifications for the laptop especially graphics card.

Thanks.

---

### Post by danbaark on 2011-01-02
Hi, thanks for all the help! I've reinstalled Ubuntu and it now boots  into Ubuntu but doesn't go into grub/I can't access the Windows 7  partition which I definitely need. 

This is the output of the bootinfo script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *        206,848    30,926,847    30,720,000   7 HPFS/NTFS
/dev/sda3          30,926,848   821,363,279   790,436,432   7 HPFS/NTFS
/dev/sda4         821,364,734   976,771,071   155,406,338   5 Extended
/dev/sda5         821,364,736   967,847,935   146,483,200  83 Linux
/dev/sda6         967,849,984   976,771,071     8,921,088  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        D86AF5BB6AF5968A                       ntfs       RECOVERY                      
/dev/sda3        18B4B7BBB4B799A8                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        78c604f9-d4bf-4ac1-958b-5e4767b6d02b   ext4                                     
/dev/sda6        840aa441-d97d-44e4-a3b6-dcb53abe1357   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set 78c604f9-d4bf-4ac1-958b-5e4767b6d02b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 78c604f9-d4bf-4ac1-958b-5e4767b6d02b
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78c604f9-d4bf-4ac1-958b-5e4767b6d02b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=78c604f9-d4bf-4ac1-958b-5e4767b6d02b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78c604f9-d4bf-4ac1-958b-5e4767b6d02b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=78c604f9-d4bf-4ac1-958b-5e4767b6d02b ro single 
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
    search --no-floppy --fs-uuid --set 78c604f9-d4bf-4ac1-958b-5e4767b6d02b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78c604f9-d4bf-4ac1-958b-5e4767b6d02b
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
UUID=78c604f9-d4bf-4ac1-958b-5e4767b6d02b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=840aa441-d97d-44e4-a3b6-dcb53abe1357 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 435.7GB: boot/grub/core.img
 476.5GB: boot/grub/grub.cfg
 421.6GB: boot/initrd.img-2.6.35-22-generic
 435.7GB: boot/vmlinuz-2.6.35-22-generic
 421.6GB: initrd.img
 435.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

Would be very grateful if anyone can tell me what's going on.

---

### Post by danbaark on 2011-01-02
As for graphics card it's an ATI Mobility Radeon HD 4650, i5 processor, 4gb Ram not sure what else you might need?

---

### Post by Quackers on 2011-01-02
From the Ubuntu desktop open a terminal and run ```
sudo update-grub
``` then watch as grub.cfg is run to see if the Windows Loader is picked up. If it is reboot and try to boot Windows.

---

### Post by Rubi1200 on 2011-01-02
Not sure if that will help right now:
sda2: 
> Boot files/dirs:   /bootmgr /Boot/BCD [COLOR=Red]/boot/grub/core.img[/COLOR]

> ### BEGIN /etc/grub.d/30_os-prober ###
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
Windows is not being picked up because there are GRUB files in its boot sector.

You need to restore the Windows bootloader and then reinstall GRUB.

---

### Post by danbaark on 2011-01-02
The output of sudo update-grub is:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

Windows isn't there?

Thanks again

---

### Post by danbaark on 2011-01-02
Any chance there's an easy way to do that? Dell have a recovery partition rather than CDs and I don't seem to be able to access that as it boots up (presumably because of the grub files?)

Any suggestions? Thanks a lot!

---

### Post by Quackers on 2011-01-02
I was hoping the grub file wouldn't interfere. I'm not sure about this bit though ```
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
```
Was this run from your Ubuntu installation or the Live cd?

---

### Post by danbaark on 2011-01-02
This was run from the installation.

---

### Post by Quackers on 2011-01-02
Hmm, it might be better to start from the beginning, as Rubi1200 suggests. Do you have a Windows repair disc?

---

### Post by Rubi1200 on 2011-01-02
Do you have a LiveCD?

If yes, we can boot the computer, install a generic bootloader, and then reinstall GRUB.

From the terminal on a LiveCD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```Ignore any warnings, we just want to get lilo installed to the MBR.

I would then restart and check to see that Windows is booting normally.

To reinstall GRUB, boot with the LiveCD again and run these commands:
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sda
```After rebooting, run this command in Ubuntu to pick up the Windows install:
```
sudo update-grub
```

---

### Post by danbaark on 2011-01-02
No I don't only a restore partition but I can't seem to access that, was going to try to use Supergrub to restore windows.

---

### Post by Quackers on 2011-01-02
One post up should sort things out

---

### Post by danbaark on 2011-01-12
In the end just got hold of a windows disc and reinstalled that from scratch (getting rid of the dell recovery partition) and then reinstalled Ubuntu using the default installer, worked fine this time round.

Thanks very much for all the help though.

---

### Post by morty71 on 2011-04-22
> **Rubi1200 said:**
> Do you have a LiveCD?

If yes, we can boot the computer, install a generic bootloader, and then reinstall GRUB.

From the terminal on a LiveCD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```Ignore any warnings, we just want to get lilo installed to the MBR.

I would then restart and check to see that Windows is booting normally.

To reinstall GRUB, boot with the LiveCD again and run these commands:
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sda
```After rebooting, run this command in Ubuntu to pick up the Windows install:
```
sudo update-grub
```
 
Thanks alot [Rubi1200]("http://ubuntuforums.org/member.php?u=1040746"), Today I ran into the same problem. I followed the steps and it just worked fine for me. I had both my ubuntu and windows back without reinstalling from scratch in less that 5 minutes.

---

