---
title: "cant boot XP in grub 2 with weird partitioning"
date: 2011-11-09
forum: General Help
---

### Post by milkboy007 on 2011-11-09
just did a fresh ubuntu 11.10 install on my freinds pc
and the grub2 doest seem to detect WIN XP

his partition is abit weird, look
sda1->logical drive
    sda5 ->xp
sda2 ->ubuntu
sda3 ->swap
sda4 ->just ntfs partition

did "sudo update-grub",reboot , and nothing. not even on grub.cfg

so i tried editing
/etc/grub.d/40_custom

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
[B]menuentry "Windows " {
set root=(hd0,5)
chainloader (hd0,5)+1
}[/B]

#just to be safe, seeng that xp in sda1 logical drive
[B]menuentry "Windows " {
set root=(hd0,1)
chainloader (hd0,1)+1
}[/B]

then run :sudo update-grub
double check grub.cfg, to make sure the entries are there.
reboot

now that i have the menu selection, i tried booth, but stuck at booting after that.

any idea how to fix without deleting the xp partition?
apparently needed for othere stuff

---

### Post by fantab on 2011-11-09
Welcome to the Forum!

Where did you install GRUB?

Also you have XP on /dev/sda5- isn't this equal to** hd0,4**?

If problem persists then post the screenshot of the Partition scheme. and or the output of the following:

```
$sudo blkid
```

---

### Post by oldfred on 2011-11-09
The hd0,4 would be with grub legacy. Grub2  starts count at 1 so sda1 is hd0,1 where in grub legacy it was hd0,0.

Windows does not officially boot from a logical partition. The first install of Windows has to be a primary(active) partition. In fact the Windows definition of active partition is also bootable. A second install of Windows can be in a logical partition but all the boot files are moved to the primary partition. Then if you delete the primary partition with the first install, all the boot files are gone that are needed for the logical.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

But XP can be made to boot with grub from a logical if you have the correct boot files. Or you can create a small FAT primary partition for the boot files. You may also have to repair the boot sector as that has to be a correct NTFS signature.

