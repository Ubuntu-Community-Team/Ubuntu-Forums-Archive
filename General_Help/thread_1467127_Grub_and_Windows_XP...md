---
title: "Grub and Windows XP..??"
date: 2010-04-30
forum: General Help
---

### Post by robertcoulson on 2010-04-30
Hi..Installed Ubuntu 10.04 and the Grub program comes up and I see XP, but when I click it, it just returns to the Grub display...???
Can anyone help...Robert

---

### Post by CampbellBoyd on 2010-04-30
Same (or very similar) problem. I can access the drive with XP on it and read files from it but if I select the XP option in the Grub menu the PC goes back to the original boot screen (instead of the windows loading screen) then back to Grub. The ununtu option in Grub works fine.

regards 

Campbell
(I'm nearly away from XP but just need back to run MS programs and export some data.)

---

### Post by robertcoulson on 2010-04-30
Ya...Maybe I should have stayed with 9.10...I am either going to reinstall 9.10 (fresh install) or ISO to Disc install...Hope it works.
Robert

---

### Post by bcbc on 2010-04-30
See here for fix: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by robertcoulson on 2010-04-30
Would a fresh install from 9.10 or 10.04 fix my grub problem...???
Robert

---

### Post by bcbc on 2010-04-30
> **robertcoulson said:**
> Would a fresh install from 9.10 or 10.04 fix my grub problem...???
Robert
No. Grub2 overwrote your windows boot sector. You need to repair it to get windows running.

---

### Post by CampbellBoyd on 2010-04-30
> **bcbc said:**
> See here for fix: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I've followed the instructions in the link and the contents of the results file are pasted below:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 159284314 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 159284314 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 159284314 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5 and 
                       looks at sector 159284314 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   234,372,284   234,275,895   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         159,011,370   234,436,544    75,425,175  83 Linux
/dev/sdb2    *         16,065   159,011,369   158,995,305   5 Extended
/dev/sdb5              16,128   155,685,914   155,669,787   7 HPFS/NTFS
/dev/sdb6         155,685,978   159,011,369     3,325,392  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D3-0A11                              vfat       DellUtility                   
/dev/sda2        36A0267BA02641AB                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        42af23c5-2c6e-474f-acfc-ae260e2a7afe   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        A2B5CE7F94558B51                       ntfs       EDRIVE                        
/dev/sdb6        bd147741-cc93-45f4-b892-7d2462c21c0f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=campbell)
/dev/sda2        /media/36A0267BA02641AB  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 42af23c5-2c6e-474f-acfc-ae260e2a7afe
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 42af23c5-2c6e-474f-acfc-ae260e2a7afe
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 42af23c5-2c6e-474f-acfc-ae260e2a7afe
    linux    /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=42af23c5-2c6e-474f-acfc-ae260e2a7afe ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 42af23c5-2c6e-474f-acfc-ae260e2a7afe
    echo    'Loading Linux 2.6.32-21-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=42af23c5-2c6e-474f-acfc-ae260e2a7afe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 42af23c5-2c6e-474f-acfc-ae260e2a7afe
    linux    /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=42af23c5-2c6e-474f-acfc-ae260e2a7afe ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 42af23c5-2c6e-474f-acfc-ae260e2a7afe
    echo    'Loading Linux 2.6.31-21-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=42af23c5-2c6e-474f-acfc-ae260e2a7afe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 42af23c5-2c6e-474f-acfc-ae260e2a7afe
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 42af23c5-2c6e-474f-acfc-ae260e2a7afe
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 36a0267ba02641ab
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=42af23c5-2c6e-474f-acfc-ae260e2a7afe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=bd147741-cc93-45f4-b892-7d2462c21c0f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  81.5GB: boot/grub/core.img
  84.2GB: boot/grub/grub.cfg
  91.9GB: boot/initrd.img-2.6.31-21-generic-pae
  92.0GB: boot/initrd.img-2.6.32-21-generic-pae
  82.0GB: boot/vmlinuz-2.6.31-21-generic-pae
  91.8GB: boot/vmlinuz-2.6.32-21-generic-pae
  92.0GB: initrd.img
  91.9GB: initrd.img.old
  91.8GB: vmlinuz
  82.0GB: vmlinuz.old

