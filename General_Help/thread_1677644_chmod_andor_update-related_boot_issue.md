---
title: "chmod and/or update-related boot issue?"
date: 2011-01-29
forum: General Help
---

### Post by tardis.42 on 2011-01-29
Hi everyone,

So, I've had my share of troubles with Ubuntu before and always been able to find help just by reading the forums, but this time it doesn't seem to be happening.  Basically, I think I did something stupid by trying to change the permissions on my home folder to 777.  (I'm the only person who uses my computer and got sick of always having to get root permissions.)  Halfway through the process, the computer slowed to a crawl and text in dialog boxes started getting replaced with empty squares.

Naturally I rebooted &#8211; or tried to.  Regular boot didn't work, so I tried recovery mode, which was kind enough to tell me I had a kernel panic because sbin/init wasn't found.  Here's where things got weird: I then tried to boot from my Ubuntu USB stick, and couldn't.  I got to the USB menu, hit the "run" option, and after a few seconds of the Ubuntu boot screen, my monitor went blank.  Actually, to be technical, it didn't just show a black screen &#8211; the screen shut off.  That's as far as I've been able to get.

By the way, just before I tried what I'm now calling the chmod-of-death, I also had an update freeze in the middle.

I am able to boot into Windows, and have checked my USB stick &#8211; all seems fine.  Any thoughts on this?  Worst case, I can reformat the partition and reinstall, but I'd rather not lose all that data.

Thanks!!

UPDATE: Okay, so I *did* manage, after about ten more tries, to boot from the USB stick.  I went in from there and changed all the permissions back to 755.  Tried to boot in recovery again, and still getting the same sbin/init error - so I'm wondering now if it had more to do with the failed update than the permission change....

---

### Post by Rubi1200 on 2011-01-29
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by tardis.42 on 2011-01-29
Rubi,

I don't have that option.  When I boot from USB, I get the following menu:

Run Ubuntu from this USB
Install Ubuntu on a Hard Disk
Test memory
Boot from first hard disk
Advanced options
Help

"Advanced options" is empty.

Am I running an old build?  Should I get myself a new live USB stick?

---

### Post by Rubi1200 on 2011-01-29
What version do you have on the USB?

You can try the option to > Run Ubuntu from this USB

---

### Post by tardis.42 on 2011-01-29
That was actually what I did.  I was able to download and run the script.  Here are the results:

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => HP/Gateway is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048   625,139,711   600,561,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,046     4,882,431     4,880,386   5 Extended
/dev/sdb5               2,048     4,882,431     4,880,384  82 Linux swap / Solaris
/dev/sdb2         378,009,600   488,396,799   110,387,200  83 Linux
/dev/sdb3           4,883,760   378,009,449   373,125,690   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1021 MB, 1021312512 bytes
129 heads, 16 sectors/track, 966 cylinders, total 1994751 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             16     1,994,750     1,994,735   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2CC6D5BDC6D5878A                       ntfs       PQSERVICE                     
/dev/sda2        16CCF676CCF64F8B                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        acef62c3-2e65-4454-a842-92d1ced56365   ext4                                     
/dev/sdb3        13DE0ADF3133BA0B                       ntfs       Data                          
/dev/sdb5                                               swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3A85-9A8B                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat        (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /media/U3 System         iso9660     (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set default="5"
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set acef62c3-2e65-4454-a842-92d1ced56365
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set acef62c3-2e65-4454-a842-92d1ced56365
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set acef62c3-2e65-4454-a842-92d1ced56365
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=acef62c3-2e65-4454-a842-92d1ced56365 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set acef62c3-2e65-4454-a842-92d1ced56365
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=acef62c3-2e65-4454-a842-92d1ced56365 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set acef62c3-2e65-4454-a842-92d1ced56365
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set acef62c3-2e65-4454-a842-92d1ced56365
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2cc6d5bdc6d5878a
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 16ccf676ccf64f8b
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb2       /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/sdc1       /media/         ntfs    defaults,umask=000,uid=1000,gid=1000,noatime 0 0
/dev/sda2       /C/             ntfs    defaults,umask=000,uid=1000,gid=1000,noatime 0 0

=================== sdb2: Location of files loaded by Grub: ===================


 247.3GB: boot/grub/core.img
 247.4GB: boot/grub/grub.cfg
 201.3GB: boot/initrd.img-2.6.32-25-generic
 247.5GB: boot/vmlinuz-2.6.32-25-generic
 201.3GB: initrd.img
 247.5GB: vmlinuz
```

---

### Post by tardis.42 on 2011-01-29
Update (sorry for the double post):

I tried once more to boot into recovery mode and got a picture of the error messages I'm receiving so I could post them.  Here's what I'm looking at:

```
[   12.341223] Kernel panic - not syncing: Attempted to kill init!
[   12.341397] Pid: 1, comm: run-init Not tainted 2.6.32-25-generic #45-Ubuntu
[   12.341582] Call trace:
[   12.341676]  [<ffffffff81540a6d>] panic+0x78/0x137
[   12.341815]  [<ffffffff81144a49>] ? __fput+0x199/0x210
[   12.341961]  [<ffffffff81068b8d>] forget_original_parent+0x30d/0x320
[   12.342134]  [<ffffffff81067fc4>] ? put_files_struct+0xc4/0xf0
[   12.342296]  [<ffffffff81068bbb>] exit_notify+0x1b/0x1b0
[   12.342446]  [<ffffffff8106a5f0>] do_exit+0x1b0/0x380
```

I found a reference to similar error codes [here]("http://ubuntuforums.org/showthread.php?t=1347696"), but that person eventually figured out that he had somehow accidentally run a script that deleted /lib, and my /lib is definitely intact.

---

### Post by tardis.42 on 2011-01-30
SOLVED!

Thanks for the help, but I have it fixed!

One of the searches I did for those error codes turned up something about a failed upgrade, so I came at it from that angle.  Here's what I did to fix the problem, in case anyone's in a similar boat in the future:

Booted from live USB
Opened terminal
sudo su
Mounted my Ubuntu partition as /media/sys_root
chroot /media/sys_root
Hit a bunch of error messages telling me "/bin/bash permission denied".  Ironically, the only way past this was to do the chmod I *thought* had been my mistake when all this started: chmod 777 /media/sys_root.  Tried chroot again, worked.
apt-get update
apt-get upgrade

130 packages updated, and my system is back to booting normally.

NOTE: chmoding your whole file system to 777 WILL screw up your ability to sudo.  I had to use recovery mode to chmod etc/sudoers.d/ and all files therein back to 0440 and chown it to root.root.

---

### Post by Rubi1200 on 2011-01-30
Excellent! Glad you got it sorted out :-)

---

