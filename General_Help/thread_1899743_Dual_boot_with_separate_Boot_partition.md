---
title: "Dual boot with separate Boot partition"
date: 2011-12-24
forum: General Help
---

### Post by tommihl on 2011-12-24
Hello,

Installed Ubuntu with Windows 7. I made a separate partition for boot and pointed Ubuntu installation to there. Then tried to boot but Grub recovery console opened.. Then installed Windows 7 bootloader back. So what I'm asking is should I try to install Grub with better success or use Windows bootloader to load Ubuntu as well? If not latter, do I have to boot LiveCD and use chroot or something to set up Grub? Thanks!

---

### Post by oldfred on 2011-12-24
Run this script so we can see what is installed where From a liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

If only minor repairs are required this will run script and make some repairs.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

And sometimes this will boot a system that has grub issues so you can repair from inside the install without having to chroot.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by fantab on 2011-12-24
> **tommihl said:**
> Hello,

Installed Ubuntu with Windows 7. **I made a separate partition for boot and pointed Ubuntu installation to there.** Then tried to boot but Grub recovery console opened.. Then installed Windows 7 bootloader back. So what I'm asking is should I try to install Grub with better success or use Windows bootloader to load Ubuntu as well? If not latter, do I have to boot LiveCD and use chroot or something to set up Grub? Thanks!

GRUB should be installed only on the Hard Disk (**/dev/sda**) and NOT the partitions like /dev/sda1 or /dev/sda4, etc. 

*"I made a separate partition for boot and pointed Ubuntu installation to there"*. This is confusing. Are you talking about " / " or " /boot " partition? If you are not sure of the answer post the output of the BOOT INFO SCRIPT as requested by post above.

---

### Post by tommihl on 2011-12-26
> **fantab said:**
> GRUB should be installed only on the Hard Disk (**/dev/sda**) and NOT the partitions like /dev/sda1 or /dev/sda4, etc. 

*"I made a separate partition for boot and pointed Ubuntu installation to there"*. This is confusing. Are you talking about " / " or " /boot " partition? If you are not sure of the answer post the output of the BOOT INFO SCRIPT as requested by post above.

Sorry. There's partitions for Home, /, and Boot.

---

### Post by tommihl on 2011-12-26
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb.
 => Lilo is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       
    Boot sector type:  - (cleared BS by FDISK)
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb4: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *         16,065   488,392,064   488,376,000   f W95 Extended (LBA)
/dev/sda5              16,128   488,392,064   488,375,937   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *      1,429,785   411,023,024   409,593,240   7 NTFS / exFAT / HPFS
/dev/sdb2         411,023,025   513,421,334   102,398,310  83 Linux
/dev/sdb3         513,421,335   976,768,064   463,346,730   1 FAT12
/dev/sdb4               2,048     1,429,503     1,427,456  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   586,099,394   586,099,332  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        8CE81662E8164ABA                       ntfs       Varasto 1
/dev/sdb1        398DA0FC5E9BDBA1                       ntfs       WINDOWS
/dev/sdb2        d4d0e342-1027-0000-85bd-806e6f6e6963   ext3       /
/dev/sdb4        0fd8243f-4d9e-4cbb-aec8-fcc59e273941   ext2       Boot
/dev/sdc1        4fc85f57-1027-0000-85bd-806e6f6e6963   ext3       Home

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set=root d4d0e342-1027-0000-85bd-806e6f6e6963
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos2)'
  search --no-floppy --fs-uuid --set=root d4d0e342-1027-0000-85bd-806e6f6e6963
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
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
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root d4d0e342-1027-0000-85bd-806e6f6e6963
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=d4d0e342-1027-0000-85bd-806e6f6e6963 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root d4d0e342-1027-0000-85bd-806e6f6e6963
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=d4d0e342-1027-0000-85bd-806e6f6e6963 ro recovery nomodeset 
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
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root d4d0e342-1027-0000-85bd-806e6f6e6963
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root d4d0e342-1027-0000-85bd-806e6f6e6963
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 398DA0FC5E9BDBA1
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
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=d4d0e342-1027-0000-85bd-806e6f6e6963 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdc1 during installation
UUID=4fc85f57-1027-0000-85bd-806e6f6e6963 /home           ext3    defaults        0       2
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 237.061523914 = 254.542873088  boot/grub/core.img                             1
 237.038017750 = 254.517633536  boot/grub/grub.cfg                             1
 236.964809895 = 254.439027200  boot/initrd.img-3.0.0-12-generic               5
 236.979778767 = 254.455099904  boot/vmlinuz-3.0.0-12-generic                  3
 236.964809895 = 254.439027200  initrd.img                                     5
 236.979778767 = 254.455099904  vmlinuz                                        3

=================== sdb4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.165191650 = 0.177373184    boot/grub/core.img                             2



```

---

### Post by tommihl on 2011-12-26
So what does your trained eyes see

---

### Post by oldfred on 2011-12-26
If you created a separate /boot it is not being used. Your full install is in sdb2. But grub in the MBR of sda is trying to boot from partition 7 (it may not be partition 7 on sda). 

I think you can just reinstall grub to sda.

#confirm that linux is sdb2
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Change BIOS or use one time boot key (f12 on mine) to boot from sda.
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

I actually do not recommend separate /boot for most desktops. Servers with RAID or LVM and some old computers that have to boot from inside the first 137GB may need the /boot partition, but not always even then.

Your sda has just an extended partition with one NTFS partition inside it which is a bit unusual. And you have a FAT12? partition sdb3 which looks like it may have some issues.

With multiple drives, I prefer to have each operating system on separate drives with its boot loader in the MBR of that same drive. That way if one drive has issues you can change BIOS or use one time boot key to boot other drive.

---

### Post by tommihl on 2011-12-29
> **oldfred said:**
> If you created a separate /boot it is not being used. Your full install is in sdb2. But grub in the MBR of sda is trying to boot from partition 7 (it may not be partition 7 on sda). 

I think you can just reinstall grub to sda.

#confirm that linux is sdb2
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Change BIOS or use one time boot key (f12 on mine) to boot from sda.
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

I actually do not recommend separate /boot for most desktops. Servers with RAID or LVM and some old computers that have to boot from inside the first 137GB may need the /boot partition, but not always even then.

Your sda has just an extended partition with one NTFS partition inside it which is a bit unusual. And you have a FAT12? partition sdb3 which looks like it may have some issues.

With multiple drives, I prefer to have each operating system on separate drives with its boot loader in the MBR of that same drive. That way if one drive has issues you can change BIOS or use one time boot key to boot other drive.

Thanks this helped! Hopefully some day VirtualBox is so good that I don't need a dual boot anymore :) That FAT12 is just an erased partition...

---

### Post by oldfred on 2011-12-29
Glad you got it working.:)

---