```

---

### Post by bcbc on 2010-04-30
> **CampbellBoyd said:**
> I've followed the instructions in the link and the contents of the results file are pasted below:


So you do have the problem (installed grub to the windows partition boot sector) - have you tried the solution posted on that link?

---

### Post by robertcoulson on 2010-04-30
Hey BCBC....I tried your link and WOW, I have Windows XP back...Thank you very, very much...My 10.04 is still screwy...Can I now reinstall 10.04 since I believe I am now running GRUB2...Without screwing up XP again...??
Robert

---

### Post by bcbc on 2010-04-30
> **robertcoulson said:**
> Hey BCBC....I tried your link and WOW, I have Windows XP back...Thank you very, very much...My 10.04 is still screwy...Can I now reinstall 10.04 since I believe I am now running GRUB2...Without screwing up XP again...??
Robert

Great news!

Yes reinstall 10.04 by all means, but when it asks you where to install grub2 make sure you do not select any partition.
i.e.
/dev/sda  OK
/dev/sda1 NOT OK

You will want to install it to the MBR of the disk that boots first (if you have more than one) - generally, that will be /dev/sda

---

### Post by robertcoulson on 2010-04-30
Is that the point where it asks you (sorry I am stupid) to use the largest free space(not where windows is located).
Robert

---

### Post by robertcoulson on 2010-04-30
Sorry BCBC...I only have ONE hard drive that is partitioned...
Robert

---

### Post by bcbc on 2010-04-30
> **robertcoulson said:**
> Sorry BCBC...I only have ONE hard drive that is partitioned...
Robert

Ok so you install grub to /dev/sda

Your disk should already have the ubuntu partition and swap, so select the manual option and tell it where to install.

---

### Post by robertcoulson on 2010-04-30
Yes....Correct, so I can reinstall it OVER the existing Ubuntu partition, correct...???
Robert

---

### Post by bcbc on 2010-04-30
Hold on... you didn't say what was wrong with Ubuntu 10.04. When you say it is 'screwy' what exactly do you mean?

---

### Post by robertcoulson on 2010-04-30
Well BCBC..I could not use the Minimize bar top right hand corner and my mouse was an "X" and not a pointer, BUT just fixed that....so, everything may be OK now...Thanks for the great help, will NOT reinstall for now.
Thanks again..Robert

---

### Post by davexnet on 2010-04-30
I installed grub in the linux partition and maintained the Windows
MBR and Vista boot loader.  I then added Ubuntu as an option in my Vista
boot screen.

I must admit as a linux newbie, I was nervous of allowing Grub to take over
the MBR.

I've since done dist upgrades, and the boot environment has continued to
work without any further modification.

---

### Post by bcbc on 2010-04-30
The minimize bar has moved - by default - to the left. You can change that if you want.

Anyway - great that it's working again. And I agree - don't reinstall unless necessary.

---

### Post by robertcoulson on 2010-04-30
That's funny...Mine are on the right...Weird.
Robert

---

### Post by robertcoulson on 2010-04-30
davexnet  Know what you mean....scary as heck, isn't it.
Robert

---

### Post by CampbellBoyd on 2010-04-30
> **bcbc said:**
> So you do have the problem (installed grub to the windows partition boot sector) - have you tried the solution posted on that link?

Sorry bcbc, like a real idiot I got confused in the links. I have now re-followed and carried out the instructions which worked perfectly. Everything is now as it should be.

Many thanks

---

### Post by bcbc on 2010-04-30
> **CampbellBoyd said:**
> Sorry bcbc, like a real idiot I got confused in the links. I have now re-followed and carried out the instructions which worked perfectly. Everything is now as it should be.

Many thanks
Great! You're welcome.

---

