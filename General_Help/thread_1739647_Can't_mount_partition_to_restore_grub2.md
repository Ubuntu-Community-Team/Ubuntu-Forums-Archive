---
title: "Can't mount partition to restore grub2"
date: 2011-04-26
forum: General Help
---

### Post by CoolStoryBro on 2011-04-26
Hey all,

I recently installed windows 7 and of course it got rid of grub2 for me. I tried restoring it but when I try to mount the ubuntu partition (sda3, extended filesystem) I get the error "mount: you must specify the filesystem type" 

I tried searching the net but can't find the answer. 

Please help me :guitar:

---

### Post by AndyBoy_LV on 2011-04-26
Please post the output of your 

```
sudo fdisk -l
```

command

---

### Post by CoolStoryBro on 2011-04-26
Hi Andy, thanks for posting.

Results are:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9269113e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       29358   235714560    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           29359       34581    41952875+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4           34582      121601   698988150    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           34362       34581     1767118+  82  Linux swap / Solaris
```

---

### Post by AndyBoy_LV on 2011-04-26
You cannot mount Extended partitions. You can mount subpartitions of an extended partition, which in you case are /dev/sda4 and /dev/sda5. 

Are you sure you did not format Linux partition while installing Windows? Because i see no Linux partitions under /dev/sda3 except for swap on /dev/sda5.

---

### Post by CoolStoryBro on 2011-04-26
Yeah I think I got rid of it somehow. I reinstalled Ubuntu but I didn't get grub back. It boots straight to Ubuntu. Here's my new fdisk.

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9269113e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       29358   235714560    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           29359       34581    41952875+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4           34582      121601   698988150    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           34362       34581     1767118+  82  Linux swap / Solaris
/dev/sda6           29359       34361    40184832   83  Linux
```

How do I get grub2 and Windows 7 back :confused:

---

### Post by CoolStoryBro on 2011-04-26
Bump :frown:

---

### Post by Quackers on 2011-04-26
Boot from the live cd/usb and select "try ubuntu".
Open a terminal and run these commands
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Then reboot. Ubuntu should boot directly. Open a terminal and run ```
sudo update-grub
``` to update grub menu to include Windows Loader.

---

### Post by CoolStoryBro on 2011-04-26
Hey Quackers,

Thanks for posting. I tried what you said and got this message when I updated grub:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-28-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done
```

My PC still boots straight to Ubuntu with no grub showing.

---

### Post by Quackers on 2011-04-26
If you have a look in synaptic package manager and enter "os-prober" in the search box, it should appear in the main window with a green box to its left, if it is installed. If it isn't installed right-click on it and mark it for installation, then apply the change.
Then re-run sudo update-grub.

If it's already installed please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by CoolStoryBro on 2011-04-26
OK here's the text file:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   471,635,967   471,429,120   7 HPFS/NTFS
/dev/sda3         471,638,014   555,543,764    83,905,751   5 Extended
/dev/sda5         552,009,528   555,543,764     3,534,237  82 Linux swap / Solaris
/dev/sda6         471,638,016   552,007,679    80,369,664  83 Linux
/dev/sda4         555,543,765 1,953,520,064 1,397,976,300   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        108AACB58AAC992C                       ntfs       System Reserved               
/dev/sda2        724CDAD24CDA9069                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        9A7C84D67C84AE97                       ntfs       New Volume                    
/dev/sda5        a6f9ca5a-faff-45ca-9406-f7738a734381   swap                                     
/dev/sda6        00014807-b7e8-43d2-ba30-56a51a698997   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 00014807-b7e8-43d2-ba30-56a51a698997
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 00014807-b7e8-43d2-ba30-56a51a698997
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 00014807-b7e8-43d2-ba30-56a51a698997
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=00014807-b7e8-43d2-ba30-56a51a698997 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 00014807-b7e8-43d2-ba30-56a51a698997
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=00014807-b7e8-43d2-ba30-56a51a698997 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 00014807-b7e8-43d2-ba30-56a51a698997
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 00014807-b7e8-43d2-ba30-56a51a698997
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=00014807-b7e8-43d2-ba30-56a51a698997 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a6f9ca5a-faff-45ca-9406-f7738a734381 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 263.0GB: boot/grub/core.img
 263.1GB: boot/grub/grub.cfg
 249.5GB: boot/initrd.img-2.6.35-28-generic-pae
 263.0GB: boot/vmlinuz-2.6.35-28-generic-pae
 249.5GB: initrd.img
 263.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

Thank you for helping me :KS

---

### Post by Quackers on 2011-04-26
os-prober was already installed then.

The entry in red below should not be there.
You could try removing that folder by navigating there using gksudo nautilus in the terminal. You need to delete the /boot folder which has a /grub folder inside it. DO NOT DELETE the Windows /boot folder! Just the folder that has grub and core.img inside it.
This is in the Windows root.
```
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD [COLOR="Red"]/boot/grub/core.img[/COLOR]

