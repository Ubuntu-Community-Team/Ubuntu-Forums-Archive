---
title: "grub rescue error"
date: 2010-12-05
forum: General Help
---

### Post by sks06c on 2010-12-05
I recently installed Ubuntu, and after downloading updates and restarting I was given a grub rescue error screen. I can't boot into either Windows or Ubuntu, and I tried making a bootable USB to reinstall Ubuntu but that isn't working either. The only thing I see after turning the power on is:

error: no such device: b4208f23-d31c-4fbd-b907-eacb63fc162b.
grub rescue>

Any suggestions for what to do here?

---

### Post by Sidewinder1 on 2010-12-05
Not sure that this will help but you could try the following:
Boot to Live CD.
Open a terminal and type:
```
update grub
```
It won't hurt anything and might be worth a shot.
HTH,
Side

---

### Post by sks06c on 2010-12-05
> **Sidewinder1 said:**
> Not sure that this will help but you could try the following:
Boot to Live CD.
Open a terminal and type:
```
update grub
```It won't hurt anything and might be worth a shot.
HTH,
Side
I made a boot USB and changed the boot order priority, but it still only boots to the grub rescue error screen.

---

### Post by wilee-nilee on 2010-12-05
There is a per-session boot from a boot from menu a key prompt is needed mine is f12, yours may be different could be esc. You use this key prompt as soon as you power on if you get to the live thumb/cd environment do this. You use this like you did when you accessed the bios.
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by sks06c on 2010-12-05
> **wilee-nilee said:**
> There is a per-session boot from a boot from menu a key prompt is needed mine is f12, yours may be different could be esc. You use this key prompt as soon as you power on if you get to the live thumb/cd environment do this. You use this like you did when you accessed the bios.
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.
I tried hitting all the F# keys and Esc on startup, but the only menu I got to was the BIOS menu.

---

### Post by wilee-nilee on 2010-12-05
> **sks06c said:**
> I tried hitting all the F# keys and Esc on startup, but the only menu I got to was the BIOS menu.

What is the exact computer model?

---

### Post by sks06c on 2010-12-05
> **wilee-nilee said:**
> What is the exact computer model?
Asus Eee 1215N

---

### Post by wilee-nilee on 2010-12-05
> **sks06c said:**
> Asus Eee 1215N

