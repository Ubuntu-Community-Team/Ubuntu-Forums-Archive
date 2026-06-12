---
title: "windows will not boot after ubuntu install"
date: 2010-07-10
forum: General Help
---

### Post by pedro6 on 2010-07-10
i installed Ubuntu 9.10 on my windows 7 laptop the other day, it all went fine until i tried to boot into windows, it came up with 0xc00225 the boot sector failed. when i try to do fixmbr it writes over grub and comes up with "this disc is not boot-able" and fixboot and all the other commands like that come up with "could not open the volume root directory: the parameter is incorrect".
i think it is some thing to do about resizing the partition, i did it with the window manage thing. i also can get into the partitions in Ubuntu and their both there so i didn't delete anything.
has anyone had an issue like this or any idea how i could try and fix it?
thanks

---

### Post by Rubi1200 on 2010-07-10
Did you install Ubuntu from the CD or is this a Wubi install?

If you installed with a CD, do you still have it?

If the answer is yes:

Boot the computer with the CD and choose to try Ubuntu in live mode.

Once you are at the Desktop, click on the link at the bottom of my post and follow the instructions there before posting the results back here. Please wrap the text with the code # tags; makes for easier reading.

---

### Post by pedro6 on 2010-07-10
ok i have done that
```
[RESULTS.txt]("http://ubuntuforums.org/attachment.php?attachmentid=162959&d=1278746366")
```
thanks for the help[]("http://ubuntuforums.org/attachment.php?attachmentid=162959&d=1278746366")

---

### Post by Rubi1200 on 2010-07-10
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63. According to the info in the 
                       boot sector, sda1 has 0 sectors.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe56ad066

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63         2,047         1,985   0 Empty
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   317,665,279   317,255,680  42 SFS
/dev/sda4         317,669,310   488,392,064   170,722,755   5 Extended
/dev/sda5         317,669,373   356,723,324    39,053,952  83 Linux
/dev/sda6         356,723,388   364,530,914     7,807,527  82 Linux swap / Solaris
/dev/sda7         364,530,978   488,392,064   123,861,087  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        358B-7A48                              vfat                                     
/dev/sda2        80C82025C8201BC2                       ntfs       SYSTEM                        
/dev/sda3        9012251712250436                       ntfs                                     
/dev/sda5        c10bd006-62cd-4e3e-9896-94cf999f0c1d   ext4                                     
/dev/sda6        f90749b0-eded-4103-93ef-c3c4bc78f4c0   swap                                     
/dev/sda7        88f89e6d-8a5a-4dd4-ab3a-9cd428f904f9   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=ryan)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set c10bd006-62cd-4e3e-9896-94cf999f0c1d
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set c10bd006-62cd-4e3e-9896-94cf999f0c1d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c10bd006-62cd-4e3e-9896-94cf999f0c1d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set c10bd006-62cd-4e3e-9896-94cf999f0c1d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c10bd006-62cd-4e3e-9896-94cf999f0c1d ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 80c82025c8201bc2
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9012251712250436
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=c10bd006-62cd-4e3e-9896-94cf999f0c1d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=88f89e6d-8a5a-4dd4-ab3a-9cd428f904f9 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=f90749b0-eded-4103-93ef-c3c4bc78f4c0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 165.1GB: boot/grub/core.img
 165.1GB: boot/grub/grub.cfg
 163.4GB: boot/initrd.img-2.6.31-14-generic
 165.0GB: boot/vmlinuz-2.6.31-14-generic
 163.4GB: initrd.img
 165.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

This is how we need to see it; just for future reference.

Ok, the problem seems to be here:

 > Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63. According to the info in the 
                       boot sector, sda1 has 0 sectors.

See here too:

> /dev/sda1    *             63         2,047         1,985   0 Empty
/dev/sda2    *          2,048       409,599       407,552  42 SFS

I am not sure what is going on here. 

I suggest you wait until one of the more experienced forum members comes along with some advice.

Meantime, just hang in there please.

---

### Post by pedro6 on 2010-07-10
just for a bit more info bootrec.exe/fixboot says the volume does not contain recognized file system
bootrec.exe/rebuild says total identified windows installation: 0 
bootsect.exe/nt60 all  says could not open the volume root directory: the parameter is incorrect.
and i have done startup repair a lot of times now and hasn't worked.
thanks

---

### Post by oldfred on 2010-07-10
You have two boot flags and can only have one on a primary partition. Windows will normally repair the partition with the boot flag but if you have two it gets lost.

You can use gparted, right click on partition & manage flags, Disk Utility, or command line:
set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda

You have a boot partition in sda2 but your sda3 looks like it has all the files to boot. Was sda3 repaired?  I would set flag on sda2 and repair. See it it works. Then set flag on sda3 and repair.

I see your windows partitions are SFS which has caused issues in the past. This is a windows only partition dynamic disk. I think it was easy to convert to that and just about impossible to convert back.

---

### Post by pedro6 on 2010-07-10
thanks for the help but changing the boot flags didn't work it still does the exact same thing when trying the repair disc. 
do you think reinstalling window would be a good idea? but i would have to download the ISO first which will such with slow Internet.
thanks

---

### Post by oldfred on 2010-07-11
Do not know, but if you do make sure the partitions are pure NTFS not SFS with NTFS.

---

### Post by pedro6 on 2010-07-16
thanks for the help it was the sfs, i had a bit of trouble and had to recover one of my partitions and some how restored windows back to a build, but i was able to get it back. i never would have got that if it wasn't for you's, and i think it is kind of funny how the ubuntu forum can help me with windows but the windows 7 forum was basically useless. 
thank you for your help.

---