Post this to see what is where.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Way to boot windows in extended logical partition with lilo's MBR post#5
[http://ubuntuforums.org/showthread.php?t=1367323](http://ubuntuforums.org/showthread.php?t=1367323)
Major windows repair with dual boot and logical partition
[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)
You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)
[http://support.microsoft.com/kb/306559#f1](http://support.microsoft.com/kb/306559#f1)
Create small FAT Primary to boot windows in logical
[http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition](http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition)

---

### Post by milkboy007 on 2011-11-10
heres the result.
i think ur in for a surprise

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1              16,126    94,750,719    94,734,594   f W95 Extended (LBA)
/dev/sda5              16,128    94,750,719    94,734,592   7 NTFS / exFAT / HPFS
/dev/sda2    *     94,750,720   134,750,207    39,999,488  83 Linux
/dev/sda3         134,750,208   142,749,695     7,999,488  82 Linux swap / Solaris
/dev/sda4         142,749,696   312,580,095   169,830,400   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        674fa865-939c-40e6-8f51-42c944119757   ext4       
/dev/sda3        0f8b93d7-e762-4c58-b6d7-05e31d17f820   swap       
/dev/sda4        170363AC2B388FCE                       ntfs       
/dev/sda5        E680DB7B80DB50A3                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 674fa865-939c-40e6-8f51-42c944119757
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 674fa865-939c-40e6-8f51-42c944119757
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 674fa865-939c-40e6-8f51-42c944119757
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=674fa865-939c-40e6-8f51-42c944119757 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 674fa865-939c-40e6-8f51-42c944119757
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=674fa865-939c-40e6-8f51-42c944119757 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 674fa865-939c-40e6-8f51-42c944119757
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 674fa865-939c-40e6-8f51-42c944119757
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "xPUD 0.9.2" {
loopback loop (hd0,2)/xpud-0.9.2.iso
linux(loop)/boot/xpud isofrom=/xpud-0.9.2.iso noisapnp quiet
initrd
(loop)/opt/media 
}
#opt/apps.opt opt/codecs.opt opt/driver.opt opt/ooo.opt opt/skype.opt 
menuentry "Windows xp" {
set root=(hd0,5)
chainloader (hd0,5)+1
}
menuentry "Windows xp" {
set root=(hd0,1)
chainloader (hd0,5)+1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=674fa865-939c-40e6-8f51-42c944119757 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=0f8b93d7-e762-4c58-b6d7-05e31d17f820 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     3
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by milkboy007 on 2011-11-10
DELETED, double post :p

---

### Post by rng on 2011-11-10
sda2 is marked as active (with * sign). I wonder if that is changed to sda5 through gparted in ubuntu, it may work. 

I presume windows was working allright before ubuntu installation.

---

### Post by milkboy007 on 2011-11-10
yup, xp was working fine.
nah it wasnt gparted fault, the partitioning was pretty messed up when i got it.
tried to tidy it up abit, thought that the sda5 is in sda1 logicaldrive wouldnt effect anything.
gueess i was wrong. :p

i have been thinking though, if i 
1. delete linux partition, and 
2. expand the sda1 logiacal drive size, then 
3. then create the necesarry linux partition inside it, then
4. install ubuntu inside it. 

that should solve it. rite?
i mean has anyone tried this?

is not a solution, but a good workaround dun you think
but if you found a simpler way, pls do share.
good documentation stuff, since theres nothing on the net.

i feel that i just thrown out my whole night just to, clean install, update and huge amount of download pakages
all just to get it wipe clean, and repeat T.T

---

### Post by rng on 2011-11-10
Then you are saying that winxp was working while it was in a logical partition and not on primary partition. 

Try making sda5 active through gparted (I think it can be done through fdisk also, but gparted is much easier). It may work. Linux installation may have changed default boot drive to sda2.

---

### Post by oldfred on 2011-11-10
If you want to convert sda5 back to a primary partition, you might be able to (note the might). As with all major system changes be sure to have good backups first.

You will have to delete swap. Later we will recreate swap inside the extended partition as a logical partition. It then will have a new UUID that you will have to update in fstab. You have to delete swap as a primary so you have another primary for Windows.

First backup current partition table, and save to another device.
sudo sfdisk -d /dev/sda > sdaparts.txt

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If you have the available primary, fixparts may let you convert sda5 to a primary since it is at the start of the extended partition. If it was in the middle it would not work.

---

### Post by milkboy007 on 2011-11-10
apparently so, i dindt touch the winxp, just other partition.

when you say making hda5 active using gparted, do mean, like change flag to boot,
mount/unmount it, etcc. cos i ald tried gparted(and fdisk) before this.
and nothing changed. could you elaborate further pls.

any1else wanna try a crack at it.

---

### Post by rng on 2011-11-10
Yes, I think try changing the flag to boot (in gparted- right click on sda5, choose manage flags, select boot- this should automatically remove boot flag from sda2 or do it manually first). Apply changes. It may work.

---

### Post by milkboy007 on 2011-11-11
[COLOR=Black]@ oldfred
thx, ill try rite now
let you guys know in a few moment

[/COLOR]

---

### Post by milkboy007 on 2011-11-11
conversion of logical to primary was successful, but grub still would not detect.
file was intact and accessible.
i thought that it might be winxp's boot.ini file, since sda5 was changed to sda1.
so i edited it, didnt work.
also tried the fixboot. didnt work

my friend is picking his pc up in a few hours.
so i just backup all of his data, did a fresh install for the winxp,
since he said he didnt mind.

thx anyways guys
*much appriciated*

---

### Post by oldfred on 2011-11-11
Whatever works.

For reference, script did not show any of the boot files. If all were there and it was a bootable install, the fixboot & edit of boot.ini should have solved it. Sometimes a chkdsk may also be required.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM

---

### Post by milkboy007 on 2011-11-11
hmm... didnt do chkdsk.
should'ev done that.

any ways the pc is gone, thx again.
learn new stuff, so its a win for me

---