Take a look at this link.
[http://vip.asus.com/forum/view.aspx?id=20081216190623424&board_id=20&model=Eee+PC+901%2FLinux&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20081216190623424&board_id=20&model=Eee+PC+901%2FLinux&page=1&SLanguage=en-us)

---

### Post by sks06c on 2010-12-05
> **wilee-nilee said:**
> Take a look at this link.
[http://vip.asus.com/forum/view.aspx?id=20081216190623424&board_id=20&model=Eee+PC+901%2FLinux&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20081216190623424&board_id=20&model=Eee+PC+901%2FLinux&page=1&SLanguage=en-us)
I was able to boot from a USB and reinstall Ubuntu. However, now I messed around with some partition stuff and I'm getting a different GRUB error.

error: no such partition.
grub rescue> 

I tried reinstalling Ubuntu again but it just leads me back into this problem.

---

### Post by drs305 on 2010-12-05
Would you please boot the LiveCD and run the boot info script from the following site. Post the contents of RESULTS.txt here, between 'code' tags, which you create by pressing the post's # icon in the menubar.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by sks06c on 2010-12-05
> **drs305 said:**
> Would you please boot the LiveCD and run the boot info script from the following site. Post the contents of RESULTS.txt here, between 'code' tags, which you create by pressing the post's # icon in the menubar.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)
I'm having some trouble running the script. I can go to the site and download the file, but I'm using the netbook edition of Ubuntu and I don't see a way to access the terminal.

---

### Post by wilee-nilee on 2010-12-05
> **sks06c said:**
> I'm having some trouble running the script. I can go to the site and download the file, but I'm using the netbook edition of Ubuntu and I don't see a way to access the terminal.

crtl-alt-t held down in that order should bring up a terminal.

---

### Post by sks06c on 2010-12-06
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 230257072 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   204,802,047   204,800,000   7 HPFS/NTFS
/dev/sda2         204,802,048   241,172,479    36,370,432  83 Linux
/dev/sda3         241,183,906   488,343,869   247,159,964   f W95 Ext d (LBA)
/dev/sda5         241,183,908   488,343,869   247,159,962  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8015 MB, 8015282176 bytes
32 heads, 63 sectors/track, 7765 cylinders, total 15654848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,654,239    15,654,177   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        383AEBD23AEB8B68                       ntfs                                     
/dev/sda2        78adbc16-f42f-484f-842d-9833cd582403   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        b999424b-7053-4994-8e35-e959728cd778   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9C26-456E                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 78adbc16-f42f-484f-842d-9833cd582403
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 78adbc16-f42f-484f-842d-9833cd582403
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 78adbc16-f42f-484f-842d-9833cd582403
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=78adbc16-f42f-484f-842d-9833cd582403 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 78adbc16-f42f-484f-842d-9833cd582403
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=78adbc16-f42f-484f-842d-9833cd582403 ro single 
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 78adbc16-f42f-484f-842d-9833cd582403
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 78adbc16-f42f-484f-842d-9833cd582403
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 383aebd23aeb8b68
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=78adbc16-f42f-484f-842d-9833cd582403 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b999424b-7053-4994-8e35-e959728cd778 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 117.8GB: boot/grub/core.img
 107.4GB: boot/grub/grub.cfg
 105.5GB: boot/initrd.img-2.6.35-22-generic
 105.2GB: boot/vmlinuz-2.6.35-22-generic
 105.5GB: initrd.img
 105.2GB: vmlinuz
```

---

### Post by sks06c on 2010-12-06
I don't know what's wrong with the partitions, but I'd like to dual-boot Windows 7 and Ubuntu and have them both read files from a shared hard drive.

---

### Post by wilee-nilee on 2010-12-06
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    **partition #7 **for (,msdos7)/boot/grub.

You have no sda7 boot the live thumb and run these commands, in the terminal of the Live cd/thumb environment.

```
sudo mount /dev/sda2 /mnt
```

then

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot to the grub menu choose the installed Ubuntu and run this command in the terminal in the installed Ubuntu
```
sudo update-grub
```

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                      ** /wubildr.mbr /wubildr**

This probably wont be a problem as it is just the remnants of a wubi install but clean them out if everything gets up and running.

---

### Post by sks06c on 2010-12-06
> **wilee-nilee said:**
> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    **partition #7 **for (,msdos7)/boot/grub.

You have no sda7 boot the live thumb and run these commands, in the terminal of the Live cd/thumb environment.

```
sudo mount /dev/sda2 /mnt
```then

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```Reboot to the grub menu choose the installed Ubuntu and run this command in the terminal in the installed Ubuntu
```
sudo update-grub
```sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                      ** /wubildr.mbr /wubildr**

This probably wont be a problem as it is just the remnants of a wubi install but clean them out if everything gets up and running.
Thank you so much! I was able to boot into Linux and update GRUB. I'm installing updates and rebooting now, but that should fix everything. How do I delete the wubi remnants?

---

### Post by wilee-nilee on 2010-12-06
> **sks06c said:**
> Thank you so much! I was able to boot into Linux and update GRUB. I'm installing updates and rebooting now, but that should fix everything. How do I delete the wubi remnants?

When you had wubi there was a file that held all the wubi stuff look for it I guess, probably called Ubuntu, that is one I'm not real familiar with. If you are able to boot into windows which from the script it looks fine, it is just a clean up thing really.

Hey and now you know the per-session prompt that keeps you from ever having to go to the bios and change the boot order it can just be boot what you want from the key prompt. Most people know nothing about this post bios boot from prompt.

---

### Post by sks06c on 2010-12-06
> **wilee-nilee said:**
> When you had wubi there was a file that held all the wubi stuff look for it I guess, probably called Ubuntu, that is one I'm not real familiar with. If you are able to boot into windows which from the script it looks fine, it is just a clean up thing really.

Hey and now you know the per-session prompt that keeps you from ever having to go to the bios and change the boot order it can just be boot what you want from the key prompt. Most people know nothing about this post bios boot from prompt.
That is pretty nifty! Should I look for the wubi files in Windows? I know I have the wubi installer on my desktop, not sure about anything else.

---

### Post by wilee-nilee on 2010-12-06
> **sks06c said:**
> That is pretty nifty! Should I look for the wubi files in Windows? I know I have the wubi installer on my desktop, not sure about anything else.

As you see I got that wubi information from the bootscript. It may just be that icon on the desktop, remove it boot into Ubuntu and run the script and look at the sda1 line and see if the wubi is gone from there.

I suspect it is the icon, but wubi is just out of my area of general knowledge. The original wubi install was in a Ubuntu folder I would look for that if the wubi still showing sda1 after removing the icon off the desktop.

Your out of danger I think even if it shows in the sda1 line, as it is just part of the dual boot MS bootscreen that gave you a choice of Windows or Ubuntu.

Personally I'm a little retentive with my setups, without ever being diagnosed with any thing other then all to average in all departments.;) Its nice being average lots of friends in that department.:popcorn:

---

### Post by drs305 on 2010-12-06
A Wubi install is normally removed via Windows Control Panel, Add Remove section. You just remove Ubuntu. If it's not there or broken, the two places I'm familiar with are the c:\ubuntu folder, which you can delete, and the c:\boot.ini file (if that is what your version of Windows uses). You can edit it with notepad and remove the line that references wubildr.

---

### Post by sks06c on 2010-12-06
> **drs305 said:**
> A Wubi install is normally removed via Windows Control Panel, Add Remove section. You just remove Ubuntu. If it's not there or broken, the two places I'm familiar with are the c:\ubuntu folder, which you can delete, and the c:\boot.ini file (if that is what your version of Windows uses). You can edit it with notepad and remove the line that references wubildr.

When I try to remove it through the Control Panel I get this error: An error occurred while trying to uninstall Ubuntu. You do not have access to D:\ubuntu\uninstall-wubi.exe

Also, the D: drive is not visible in the hard disks section of Windows. I can see it in the disk management section, and it doesn't have a file system label. How can I make it so that Windows and Ubuntu both share a D: drive?

---

### Post by wilee-nilee on 2010-12-07
> **sks06c said:**
> When I try to remove it through the Control Panel I get this error: An error occurred while trying to uninstall Ubuntu. You do not have access to D:\ubuntu\uninstall-wubi.exe

Also, the D: drive is not visible in the hard disks section of Windows. I can see it in the disk management section, and it doesn't have a file system label. How can I make it so that Windows and Ubuntu both share a D: drive?

Look at the disk manager and see what type of partition D is it should be a NTFS, but may not be showing as it may need a chkdsk run. A NTFS should show in the computer area in admin and in Ubuntu in the left sidebar of home.

As drs305 suggested I believe you really are best to delete and modify a MS set up even wubi in the MS environment.

You can get to the disk manager in admin in windows 7 by starting in the start-search bar just start to type disk ma, and you will see a partitioner show up in the panel as it is looking for matches.

You can also confirm the D partition type from gparted in Ubuntu, which you may have to install. 

```
sudo apt-get install gparted
```
in the Ubuntu terminal, you can also right click that D partition in gparted if it shows; then information for clues on maybe what is needed.

You have to be in the admin account in W7 to delete the wubi stuff as well.

---

### Post by sks06c on 2010-12-07
I don't see any wubi files in either Windows or Ubuntu. I downloaded gparted and can see the file systems my drives are set to. Windows is installed on an NTFS drive, Ubuntu on ext4, then I have an extended/linux swap drive that's over 100GB, and two small unallocated drives that are under 1GB each. Can I safely use gparted to make the large drive into an NTFS drive?

---

### Post by wilee-nilee on 2010-12-07
> **sks06c said:**
> I don't see any wubi files in either Windows or Ubuntu. I downloaded gparted and can see the file systems my drives are set to. Windows is installed on an NTFS drive, Ubuntu on ext4, then I have an extended/linux swap drive that's over 100GB, and two small unallocated drives that are under 1GB each. Can I safely use gparted to make the large drive into an NTFS drive?

I'm not sure I understand, can you post a screenshot of gparted.

---

### Post by sks06c on 2010-12-07
Here's a screenshot. I'm not sure what the keys next to some of the drives mean.

---

### Post by wilee-nilee on 2010-12-07
I think that the sda5 named swap beats the record for the biggest one I have seen. The swap is where the memory=ram and a few other things go when you hibernate or sleep the OS, so it should only be at the most twice the size of your ram.

So yes you can delete sda5 make another swap of the correct size and make the unallocated to a shared ntfs which would probably show as D in windows. As it is you have no D. When you got to remove sda5 since it is the swap right click on it to turn it off first, this is very important so if you can't turn it off repost. Since that swap is inside a extended it is noteworthy to know that you can fit as many types of partitions you want in there.

The keys you see are because your using the installed Ubuntu, you really need to boot a live usb and use that gparted to be totally safe.

---

