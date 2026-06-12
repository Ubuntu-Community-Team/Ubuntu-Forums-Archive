---
title: "Win7 Dual-Boot Woes"
date: 2011-02-01
forum: General Help
---

### Post by TySkby on 2011-02-01
Hi All,

This is my first post- I think this is the right forum, but please let me know if I should ask my questions elsewhere.

I've had Ubuntu running standalone on a separate machine for a little while, and wanted to give dual-booting a try with my HP Pavillion DM4 laptop, which is relatively new and came shipped with Windows 7.

I got Ubuntu 10.10 installed fine, but upon restarting and selecting Windows 7 from the Grub boot menu, I get the Windows 7 splash screen, about a milisecond of some flavor of the "Blue Screen" (I can't read any of it because it goes away after less than a second), and then am informed that I need to repair my Win7 installation.

Used the Win7 repair CD, which does absolutely NOTHING- doesn't find my OS, partitions, or anything.  If I select the "Automatically Repair..." option, I am informed that CHKDSK failed because a volume on the system is corrupt.

I followed the Ubuntu dual-boot instructions step-by-step ([here]("https://help.ubuntu.com/community/WindowsDualBoot")), so I'm not sure what I did wrong, but I really don't want to lose my files, which are all located on the Windows partition.

---

### Post by oldfred on 2011-02-01
Post this so we can see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Jerry N on 2011-02-01
There have been several threads on the forums recently concerning the fact that late model HP laptop and netbook computers (and possibly those of other vendors as well) already have all 4 of the 4 permissible partitions used.  If this is true of your machine, the Ubuntu installation has likely overwritten one or more of the partitions and you _might_ have to resort to the installations DVDs you were prompted to create when you initially set up the computer to get Win 7 going again, if you still want Win 7.  

Jerry

---

### Post by oldfred on 2011-02-01
Jerry N.

I like to see result.txt from boot script before I scare the OP that he may have lost his system. If all 4 partitions were used the only install is overwrite the entire system and most users do know not to do that. The problem with Maverick is the install to a partition somehow may also overwrite the windows install. Often the issue is just some missing windows files or corruption that can easily be repaired.

---

### Post by TySkby on 2011-02-02
Thanks for taking a look.  I forgot to mention that I do have access to the folders and files from the Win7 partition in a folder "/Windows".  I'm in the process of backing up the folder in case the computer needs a wipe and a fresh install of everything.

Anyways, here are the results from Boot Info Script:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

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

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 888561832 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2               2,048       409,599       407,552  42 SFS
/dev/sda3    *        409,600   832,886,783   832,477,184  42 SFS
/dev/sda4         832,888,830   976,771,071   143,882,242   5 Extended
/dev/sda5         832,888,832   976,771,071   143,882,240  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        02FE6A1DFE6A096D                       ntfs       SYSTEM                        
/dev/sda3        5222334B22333379                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        88e961a5-b193-4050-9df7-facca01550c7   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda2        /dos                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/UBCD502           iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 88e961a5-b193-4050-9df7-facca01550c7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 88e961a5-b193-4050-9df7-facca01550c7
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 88e961a5-b193-4050-9df7-facca01550c7
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=88e961a5-b193-4050-9df7-facca01550c7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 88e961a5-b193-4050-9df7-facca01550c7
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=88e961a5-b193-4050-9df7-facca01550c7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 88e961a5-b193-4050-9df7-facca01550c7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 88e961a5-b193-4050-9df7-facca01550c7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 02fe6a1dfe6a096d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 5222334b22333379
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=88e961a5-b193-4050-9df7-facca01550c7 /               ext3    errors=remount-ro 0       1
# /dos was on /dev/sda2 during installation
UUID=02FE6A1DFE6A096D /dos            ntfs    defaults,umask=007,gid=46 0       0
# /windows was on /dev/sda3 during installation
UUID=5222334B22333379 /windows        ntfs    defaults,umask=007,gid=46 0       0

=================== sda5: Location of files loaded by Grub: ===================


 454.9GB: boot/grub/core.img
 454.9GB: boot/grub/grub.cfg
 454.9GB: boot/initrd.img-2.6.35-25-generic-pae
 455.0GB: boot/vmlinuz-2.6.35-25-generic-pae
 454.9GB: initrd.img
 455.0GB: vmlinuz

```

---

### Post by oldfred on 2011-02-02
Your windows partitions are SFS or dynamic which is similar to LVM in Linux or logical volumes not real partitions. Ubuntu/grub have had lots of issues working with SFS partitions. I am surprised that we can even see the windows boot stanza in the grub menu.

Microsoft's official policy on SFS partitions is you cannot convert back to basic without fully backing up every partition, deleting entire hard drive & repartition & copy back.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)


You installed grub to sda5, a partition. Grub2 is the boot loader and has to be installed to the MBR of the drive or sda, not sda5.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

You also do not have swap. If you have lots of RAM memory it will work. Some with lots of memory do run without swap, but others say even if you do not use it system runs better with some swap.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by TySkby on 2011-02-03
Okay, thanks for the info.  I will try that out tonight and will definitely post the results of my efforts.

Thanks much.

---

### Post by Soham_Orion69 on 2011-05-18
hey i had the same problem so i went to hp service center and apparently theres an overide feature that dosent allow us to dual boot

---

