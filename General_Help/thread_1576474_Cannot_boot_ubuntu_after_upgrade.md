---
title: "Cannot boot ubuntu after upgrade"
date: 2010-09-17
forum: General Help
---

### Post by behzadsh on 2010-09-17
hi,
Yesterday I do upgrade my ubuntu from upgrade notifier.

when I restart my system, while booting ubuntu, boot splash screen has been changed to ubuntu 10.04 and four dot below, with low graphic. and after a while I received these messages.

> 
[FONT=Fixedsys]udevadm trigger is not permitted while udev is unconfigured
udevadm settle is not permitted while udev is unconfigured
udevadm settle is not permitted while udev is unconfigured
udevadm settle is not permitted while udev is unconfigured
/script/init-top/console-setup: .: line 18: can't open /etc/default/console-setup
ALERT! /dev/disk/by-uuid/87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca does not exist. Dropping to a shell!

BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu11) built in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[/FONT] 
I try to boot recovery mode, but I get the same messages.
I read other topics, but they didn't solve my problem!

what should I do ](*,):(

-----------
additional information:
ubuntu version: 10.04 lucid lynx
GNU GRUB version: 1.98-1ubuntu5
dual boot with Win7

---

### Post by drs305 on 2010-09-17
Let's see if it's just a bad fstab entry or something more severe...

Boot to a LiveCD.

Mount your Ubuntu partition. If you don't know which one it is, run these commands. If you still don't know, post the results (the second one is a lowercase L):
```
sudo blkid
fdisk -l 
``` 

To mount (Substitute XY for your partition, such as sda1, sda5, etc):
```
sudo mount /dev/sdXY /mnt
```

Open fstab for editing:
```
gksudo gedit /mnt/etc/fstab
```

Look for an entry with "87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca".
If it is the listing for **/**, change the first part of the line:
> UUID=87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca
to:
> /dev/sdXY 

If it isn't **/** or **/home**, just put a comment symbol (#) at the start of the line, like this:
> **# **UUID=87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca

Save the file and see if it now boots.

---

### Post by QLee on 2010-09-17
[QUOTE=behzadsh]
Yesterday I do upgrade my ubuntu from upgrade notifier.
...[/QUOTE]
I'm pretty sure I saw another recent thread about this, it was a kernel upgrade that did not generate an initrd image, solution was to manually create one.

---

### Post by behzadsh on 2010-09-17
> **drs305 said:**
> Let's see if it's just a bad fstab entry or something more severe...


I did not find anything :(
I attached the [ATTACH]169750[/ATTACH]

> **QLee said:**
> 
I'm pretty sure I saw another recent thread about this, it was a kernel  upgrade that did not generate an initrd image, solution was to manually  create one.     


how should I do that :(

---

### Post by Rubi1200 on 2010-09-17
For those concerned
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc       /proc           proc  nodev,noexec,nosuid  0  0  
/dev/sda5  /               ext4  errors=remount-ro    0  1  
/dev/sda6  none            swap  sw                   0  0  
/dev/sda4  /media/Windows  ntfs  defaults             0  0  
/dev/sda7  /media/Bridge   ntfs  defaults             0  0  
/dev/sda2  /media/Store    ntfs  defaults             0  0  
```

---

### Post by QLee on 2010-09-17
[QUOTE=behzadsh]
how should I do that :([/QUOTE]

You don't just run commands to fix anything until you have correctly identified the problem.

I mentioned what I did so you could have a look (I expected you to do a forum search after I mentioned seeing a recent thread) and see if it was related. Here is the link:
[http://ubuntuforums.org/showthread.php?t=1567060&highlight=udevadm+trigger+udev+unconfigured](http://ubuntuforums.org/showthread.php?t=1567060&highlight=udevadm+trigger+udev+unconfigured)

---

### Post by behzadsh on 2010-09-17
> **QLee said:**
> You don't just run commands to fix anything until you have correctly identified the problem.

I mentioned what I did so you could have a look (I expected you to do a forum search after I mentioned seeing a recent thread) and see if it was related. Here is the link:
[http://ubuntuforums.org/showthread.php?t=1567060&highlight=udevadm+trigger+udev+unconfigured](http://ubuntuforums.org/showthread.php?t=1567060&highlight=udevadm+trigger+udev+unconfigured)
I did it, but it doesn't worked for me! I'm trying to solve this whole today...

---

### Post by behzadsh on 2010-09-17
I followed every step in many threads, but no change happened.
I tried update-initramfs but no change... :(

please help...
All my applications, project and data is in my ubuntu :(

---

### Post by Rubi1200 on 2010-09-17
Can you boot the computer with an Ubuntu CD?

If yes, post the results of the bootscript linked to at the bottom of my post please.

---

### Post by behzadsh on 2010-09-17
here is the result,

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    41,945,087    41,738,240   7 HPFS/NTFS
/dev/sda3          41,947,134   178,257,239   136,310,106   5 Extended
/dev/sda5          41,947,136   146,803,389   104,856,254  83 Linux
/dev/sda6         146,818,098   150,705,764     3,887,667  82 Linux swap / Solaris
/dev/sda7         150,705,828   178,257,239    27,551,412  83 Linux
/dev/sda4         178,259,968   234,438,655    56,178,688   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        284AD7F34AD7BC2E                       ntfs       System Reserved               
/dev/sda2        9E00E55000E52FC7                       ntfs       Store                         
/dev/sda3: PTTYPE="dos" 
/dev/sda4        4C086B4A086B325E                       ntfs       Windows                       
/dev/sda5        87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca   ext4       ubuntu                        
/dev/sda6        de7e64b6-11de-4235-a54c-80ed6ce7dec2   swap                                     
/dev/sda7        1EFBA6737BE38607                       ntfs       Bridge                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/Store             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
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
search --no-floppy --fs-uuid --set 87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 87b9b1b3-0b82-4f19-bbb6-73d3cd7f71ca
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 284ad7f34ad7bc2e
    chainloader +1
}
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
proc       /proc           proc  nodev,noexec,nosuid  0  0  
/dev/sda5  /               ext4  errors=remount-ro    0  1  
/dev/sda6  none            swap  sw                   0  0  
/dev/sda4  /media/Windows  ntfs  defaults             0  0  
/dev/sda7  /media/Bridge   ntfs  defaults             0  0  
/dev/sda2  /media/Store    ntfs  defaults             0  0  

=================== sda5: Location of files loaded by Grub: ===================


  64.6GB: boot/grub/core.img
  30.4GB: boot/grub/grub.cfg
  47.2GB: boot/initrd.img-2.6.32-24-generic
  23.6GB: boot/vmlinuz-2.6.32-24-generic
  47.2GB: initrd.img
  23.6GB: vmlinuz

```

---

### Post by Rubi1200 on 2010-09-17
Did you try reinstalling Windows at some point?

And why do you have Windows in an extended partition (sda4)?

---

### Post by behzadsh on 2010-09-17
> **Rubi1200 said:**
> 
Did you try reinstalling Windows at some point?


yes I did. and reinstall grub from live disk
```

sudo grub-install --recheck --root-directory=/media/ubuntu /dev/sda

```> **Rubi1200 said:**
> 
And why do you have Windows in an extended partition (sda4)?

Windows is installed on sda2, formerly I have sabayon on sda4

-----------------------------

what should I do now!!!? :(

---

### Post by Rubi1200 on 2010-09-17
Look at the bootscript: sda2 has no Windows boot files and sda4 seems still to have something there. Also half the Windows boot files are on sda1 and on sda7.

It might be a good idea to first reinstall the Windows bootloader to the MBR and then we can work on getting Ubuntu back up and running (this assumes you cannot boot into Windows right now?).

---

### Post by behzadsh on 2010-09-17
> **Rubi1200 said:**
> Look at the bootscript: sda2 has no Windows boot files and sda4 seems still to have something there. Also half the Windows boot files are on sda1 and on sda7.

It might be a good idea to first reinstall the Windows bootloader to the MBR and then we can work on getting Ubuntu back up and running (this assumes you cannot boot into Windows right now?).

I'm on windows right now. maybe because of sda4 was mounted, sda4 have some boot information. I'm sure that windows is installed on sda2

---

### Post by Rubi1200 on 2010-09-17
I am running out of ideas, but let's try and reinstall GRUB with a different method and see if it works:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Use Method 3: CHROOT

Obviously, you need to make sure you mount the right partitions and install GRUB to the MBR of sda.

---

### Post by behzadsh on 2010-09-17
thank you Rubi1200, the link was helpful although I found a thread with the same problem that has been solved. [http://ubuntuforums.org/showthread.php?t=1575498](http://ubuntuforums.org/showthread.php?t=1575498) comment 6 & 8 was so helpful and I'm back on ubuntu right now :D 

I boot from ubuntu CD and do these:
```

sudo mount /dev/sdaX /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo cp /mnt/etc/resolv.conf /etc/resolv.conf
sudo chroot /mnt

```and with chroot do these:
```

dpkg --configure -a

```Special thanks to **Rubi1200** and [COLOR=DarkSlateGray]**[isantop]("http://ubuntuforums.org/member.php?u=394913")**[/COLOR]
Thread is mark as solved):P:D

---

### Post by Rubi1200 on 2010-09-17
You are more than welcome :D

I am really pleased you managed to get things working again!

---

