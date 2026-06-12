---
title: "Dual-booting with Windows 7 - Windows Boot Fails"
date: 2011-10-11
forum: General Help
---

### Post by cfisher14 on 2011-10-11
Last night I installed Ubuntu on my 250g hdd and allocated a 50g swap partition. Previously, I was unable to get the CD to install Ubuntu because of some issue with the BIOS being set to "IDE" for my sata hdd's so I had to set it to "AHCI" instead. After that, it worked perfectly fine! It installed Ubuntu and I was happy! Then, It restarted and it went to "grub rescue" and I had to go back into the live CD and install grub this way (I used google to find this method)... I have a bit of linux knowledge but not a whole lot

sudo fdisk -l[INDENT]disk /dev/sda: 250.1 GB
(bunch of mumbo jumbo)

Device           Start               End        Id        System
/dev/sda1             1            6079        82         Linux Swap / Solaris
/dev/sda2       6079          30402          5         Extended
/dev/sda5       6079          30402        83         Linux

Disk /dev/sdb: 500.1 GB
(bunch of mumbo jumbo)     

Device       Boot         Start          End        Id          System
/dev/sdb1       *                1       60802         7          HPFS/NTFS               
[/INDENT]sudo mkdir /media/sda5 
sudo mount /dev/sda5 /media/sda5
sudo grub-install --root-directory=/media/sda5 /dev/sda


After I did that, grub bootloader came up and I was happy again! Then I tried to boot into my Windows 7 and it gets to the loading screen with the fancy swirls and what not, then quickly flashes a blue screen (tried to pause it but I could not) and restarts the computer.

Any idea of what I did to break it? And any possible ways to fix it? 

Thank you!

---

### Post by Quackers on 2011-10-11
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

OR alternatively see here

[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

---

### Post by cfisher14 on 2011-10-11
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    97,656,831    97,654,784  82 Linux swap / Solaris
/dev/sda2          97,658,878   488,396,799   390,737,922   5 Extended
/dev/sda5          97,658,880   488,396,799   390,737,920  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   976,771,071   976,769,024   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 ebd92774-fcd2-42f0-a32e-f2733756e4e8   swap       
/dev/sda5        5d18dd5f-ecc7-47ef-b360-d2a689c5f30a   ext4       
/dev/sdb1        1458F8E058F8C212                       ntfs       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 5d18dd5f-ecc7-47ef-b360-d2a689c5f30a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 5d18dd5f-ecc7-47ef-b360-d2a689c5f30a
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 5d18dd5f-ecc7-47ef-b360-d2a689c5f30a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5d18dd5f-ecc7-47ef-b360-d2a689c5f30a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 5d18dd5f-ecc7-47ef-b360-d2a689c5f30a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5d18dd5f-ecc7-47ef-b360-d2a689c5f30a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 5d18dd5f-ecc7-47ef-b360-d2a689c5f30a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 5d18dd5f-ecc7-47ef-b360-d2a689c5f30a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 1458F8E058F8C212
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
#UUID=1e976804-98c0-4022-afe9-509c8c5060e9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 164.706733704 = 176.852508672  boot/grub/core.img                             1
  76.747390747 = 82.406883328   boot/grub/grub.cfg                             1
  48.248966217 = 51.806932992   boot/initrd.img-2.6.38-8-generic               1
 164.700199127 = 176.845492224  boot/vmlinuz-2.6.38-8-generic                  1
  48.248966217 = 51.806932992   initrd.img                                     1
 164.700199127 = 176.845492224  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```

---

### Post by oldfred on 2011-10-12
Windows is on a separate drive, so it should not have been changed with the install of Ubuntu. Was it originally booting from sda? You do have all the boot files in the sdb1 partition.

I would install lilo or the windows boot loader to the MBR and try directly booting Windows by using one time boot key (f12 on my system) to boot sdb. Yoiu may also need to use f8 to get to a Windows repair console. From grub it is difficult to get the  f8 inserted in time as it boots quickly  from grub to Windows. Some have had the f8 work but had to try many times.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

The change from IDE may require some change in Win7. I know my XP does not work at all in AHCI mode. Drivers have to be installed for XP during install, but I think Win7 includes them automatically.

Are you confusing swap with a shared NTFS partition with Windows? Swap is for RAM memory overflow. If you have 4GB of RAM you may never use swap. We ofter recommend 2GB of swap or swap equal to RAM in GiB if you want to hibernate. you really do not want to use swap as it is a lot slower than RAM anyway.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by cfisher14 on 2011-10-12
Just reporting in! After you mentioned that Windows 7 may needed some sort of change to work with AHCI... I switched back to IDE! Don't know why I didn't bother to try that in the first place... but it worked! Ubuntu and Windows 7 are booting up fine! I guess I just assumed I royally screwed something up :D

Thank you both for your help!!!

---

### Post by Quackers on 2011-10-12
Glad you got it working :-)

---

### Post by Mark Phelps on 2011-10-13
Good to see you got it working so easily.

Please use the Thread Tools to mark this thread as SOLVED.

thanks

---

