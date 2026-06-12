---
title: "grub2 doal boot problem"
date: 2010-04-24
forum: General Help
---

### Post by mr0no on 2010-04-24
I have a very rare problem with grub. I have dual-boot with windows 7 and ubuntu, but windows doesn't want to boot from grub. This is what happened: I installed windows 7 and ubuntu, and everything worked. Then my windows 7 installation crashed - when i tried to start it, it ran disk check, and it just couldn't load. So i made new partition, and install new windows 7 on it. Everything worked ok, i could boot new windows and crashed one, until i decided to format the crashed windows partition. I guess boot manager for windows was on crashed windows' partition, and now it can't load. I tried update-grub, but it didn't change anything.

---

### Post by ajgreeny on 2010-04-24
First thing to try is reinstalling grub with the live CD
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by mr0no on 2010-04-25
> **ajgreeny said:**
> First thing to try is reinstalling grub with the live CD
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

I followed tutorial correctly, no errors found, but now there's no windows 7 option in grub menu when booting up. Only ubuntu, ubuntu recovery mode, memtest, and chainloader something...

---

### Post by ajgreeny on 2010-04-25
What's the "chainloader something" that you talk of?  Perhaps that is your windows, buty having no exoerience of windows 7 which seems to boot differently to XP, the last windows I used, I can't help further, I'm afraid.

What happens if you pick this chainloader line from grub?

---

### Post by mr0no on 2010-04-25
> **ajgreeny said:**
> What's the "chainloader something" that you talk of?  Perhaps that is your windows, buty having no exoerience of windows 7 which seems to boot differently to XP, the last windows I used, I can't help further, I'm afraid.

What happens if you pick this chainloader line from grub?


The option is "chainload into grub 2", and when i select it, it goes to black screen and says:
"error 11: unrecognized device string"
"press any key to continue..."

and if i press enter, it just goes back to grub menu

---

### Post by john newbuntu on 2010-04-25
As you said, your bootloader is hosed up.  Hoping that you have all of your data backed up.  First get W7 to work properly.  Follow the post below by talsemgeest and repair the bootloader for W7:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
If you do not have the W7 install CDs, there is a link to neosmart to download some very basic startup repair utilities.

Then in the same post, there are instructions to restore Grub bootloader based on the version of grub you have.

---

### Post by mr0no on 2010-04-25
> **john newbuntu said:**
> As you said, your bootloader is hosed up.  Hoping that you have all of your data backed up.  First get W7 to work properly.  Follow the post below by talsemgeest and repair the bootloader for W7:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
If you do not have the W7 install CDs, there is a link to neosmart to download some very basic startup repair utilities.

Then in the same post, there are instructions to restore Grub bootloader based on the version of grub you have.