```
Then re-run sudo update-grub.

---

### Post by CoolStoryBro on 2011-04-26
I'm not sure if I did the last step correctly but when I restarted the PC I got a screen that said:

GNU GRUB Version ...
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions.

What do I do now haha?

---

### Post by Quackers on 2011-04-26
Did you run sudo update-grub before you rebooted? What did it say?

Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by CoolStoryBro on 2011-04-26
Yeah, I did a update-grub. I can't remember exactly what it said but it was very short.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   471,635,967   471,429,120   7 HPFS/NTFS
/dev/sda3         471,638,014   555,543,764    83,905,751   5 Extended
/dev/sda5         552,009,528   555,543,764     3,534,237  82 Linux swap / Solaris
/dev/sda6         471,638,016   552,007,679    80,369,664  83 Linux
/dev/sda4         555,543,765 1,953,520,064 1,397,976,300   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        108AACB58AAC992C                       ntfs       System Reserved               
/dev/sda2        724CDAD24CDA9069                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        9A7C84D67C84AE97                       ntfs       New Volume                    
/dev/sda5        a6f9ca5a-faff-45ca-9406-f7738a734381   swap                                     
/dev/sda6        00014807-b7e8-43d2-ba30-56a51a698997   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=00014807-b7e8-43d2-ba30-56a51a698997 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a6f9ca5a-faff-45ca-9406-f7738a734381 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 267.3GB: boot/grub/core.img
 248.3GB: boot/grub/grub.cfg
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by Quackers on 2011-04-26
Hmm, as you can see form the first sda1 entry, /boot/grub/core.img is still there! It needs to be removed. Did you do that?

---

### Post by CoolStoryBro on 2011-04-26
I went to the bottom of the filesystem and deleted the "boot" folder that had a folder called "grub" inside which had the core.img.

Was that the correct way to do it?

---

### Post by Quackers on 2011-04-26
What do you mean by "bottom of the file system"? Presumably that was Windows file system? I'm suspecting that you did that to the Ubuntu file system, not the Windows file system.
According to the boot script /boot/grub/core.img is still in sda1

---

### Post by CoolStoryBro on 2011-04-26
I deleted the boot folder from the Ubuntu file system.

---

### Post by CoolStoryBro on 2011-04-26
wow this is getting very annoying. I have no clue how to solve this.

---

### Post by Quackers on 2011-04-26
You need to delete the /boot folder from the Windows root (but not the Windows boot folder), not Ubuntu :-)
We can repair grub after, but you need to get Windows booting first now.
In Ubuntu mount the Windows drive via Places menu. In teh first Windows screen what folders are there? There will be a boot folder. There may be another boot folder within that one that holds the /grub folder which has core.img in it. That's the folder that needs to be deleted. DO NOT DELETE the whole boot folder! Some of it is for Windows.
It may be that it will not let you delete the folder. You may need to navigate to Windows root via the terminal with gksudo nautilus command.
Post screenshots if not sure.

---

### Post by CoolStoryBro on 2011-04-26
Hey Quackers,

I got fed up of being on that black screen so I re-installed Ubuntu. Does this change anything or should I go ahead and delete that folder?

---

### Post by Quackers on 2011-04-26
Why do you think re-installing Ubuntu will help Windows boot? It won't.
There is something in with your Windows boot files that doesn't belong there. Windows won't boot with that file in there. Yes, you need to remove it.
Alternatively you can repair the Windows bootloader and boot files using a Windows repair disc or installation disc. This will over-write grub, which would need to be re-installed after.
I was trying to save you that effort but it seems you want to go your own way.

---

### Post by CoolStoryBro on 2011-04-26
I was modifying so many files that I thought it would be best to get a clean install. Nothing was lost. Anyways I did what you said and deleted that folder, as well as doing the steps you gave me in the first page. 

Grub is back :guitar:

Thanks for your help and patience Quackers. I owe you one. Now to put Windows on the top of grub.

Thanks again dude

---

