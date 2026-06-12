---
title: "Duel Boot Ubuntu &amp; Windows Vista"
date: 2010-05-02
forum: General Help
---

### Post by Kidneythief on 2010-05-02
As I am sure many have had this issue. I have installed 10.4 and I cannot boot back into windows vista. I can boot into ubuntu just fine. I have installed Grub and Grub2 both program pick up ubuntu just fine, but they will not even find the windows install. I have tried a few fixes and none seem to have worked. So at this point I am not sure if it is a person PC issue or just the OS itself. I see lots of people are having this issue. Misery love company.

---

### Post by GSF1200S on 2010-05-02
> **Kidneythief said:**
> As I am sure many have had this issue. I have installed 10.4 and I cannot boot back into windows vista. I can boot into ubuntu just fine. I have installed Grub and Grub2 both program pick up ubuntu just fine, but they will not even find the windows install. I have tried a few fixes and none seem to have worked. So at this point I am not sure if it is a person PC issue or just the OS itself. I see lots of people are having this issue. Misery love company.

First, what is the output from:
```
sudo update-grub
```

Second, download the script from the following URL to your home folder. 
[http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")

Then run:
```
sudo bash boot_info_script055.sh
```

It will create a text file named RESULTS.TXT in your home folder. Please paste the contents of that in a reply to this thread so I can see your layout and help you :)

---

### Post by Kidneythief on 2010-05-02
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin

---

### Post by Kidneythief on 2010-05-02
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/mapper/pdc_ccjfaigbc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

pdc_ccjfaigbc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   732,419,414   732,419,352   7 HPFS/NTFS
/dev/sda2         732,420,096 1,448,355,839   715,935,744  83 Linux
/dev/sda3       1,448,356,140 1,465,144,064    16,787,925  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 1,953,122,303 1,953,120,256   7 HPFS/NTFS


Drive: pdc_ccjfaigbc ___________________ _____________________________________________________

Disk /dev/mapper/pdc_ccjfaigbc: 1000.0 GB, 999999995904 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_ccjfaigbc1              2,048 1,953,122,303 1,953,120,256   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/pdc_ccjfaigbc1 D4E4BAF8E4BADBC4                       ntfs       Storage                       
/dev/mapper/pdc_ccjfaigbc: PTTYPE="dos" 
/dev/sda1        CAD8A7F4D8A7DCC7                       ntfs       Windows Vista                 
/dev/sda2        b4b74fe7-3eab-4a94-980d-4ad90565368a   ext4                                     
/dev/sda3                                               swap                                     
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        8AAED4CAAED4AFC5                       ntfs       Media Storage                 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        D4E4BAF8E4BADBC4                       ntfs       Storage                       
/dev/sdc                                                promise_fasttrack_raid_member                               
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set b4b74fe7-3eab-4a94-980d-4ad90565368a
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set b4b74fe7-3eab-4a94-980d-4ad90565368a
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b4b74fe7-3eab-4a94-980d-4ad90565368a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b4b74fe7-3eab-4a94-980d-4ad90565368a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b4b74fe7-3eab-4a94-980d-4ad90565368a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b4b74fe7-3eab-4a94-980d-4ad90565368a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b4b74fe7-3eab-4a94-980d-4ad90565368a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b4b74fe7-3eab-4a94-980d-4ad90565368a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
UUID=b4b74fe7-3eab-4a94-980d-4ad90565368a /               ext4    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 542.6GB: boot/grub/core.img
 727.3GB: boot/grub/grub.cfg
 542.6GB: boot/initrd.img-2.6.32-21-generic
 641.5GB: boot/vmlinuz-2.6.32-21-generic
 542.6GB: initrd.img
 641.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg

---

### Post by GSF1200S on 2010-05-02
It seems you have multiple hard drives, and im unsure which of them the Windows install you use is on. Do you know if Ubuntu is installed on a different hard drive than windows is? The printout from the boot script suggests windows is installed on the same hard drive, but what concerns me is the:
> sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy


This might be the install you actually want to use, or the install might be on /dev/sda (where the boot script mentions a Windows install, and an Ubuntu 10.04 install.)

Grub2 should automagically pick up all OS's on disks attached to the computer. As an example, I had a laptop harddrive attached via USB that had an old install of Ubuntu 8.04, and grub2 added that to my Grub menu! I noticed you said you installed both versions of Grub, and I think that might be part of the issue. I think you might be invoking Grub1, when Grub2 is what we really want to use. Try running the following in a terminal:
```
sudo apt-get remove grub
sudo apt-get autoremove
sudo apt-get install grub-pc
sudo update-grub2
```
and give me the printout for the last command. Also, please tell me all you know about where windows is installed.

---

### Post by Kidneythief on 2010-05-02
sda1:
File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista

Vista is installed on the first hd on the first partition. its the 750g drive sda.. windows is on sda1 linux sda2 and linux swap sda3

---

### Post by Kidneythief on 2010-05-02
shadow666@shadow:~$ sudo apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-pc is already the newest version.
grub-pc set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shadow666@shadow:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by GSF1200S on 2010-05-02
> **Kidneythief said:**
> shadow666@shadow:~$ sudo apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-pc is already the newest version.
grub-pc set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shadow666@shadow:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

Wow man.. im stumped. Unfortunately I dont have a computer around with the same problem so its kind of hard to help. Doing some searching for a solution, I ran into this thread:
[http://ubuntuforums.org/showthread.php?t=1417950](http://ubuntuforums.org/showthread.php?t=1417950)
Have you seen it yet?

I figured that Windows was on /dev/sda1, but considering that Ubuntu is on the same harddrive and Grub2 is installed to the MBA, you should not be having any issues. Try the solutions in above thread and let me know if something is confusing or what the deal is. Sorry I cant be of more help :(

**EDIT** Perhaps you could restore the MBR using a Windows Installation CD, then boot a live CD, chroot into the partition (ask here if you need help with that) and then try to reconfigure Grub? Just a thought..

---

### Post by Kidneythief on 2010-05-02
Thanks for tying to help but as you can see it kinda weird how this is working out. I think i might try another bootloader at this point. Thanks anyways

---

### Post by itiswhatitis on 2010-05-03
I had the same issue on two computers.  I spent a week or two reading topics here and the grub2 documentation.  It boils down to the Grub2 installation being somewhat ambiguous on what you should do during the upgrade.

There are a couple fixes you can try... I've written a doc that is based on Windows 7 but I am pretty sure Vista is the same (based on the MS Doc I reference).  At the very bottom, there is a link to an alternative solution, which seems to be a popular fix as well.  

I have followed the steps in my doc on two computers w/o issue, however I have not tried the alternative solution.

Here is  my doc..
[http://www.jeffdickman.com/2010/05/ubuntu-10-4-lts-lucid-lynx/](http://www.jeffdickman.com/2010/05/ubuntu-10-4-lts-lucid-lynx/)

And for easy reference, the alternative:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