In windows installation cd command "bootrec.exe /fixboot" didn't work, it said "element not found". But command [FONT=monospace]b[/FONT]ootrec.exe /fixmbr worked well. So I rebooted, and grub didn't load, it showed error "NTLDR is missing", so i recovered grub from live cd following some tutorial (don't remember the link) - this one didn't work [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708). 
Grub menu is the same as it was before, but now there's no chainload option. Its just ubuntu, ubuntu recovery mode, and memtest.

---

### Post by carl4926 on 2010-04-25
Following the live CD repair, once you booted

Did you actually run this from your installed ubuntu

```
sudo update-grub
``````
sudo grub-install /dev/sda
```

---

### Post by mr0no on 2010-04-25
i ran those commands from live CD, and then from ubuntu too.

---

### Post by carl4926 on 2010-04-25
>  it showed error "NTLDR is missing"This is confusing me, it's a WIN XP error, not win7. There is no NTLDR in win7.

It's really easy all this. Just repair win7 and once that is booting, repair grub again with the live CD

---

### Post by mr0no on 2010-04-25
> **carl4926 said:**
> This is confusing me, it's a WIN XP error, not win7. There is no NTLDR in win7.

It's really easy all this. Just repair win7 and once that is booting, repair grub again with the live CD

Last time i repaired windows it completely wiped out my ubuntu partition, so i tried to avoid this. But if it's only solution, ill make a backup and try...

---

### Post by carl4926 on 2010-04-25
> **mr0no said:**
> Last time i repaired windows it completely wiped out my ubuntu partition, so i tried to avoid this. But if it's only solution, ill make a backup and try...

No way it should do that.

---

### Post by dino99 on 2010-04-25
you have to boot on ubuntu, then into console teach grub2 about other distro:

sudo grub-mkconfig
sudo update-grub

it might be ok

---

### Post by mr0no on 2010-04-25
> **dino99 said:**
> 
sudo grub-mkconfig
sudo update-grub


didn't work

---

### Post by oldfred on 2010-04-25
Lets see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by mr0no on 2010-04-25
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub in the file /ubninit looks at sector on boot 
                       drive #-127 for the stage2 file, but no stage2 files 
                       can be found at this location.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x081e081d

Partition  Boot         Start           End          Size  Id System

/dev/sda2                  63   249,087,824   249,087,762   5 Extended
/dev/sda5                 126   238,886,549   238,886,424  83 Linux
/dev/sda6         238,886,613   249,087,824    10,201,212  82 Linux swap / Solaris
/dev/sda3         249,087,825   488,392,064   239,304,240   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x36293628

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1022 MB, 1022361600 bytes
255 heads, 63 sectors/track, 124 cylinders, total 1996800 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000338fa

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     1,992,059     1,991,997   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda3        565D04EA2E22E335                       ntfs                                     
/dev/sda5        169dbfc5-0151-4788-954f-50e455b70ca9   ext4                                     
/dev/sda6        1f114063-b4c2-4dc9-aba0-201f39dc95b2   swap                                     
/dev/sdb1        8E002DCE002DBE59                       ntfs       500 GB                        
/dev/sdc1        BA11-BDD0                              vfat       NEW VOLUME                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/500gb             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /media/win7              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /media/NEW VOLUME        vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=169dbfc5-0151-4788-954f-50e455b70ca9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=169dbfc5-0151-4788-954f-50e455b70ca9

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-20-generic-pae
uuid        169dbfc5-0151-4788-954f-50e455b70ca9
kernel        /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=169dbfc5-0151-4788-954f-50e455b70ca9 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic-pae
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic-pae (recovery mode)
uuid        169dbfc5-0151-4788-954f-50e455b70ca9
kernel        /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=169dbfc5-0151-4788-954f-50e455b70ca9 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic-pae

title        Ubuntu 9.10, memtest86+
uuid        169dbfc5-0151-4788-954f-50e455b70ca9
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set 169dbfc5-0151-4788-954f-50e455b70ca9
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
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 169dbfc5-0151-4788-954f-50e455b70ca9
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=169dbfc5-0151-4788-954f-50e455b70ca9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 169dbfc5-0151-4788-954f-50e455b70ca9
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=169dbfc5-0151-4788-954f-50e455b70ca9 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
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
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 565d04ea2e22e335
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
UUID=169dbfc5-0151-4788-954f-50e455b70ca9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1f114063-b4c2-4dc9-aba0-201f39dc95b2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1    /media/500gb    ntfs defaults 0 0
/dev/sda3    /media/win7    ntfs defaults 0 0

=================== sda5: Location of files loaded by Grub: ===================


    .3GB: boot/grub/grub.cfg
   6.2GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2
   1.5GB: boot/initrd.img-2.6.31-20-generic-pae
    .3GB: boot/vmlinuz-2.6.31-20-generic-pae
   1.5GB: initrd.img
    .3GB: vmlinuz
=============================== StdErr Messages: ===============================

hexdump: /media/NEW: No such file or directory
hexdump: VOLUME/ubninit: No such file or directory
./Downloads/boot_info_script055.sh: line 789: [: -lt: unary operator expected
./Downloads/boot_info_script055.sh: line 789: [: -lt: unary operator expected
./Downloads/boot_info_script055.sh: line 789: [: -lt: unary operator expected

```

---

### Post by oldfred on 2010-04-25
Did you somewhere delete a sda1 or overwrite sda2. You have no NTFS partition flagged as boot and the win7 partition is missing some boot files which then are usually in the 100mb partition that win7 creates with a clean install.

I think if you set the boot flag on sda3 and then run teh windows repairs it should work.

Grub will only find working windows partitions. And grub legacy is not as good as grub2 at finding windows.

To set boot partition you can use gparted, right click on partition and manage flags, disk utility or command line:

set boot flag on for sda3 (off on others)
sudo sfdisk -A3 /dev/sda
Some bios refuse to boot a hard drive without a boot flag. Although linux does not need one.
More precisely: Some Bios require a boot flag on a primary partition.
So it is not important that the first partition has the boot flag, but that one of the first four partition has a boot flag.

---

### Post by carl4926 on 2010-04-25
This is very messy and we were working on the understanding that you were using Grub2
BUT

```
=>[COLOR=DarkRed] Grub 0.97 is installed[/COLOR] in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc
```

---

### Post by mr0no on 2010-04-25
> **oldfred said:**
> 
I think if you set the boot flag on sda3 and then run teh windows repairs it should work.


Didn't work. In windows installation cd command line I typed in bootrec.exe /fixboot, and bootrec.exe /fixmbr. Both commands were executed successfully, but now grub didn't start. It just froze on the screen that would be before grub would usually start. I repaired grub with live CD, but it's the same as it was before.

---

### Post by oldfred on 2010-04-25
After you did fixMBR you should not have grub. You should be booting directly into windows to make sure it boots ok. 

Did you run all the windows commands to repair.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

I do not think this microsoft site site mentions chkdsk but you should also run it.
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Once you know windows works then you can reinstall grub.

---

### Post by mr0no on 2010-04-26
> **oldfred said:**
> 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd
.

Didn't work. 


I give up. I just formatted and reinstalled windows. Thank you all for your support. Great community!

---

