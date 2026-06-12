---
title: "Can't boot Windows after Grub2 update"
date: 2010-07-21
forum: General Help
---

### Post by term1nus on 2010-07-21
I've been trying on and off to fix this on my own, but I just can't seem to figure it out. I have not been able to load Windows since the Grub2 update several weeks back, and I'll outline what steps I've taken to date so that perhaps we can arrive at a solution.

1. The Windows loader was visible in the menu, but selecting it did nothing whatsoever. I booted back into Linux.

2. I tried the 'update-grub' command from root to fix the issue, but it couldn't find it. I got annoyed.

3. I tried 'repairing' Windows using the original disc, but it could not find a copy of the OS on the partition. I became confused.

4. I ran the command to restore the Windows bootloader to the MBT, but then neither OS would boot up. I became concerned.

5. I reinstalled Grub to the MBT, which at least allowed me to work in Linux. I was somewhat relieved.

6. I looked for my Windows partition, and it was now largely blank. I felt like throwing something.

7. I reinstalled Windows from the original disc and tried booting up only to find that Windows was not in the Grub menu. I got more aggravated.

8. I used the 'update-grub' command once again, this time with success. The Windows loader was now in the menu! I was pleased.

9. I tried booting into Windows - and my system freezes on a black screen after I select it from the Grub menu. Only a hard reboot will clear it. I was at a loss.

10. I used the 'fdisk -l' command to see if Grub had mapped the drive incorrectly. Everything looked fine to me. I decided to seek assistance.

11. I posted this thread. I am hopeful.

Can anyone shed any light on the situation? :(

---

### Post by wilee-nilee on 2010-07-21
Post the bootscript in my signature in code tags as described.

---

### Post by term1nus on 2010-07-21
Here it is.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 244487416 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 244487544 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 244481784 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 244481784 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 244480864 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2    *        129,024   233,963,519   233,834,496   7 HPFS/NTFS
/dev/sda3         233,965,567   488,279,609   254,314,043   f W95 Ext d (LBA)
/dev/sda5         233,965,568   244,203,519    10,237,952   7 HPFS/NTFS
/dev/sda6         244,204,128   478,030,139   233,826,012  83 Linux
/dev/sda7         478,030,203   488,279,609    10,249,407  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       112,454       112,392  de Dell Utility
/dev/sdb2             112,640   488,278,015   488,165,376   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-061D                              vfat       DellUtility                   
/dev/sda2        DEC0F09DC0F07CD9                       ntfs       One                         
/dev/sda3: PTTYPE="dos" 
/dev/sda5        FEBCE0A1BCE05625                       ntfs       Swap                          
/dev/sda6        121376ba-6225-4a76-bc2f-00bd84fcdf4e   ext4                                     
/dev/sda7        36f7923c-6954-4e72-aca4-8826aa2ca48f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        07D4-071C                              vfat       DellUtility                   
/dev/sdb2        249C09419C090F4C                       ntfs       Two                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        32C4647DC46444E7                       ntfs       Three                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/Three             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 121376ba-6225-4a76-bc2f-00bd84fcdf4e
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 121376ba-6225-4a76-bc2f-00bd84fcdf4e
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 121376ba-6225-4a76-bc2f-00bd84fcdf4e
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=121376ba-6225-4a76-bc2f-00bd84fcdf4e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 121376ba-6225-4a76-bc2f-00bd84fcdf4e
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=121376ba-6225-4a76-bc2f-00bd84fcdf4e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 121376ba-6225-4a76-bc2f-00bd84fcdf4e
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=121376ba-6225-4a76-bc2f-00bd84fcdf4e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 121376ba-6225-4a76-bc2f-00bd84fcdf4e
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=121376ba-6225-4a76-bc2f-00bd84fcdf4e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 121376ba-6225-4a76-bc2f-00bd84fcdf4e
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=121376ba-6225-4a76-bc2f-00bd84fcdf4e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 121376ba-6225-4a76-bc2f-00bd84fcdf4e
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=121376ba-6225-4a76-bc2f-00bd84fcdf4e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 121376ba-6225-4a76-bc2f-00bd84fcdf4e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 121376ba-6225-4a76-bc2f-00bd84fcdf4e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07d7-061d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set dec0f09dc0f07cd9
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=121376ba-6225-4a76-bc2f-00bd84fcdf4e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=36f7923c-6954-4e72-aca4-8826aa2ca48f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 125.1GB: boot/grub/core.img
 131.3GB: boot/grub/grub.cfg
 126.6GB: boot/initrd.img-2.6.31-21-generic
 126.4GB: boot/initrd.img-2.6.32-22-generic
 137.5GB: boot/initrd.img-2.6.32-23-generic
 126.2GB: boot/vmlinuz-2.6.31-21-generic
 126.3GB: boot/vmlinuz-2.6.32-22-generic
 125.9GB: boot/vmlinuz-2.6.32-23-generic
 137.5GB: initrd.img
 126.4GB: initrd.img.old
 125.9GB: vmlinuz
 126.3GB: vmlinuz.old

P.S. I very much like this script.

---

### Post by wilee-nilee on 2010-07-21
sda1: __________________________________________________ _______________________

File system: vfat
[B]Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sda1 [/B]and
looks at sector 244487416 of the same hard drive for
core.img, but core.img can not be found at this
location. No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /COMMAND.COM

Now this is the dell firmware junk partition but it does contain some boot files, and even though your sda2 partition is set to boot or active it is probably the main problem. You also have grub in other partitions like, sda5, sdb1, sdb2, sdc1. So to fix the sda1 partition use this link.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

The other partitions can probably be cleaned manually.

The other problem here may be a a dell data safe program here is a link regarding this.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by prodigy_ on 2010-07-21
For some reason you have Grub2 installed on **every** HDD on **every** partition. And everywhere it points to a wrong location.

Like **wilee-nilee** said, you'll need to reinstall Grub2 properly, but keep in mind that you only really need it in the MBR of the HDD you boot from. Having a bootloader installed everywhere only complicates things (unless you know exactly what you're doing).

---

### Post by term1nus on 2010-07-21
wilee_nilee> I tried the testdisk utility, and it seemed to work, somewhat. The primary boot sector now matches, according to the utility anyhow. I'm not sure how to manually remove Grub from the partitions it can't get to, I've never had to deal with a problem like this before. I'll say this, I can't even boot into Windows with the CD now. It stopped progressing after the default background came up. The mouse cursor worked, but it went no further.

prodigy_> Yeah, I noticed that and I can't think of any way that  could have happened. All I did was run the update utility... :/

---

### Post by prodigy_ on 2010-07-21
Well, you could start with recovering MBR/bootsector on your Windows HDD/partition. Read [this HOWTO](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD). When you'll be able to boot into Windows, you'll need to reinstall Grub2 from LiveCD. Again, there's [a HOWTO](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD).

---

