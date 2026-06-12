---
title: "GRUB Editor"
date: 2010-05-08
forum: General Help
---

### Post by mscout2004 on 2010-05-08
Having trouble with grub during the update to 10.04 it changed the windows loader from SDA0 to SDA1 so windows wont load now. I cant find the grub editor anymore. Where was it moved to????

---

### Post by mscout2004 on 2010-05-08
Any one have any ideas need to fix ASAP for college work.

---

### Post by linuxman94 on 2010-05-08
Run this command from the terminal (Applications -> Accessories -> Terminal) and see if that fixes it.

```
sudo update-grub
```

---

### Post by mscout2004 on 2010-05-08
It is still pointing the win loader to SDA1 but I installed the win loader on SDA0

---

### Post by linuxman94 on 2010-05-08
So windows isn't booting when you select it?  Hmmmmmm :-k


Can you please run this script and post the output?  Use code tags (the # sign in the post creator) to keep the area small.

[Boot Info Script]("http://downloads.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh?use_mirror=hivelocity")

To run it, cd to the directory where it is saved and run this command:

```
./boot_info_script055.sh
```

---

### Post by mscout2004 on 2010-05-08
I ran the script but there was no output

---

### Post by linuxman94 on 2010-05-08
Oops.  You need to run the command as root so add sudo in front of the command.

---

### Post by mscout2004 on 2010-05-08
I did it as sudo but it didnt give me any output

---

### Post by linuxman94 on 2010-05-08
Did it just return you to the prompt?

Make sure it is marked as executable.

---

### Post by mscout2004 on 2010-05-08
this is what i did and what it gave me:

mscout2004@mscout2004-Ubuntu:~/Downloads$ sh boot_info_script055.sh
Please use "sudo" or become "root" to run this script.
mscout2004@mscout2004-Ubuntu:~/Downloads$ sudo sh boot_info_script055.sh
[sudo] password for mscout2004: 
mscout2004@mscout2004-Ubuntu:~/Downloads$

---

### Post by linuxman94 on 2010-05-08
Is it marked as executable in the Properties dialog?

---

### Post by Ravernomina on 2010-05-08
> **linuxman94 said:**
> Is it marked as executable in the Properties dialog?

Yes it is... its so the Bootloader will have rights to execute it. Basically the New Grub.cfg is kind of like a Programing language. So basically your putting in code to execute. So yes leave it marked as executable :D

---

### Post by mscout2004 on 2010-05-08
it is marked as an executable

---

### Post by mscout2004 on 2010-05-08
mscout2004@mscout2004-Ubuntu:~/Downloads$ sudo sh boot_info_script055.sh
mscout2004@mscout2004-Ubuntu:~/Downloads$ sudo sh boot_info_script055.sh
mscout2004@mscout2004-Ubuntu:~/Downloads$

---

### Post by Ravernomina on 2010-05-08
> **mscout2004 said:**
> mscout2004@mscout2004-Ubuntu:~/Downloads$ sudo sh boot_info_script055.sh
mscout2004@mscout2004-Ubuntu:~/Downloads$ sudo sh boot_info_script055.sh
mscout2004@mscout2004-Ubuntu:~/Downloads$


Try this
```
sudo sh ./boot_info_script055.sh
```

---

### Post by mscout2004 on 2010-05-08
same resault:

mscout2004@mscout2004-Ubuntu:~/Downloads$ sudo sh ./boot_info_script055.sh
mscout2004@mscout2004-Ubuntu:~/Downloads$

---

### Post by arpanaut on 2010-05-08
The script writes a text file to the Downloads folder,
It won't output to the terminal.

---

### Post by linuxman94 on 2010-05-08
Just use ./ not sh ./

```
sudo ./boot_info_script055.sh
```

Post Results.txt

@arpanaut

There is still output displayed in the terminal. It should show:

```
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda3 for information... 
Finished. The results are in the file RESULTS1.txt located in /home/evan/Downloads

```

---

### Post by mscout2004 on 2010-05-08
```
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 329780118 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 320268038 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
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
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 320294414 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb1 has 307196048 sectors, but according to the info 
                       from fdisk, it has 314568763 sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 320268694 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb2 starts at sector 0. But according to the info 
                       from fdisk, sdb2 starts at sector 314584830.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   319,000,061   318,793,214   7 HPFS/NTFS
/dev/sda3         319,000,574   625,137,344   306,136,771   5 Extended
/dev/sda5         625,057,083   625,137,344        80,262  82 Linux swap / Solaris
/dev/sda6         319,000,576   625,055,743   306,055,168  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   314,568,826   314,568,764   7 HPFS/NTFS
/dev/sdb2         314,584,830   488,392,064   173,807,235   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4CA26D78A26D6802                       ntfs       System Reserved               
/dev/sda2        86D878A0D8789063                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        3dd2a690-c034-4ee4-b843-fdc192758ce3   swap                                     
/dev/sda6        504c5448-80ec-4d62-b528-7ab3faa9d10b   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        14D4A385D4A36826                       ntfs                                     
/dev/sdb2        B5B5-C14F                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sdb1        /media/14D4A385D4A36826  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/86D878A0D8789063  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 504c5448-80ec-4d62-b528-7ab3faa9d10b
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
search --no-floppy --fs-uuid --set 504c5448-80ec-4d62-b528-7ab3faa9d10b
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 504c5448-80ec-4d62-b528-7ab3faa9d10b
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=504c5448-80ec-4d62-b528-7ab3faa9d10b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 504c5448-80ec-4d62-b528-7ab3faa9d10b
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=504c5448-80ec-4d62-b528-7ab3faa9d10b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 504c5448-80ec-4d62-b528-7ab3faa9d10b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=504c5448-80ec-4d62-b528-7ab3faa9d10b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 504c5448-80ec-4d62-b528-7ab3faa9d10b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=504c5448-80ec-4d62-b528-7ab3faa9d10b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 504c5448-80ec-4d62-b528-7ab3faa9d10b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 504c5448-80ec-4d62-b528-7ab3faa9d10b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ca26d78a26d6802
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 232.2GB: boot/grub/core.img
 176.5GB: boot/grub/grub.cfg
 232.2GB: boot/initrd.img-2.6.32-21-generic
 232.1GB: boot/initrd.img-2.6.32-22-generic
 232.1GB: boot/vmlinuz-2.6.32-21-generic
 168.1GB: boot/vmlinuz-2.6.32-22-generic
 232.1GB: initrd.img
 232.2GB: initrd.img.old
 168.1GB: vmlinuz
 232.1GB: vmlinuz.old
```

---

### Post by cariboo on 2010-05-08
Have a look at [this]("http://ubuntuforums.org/showpost.php?p=8930091&postcount=4") post, it should solve your problem.

---

### Post by mscout2004 on 2010-05-09
> **cariboo907 said:**
> Have a look at [this]("http://ubuntuforums.org/showpost.php?p=8930091&postcount=4") post, it should solve your problem.
  
I looked at this earlier and tried it but still no luck couldnt get testdisk to do anything for me. I followed the instructions but no change happened.

---

### Post by mscout2004 on 2010-05-09
Anyone know how to read that results.txt file I posted? I cant make any sense of it.

---

### Post by mscout2004 on 2010-05-09
Will check this again in the morn hopefully someone knows whats up with this. I have to have my win partition back for my school work.

---

### Post by mscout2004 on 2010-05-09
still cant boot win anyone else got ideas

---

### Post by mscout2004 on 2010-05-09
Still need help with my grub win loader problem

---

### Post by linuxman94 on 2010-05-09
It looks like you have grub installed on your windows partition.  In the link that cariboo907 posted, did you change the hard drive so that it was relevant to your configuration?  When it says "Select the Windows system partition /dev/sda3 and choose "boot," you should select /dev/sda1 then repeat the process selecting /dev/sda2.

Then run testdisk pointing to /dev/sdb

```
sudo testdisk /dev/sdb
```

and select /dev/sdb1 and then /dev/sdb2.

---

### Post by mscout2004 on 2010-05-09
oh so I have to do the testdisk twice each drive cause I have two Win7 installs and two drives??

---

### Post by linuxman94 on 2010-05-09
Well it looks like you have grub installed on multiple partitions so yes.

---

### Post by mscout2004 on 2010-05-09
linuxman you are a lifesaver now I can get my projects turned in on time. THANK YOU VERY MUCH!!!!:P:P:P:P:P

---

### Post by linuxman94 on 2010-05-09
You're very welcome.  Please mark your thread as solved using the Thread Tools menu at the top of this page.

---

