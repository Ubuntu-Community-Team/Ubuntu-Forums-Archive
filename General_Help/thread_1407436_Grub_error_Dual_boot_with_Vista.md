---
title: "Grub error? Dual boot with Vista"
date: 2010-02-15
forum: General Help
---

### Post by The_Eggert on 2010-02-15
Hey
Here the other day, I decided to try out 10.04 Alpha. But after I had done it, I weren't able to boot Vista anymore. When I choose it in the grub boot loader, it changes to only showing the word "GRUB", and nothing more happens.
As a desperate attempt to fix it, and because I weren't happy using the Alpha, I then decided to switch back to 9.10, but the problem with booting Vista persists...
Anyone got a clue as to how to fix it?

---

### Post by ironclaw on 2010-02-16
In Ubuntu, run
```
sudo update-grub
```
then try to boot into Vista again.

---

### Post by The_Eggert on 2010-02-16
> **ironclaw said:**
> In Ubuntu, run
```
sudo update-grub
```
then try to boot into Vista again.

Thanks for the answer, but I tried it, and it didn't work :(

---

### Post by m4tic on 2010-02-16
from now onwards use
```
sudo update-grub2
```

---

### Post by The_Eggert on 2010-02-16
> **m4tic said:**
> from now onwards use
```
sudo update-grub2
```

That doesn't do anything helpful either...
But the problem isn't that I can't see Vista in the boot-menu, but it just won't boot, once selected, it merely prints the word "GRUB" in the top left corner.

---

### Post by oldfred on 2010-02-16
sudo update-grub2 just calls update-grub which calls the grub-mkconfig.

Grub will only boot working Vista so did something happen to Vista?

To see the entire boot setup:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by The_Eggert on 2010-02-16
> **oldfred said:**
> sudo update-grub2 just calls update-grub which calls the grub-mkconfig.

Grub will only boot working Vista so did something happen to Vista?

To see the entire boot setup:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

Here's the output from the script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=e2991b39-722a-4df2-b990-c032edf448d0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 345114527 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 345114591 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0592de3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   951,416,831   951,416,769   7 HPFS/NTFS
/dev/sda2         951,416,832   976,766,975    25,350,144   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0aa64020

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   958,630,679   958,630,617  83 Linux
/dev/sdb2         958,630,680   976,768,064    18,137,385   5 Extended
/dev/sdb5         958,630,743   976,768,064    18,137,322  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        063C1DA73C1D92B3                       ntfs       Lokal Disk                    
/dev/sda2        42EA165CEA164C93                       ntfs       RECOVERY                      
/dev/sdb1        e2991b39-722a-4df2-b990-c032edf448d0   ext4                                     
/dev/sdb5        e61d7730-68ec-47dd-9151-d209b84be827   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set e2991b39-722a-4df2-b990-c032edf448d0
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e2991b39-722a-4df2-b990-c032edf448d0
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e2991b39-722a-4df2-b990-c032edf448d0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e2991b39-722a-4df2-b990-c032edf448d0
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e2991b39-722a-4df2-b990-c032edf448d0 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e2991b39-722a-4df2-b990-c032edf448d0
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e2991b39-722a-4df2-b990-c032edf448d0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e2991b39-722a-4df2-b990-c032edf448d0
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e2991b39-722a-4df2-b990-c032edf448d0 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 063c1da73c1d92b3
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 42ea165cea164c93
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
UUID=e2991b39-722a-4df2-b990-c032edf448d0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e61d7730-68ec-47dd-9151-d209b84be827 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .9GB: boot/grub/core.img
   1.9GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
   2.4GB: boot/initrd.img-2.6.31-19-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
    .9GB: boot/vmlinuz-2.6.31-19-generic
   2.4GB: initrd.img
    .5GB: initrd.img.old
    .9GB: vmlinuz
    .6GB: vmlinuz.old

```

---

### Post by oldfred on 2010-02-16
You installed grub into the partition (PBR) boot as well as the MBR. Windows has essential files in the PBR. You also are missing winload.exe in the list of files. Did you have another install of windows?

I would try to repair your Vista.

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm)
There are some good instructions here: 
[http://www.sevenforums.com/installation-setup/18466-how-do-i-replace-orginal-mbr-win-7-a.html](http://www.sevenforums.com/installation-setup/18466-how-do-i-replace-orginal-mbr-win-7-a.html)

---

### Post by The_Eggert on 2010-02-17
> **oldfred said:**
> You installed grub into the partition (PBR) boot as well as the MBR. Windows has essential files in the PBR. You also are missing winload.exe in the list of files. Did you have another install of windows?

I would try to repair your Vista.

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm)
There are some good instructions here: 
[http://www.sevenforums.com/installation-setup/18466-how-do-i-replace-orginal-mbr-win-7-a.html](http://www.sevenforums.com/installation-setup/18466-how-do-i-replace-orginal-mbr-win-7-a.html)

Thanks for the great answer, I'm sure it will be useful to me at some point, since I always seems to find a way to **** my computer ;)
However, it didn't do the trick this time, since now, my computer won't boot neither of my OS'...Now it just shows an almost entirely black screen, with the little white underscore blincking in the upper left corner.

But to answer some of the questions, and how the test went...
No, I haven't had any other versions of Windows installed.
I've run chkdsk a couplke of times, and none of the times, have given any errors - nor has "Startup repair"
When I ran BootRec.exe with "/Fixmbr" and "/Fixboot" i got the reply that it went successful. But when I ran "/ScanOs" it replied that it didn't find any windows installations - I don't suppose that meant to be?
But nevertheless, I choose to run "/RebuildBcd"...And now I'm stuck..
I have also tried restoreing grub, but never really got started, since it couldn't find what it was supposed to...
I have backed up all my important data, from ubuntu, so I don't really care about that OS, at this point, but rather imterested in getting access to Vista...
Am i totally screwed..?

---

### Post by oldfred on 2010-02-17
You had grub installed in both sda and sdb and the windows install of fixmbr should have only overwritten sda's MBR. If in BIOS you switch drives to sdb can you boot? From either a boot or a liveCD do you still see your Vista install. It was missing essential files but I thought that the repair might fix it.

---

### Post by The_Eggert on 2010-02-17
> **oldfred said:**
> You had grub installed in both sda and sdb and the windows install of fixmbr should have only overwritten sda's MBR. If in BIOS you switch drives to sdb can you boot? From either a boot or a liveCD do you still see your Vista install. It was missing essential files but I thought that the repair might fix it.

You say that it's missing essential files? So is it lost for me to fix, since the repair didn't do the job?

And I was able to at least start the boot process from sdb, but I got this message:
```
GRUB loading.
error: the symbol 'grub_getchartwidth' not found.
grub rescue > 
```
What do I do with that?

---

### Post by meierfra. on 2010-02-17
> You also are missing winload.exe in the list of files.
Since the boot info script was able to identify the Vista OS, it means the winload.exe is not  missing.  So the fact that "winload.exe" is not listed must be caused by a bug in the Boot Info Script.

> So is it lost for me to fix, since the repair didn't do the job?
There are other methods to fix the boot sector. Boot from the Ubuntu LiveCD and run the boot info script again so that we can  figure out your current status.

---

### Post by The_Eggert on 2010-02-17
> **meierfra. said:**
> Since the boot info script was able to identify the Vista OS, it means the windoad.exe is not  missing.  So the fact that "winload.exe" is not listed must be caused by a bug in the Boot Info Script.


There are other methods to fix the boot sector. Boot from the Ubuntu LiveCD and run the boot info script again so that we can  figure out your current status.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 345114591 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0592de3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   951,416,831   951,416,769   7 HPFS/NTFS
/dev/sda2         951,416,832   976,766,975    25,350,144   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0aa64020

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   958,630,679   958,630,617  83 Linux
/dev/sdb2         958,630,680   976,768,064    18,137,385   5 Extended
/dev/sdb5         958,630,743   976,768,064    18,137,322  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e44ed

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62     7,826,383     7,826,322   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       957fbf22-9dce-48e6-9eb2-3d7dbea56e0a   ext3                                     
/dev/sda1        063C1DA73C1D92B3                       ntfs       Lokal Disk                    
/dev/sda2        42EA165CEA164C93                       ntfs       RECOVERY                      
/dev/sdb1        e2991b39-722a-4df2-b990-c032edf448d0   ext4                                     
/dev/sdb5        e61d7730-68ec-47dd-9151-d209b84be827   swap                                     
/dev/sdc1        022D-F1B7                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set e2991b39-722a-4df2-b990-c032edf448d0
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set e2991b39-722a-4df2-b990-c032edf448d0
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=e2991b39-722a-4df2-b990-c032edf448d0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set e2991b39-722a-4df2-b990-c032edf448d0
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=e2991b39-722a-4df2-b990-c032edf448d0 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set e2991b39-722a-4df2-b990-c032edf448d0
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e2991b39-722a-4df2-b990-c032edf448d0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set e2991b39-722a-4df2-b990-c032edf448d0
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e2991b39-722a-4df2-b990-c032edf448d0 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 063c1da73c1d92b3
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 42ea165cea164c93
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
UUID=e2991b39-722a-4df2-b990-c032edf448d0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e61d7730-68ec-47dd-9151-d209b84be827 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .9GB: boot/grub/core.img
   1.9GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
   2.4GB: boot/initrd.img-2.6.31-19-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
    .9GB: boot/vmlinuz-2.6.31-19-generic
   2.4GB: initrd.img
    .5GB: initrd.img.old
    .9GB: vmlinuz
    .6GB: vmlinuz.old
```

---

### Post by meierfra. on 2010-02-17
> GRUB loading.
error: the symbol 'grub_getchartwidth' not found.
grub rescue >
Sound like the Grub in /dev/sdb needs to be reinstalled.

```
sudo mount /dev/sdb1 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sdb
```

This should allow you to boot into Ubuntu, if you set your bios to boot from the Ubuntu drive.
You can also try to boot Windows from the Grub menu. But I doubt that it will work.

But why don't you give it a try, while I think about what to do next.


Do you know what's on /dev/sda2(the 12GB partition on the Windows drive) is it a recovery partition?

---

### Post by meierfra. on 2010-02-17
> Now it just shows an almost entirely black screen, with the little white underscore blincking in the upper left corner.
Does this happen immediately or does it look like Windows is starting to boot?

---

### Post by The_Eggert on 2010-02-17
> **meierfra. said:**
> Does this happen immediately or does it look like Windows is starting to boot?

Immediately...And there's also an orange box, and another weird symbol placed on the screen - I don't think it has any special meaning, beyond the fact that it seems like an error...

---

### Post by The_Eggert on 2010-02-17
> **meierfra. said:**
> Sound like the Grub in /dev/sdb needs to be reinstalled.

```
sudo mount /dev/sdb1 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sdb
```

This should allow you to boot into Ubuntu, if you set your bios to boot from the Ubuntu drive.
You can also try to boot Windows from the Grub menu. But I doubt that it will work.

But why don't you give it a try, while I think about what to do next.

I tried that, an I think we might be getting closer :)
But still, I don't think I can boot Ubuntu...
When I choose to boot from the Ubuntu drive, it shows that it loads grub, but it doesn't give me the menu, it just gives me "Minimal BASH-like line editing", you know, it just prints this on screen:
```
grub>
```
Need I do anything from there?

> Do you know what's on /dev/sda2(the 12GB partition on the Windows drive) is it a recovery partition?
Yes, that's just a recovery partition ;)

---

### Post by meierfra. on 2010-02-17
> but it doesn't give me the menu, 
Strange.  Let's see whether you can boot into Ubuntu from the "grub>" prompt:

```

insmod ext2
insmod linux
set root=(hd0,1)
linux /vmlinuz root=/dev/sdb1 ro
initrd /initrd.img
boot

```


If this boots you  into Ubuntu, I suggest to reinstall grub from scratch:

```

sudo apt-get purge   grub-pc grub-common
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sdb
sudo update-grub
```

Reboot and see whether you get the grub-menu.

---

### Post by The_Eggert on 2010-02-17
> **meierfra. said:**
> Strange.  Let's see whether you can boot into Ubuntu from the "grub>" prompt:

```

insmod ext2
insmod linux
set root=(hd0,1)
linux /vmlinuz root=/dev/sdb1 ro
initrd /initrd.img
boot

```


When I write the first command "insmod ext2" I just get:
"Error 27: Unrecognized command"
So what now?

---

### Post by meierfra. on 2010-02-17
Now I understand. Your LiveUSB must be Ubuntu 9.04  or older.  So you installed Legacy Grub.


Try this at the Grub prompt:

```
root (hd0,0)
kernel /vmlinuz root=/dev/sdb1 ro
initrd /initrd.img
boot

```
Once booted into Ubuntu:

```
sudo rm  /boot/grub/*
sudo grub-install --recheck /dev/sdb
sudo update-grub

```

---

### Post by meierfra. on 2010-02-17
Sorry. I had a couple of typos in my previous post. But I fixed them

---

### Post by The_Eggert on 2010-02-17
> **meierfra. said:**
> Now I understand. Your LiveUSB must be Ubuntu 9.04  or older.  So you installed Legacy Grub.


Try this at the Grub prompt:

```
root (hd0,0)
kernel /vmlinuz root=/dev/sdb1 ro
initrd /initrd.img
boot

```
Once booted into Ubuntu:

```
sudo rm  /boot/grub/*
sudo grub-install --recheck /dev/sdb
sudo update-grub

```

That got the ubuntu part working again - Thank you :D
So now I'm more or less back to my original problem - I can't boot Vista..Now, when I choose my Vista Partition, it simply prints the word "compressed" on the screen...
Do you have any idea on how that might be fixed, so that I might finally get into Vista?

---

### Post by meierfra. on 2010-02-17
I'm not sure whether  this will make a difference, but I suggest to "rebuild" the Vista boot sector  with testdisk:

```
sudo apt-get install testdisk

```
(if "testdisk" is not found you have to enable the "universe" repository)
Then

```
 sudo testdisk /dev/sda
```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Vista partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk.
 (If it does not give you an option to "write", it means that the original and rebuild boot sector are identical, and  testdisk RebuildBS won't be able to solve your problem)


As long as you install testdisk you might as well use  it to restore the boot sector of your Recovery partition:


```
 sudo testdisk /dev/sda
```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Recovery  partition and choose
"boot"
"BackupBS"
Press "Y" to confirm.


I'm still a little bit puzzled that the boot info script did not find "winload.exe" So lets make sure that   you really have it:

Go to "Places->Computer" and double click the icon for your Vista partition.  Then navigate to Windows->System32  and see whether you have a file named "winload.exe"  
(Capitalization might be different: So it might the "WINDOWS->SYSTEM32,


Then reboot. Try booting Vista from the Grub menu and by setting to the Bios to boot from the Vista drive.

---

### Post by The_Eggert on 2010-02-18
> **meierfra. said:**
> I'm not sure whether  this will make a difference, but I suggest to "rebuild" the Vista boot sector  with testdisk:

```
sudo apt-get install testdisk

```
(if "testdisk" is not found you have to enable the "universe" repository)
Then

```
 sudo testdisk /dev/sda
```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Vista partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk.
 (If it does not give you an option to "write", it means that the original and rebuild boot sector are identical, and  testdisk RebuildBS won't be able to solve your problem)

I did that, and it didn't give me an option to write, and so, I still can't boot Vista - Not if I boot from the Vista partition, however now, when I do it that way, the colorbox and the weird symbol have disappeared. And when I try to boot Vista from the grub menu, it still just shows "compressed"

> 
As long as you install testdisk you might as well use  it to restore the boot sector of your Recovery partition:


```
 sudo testdisk /dev/sda
```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Recovery  partition and choose
"boot"
"BackupBS"
Press "Y" to confirm.

That must've worked, because I am now able to boot my recovery partition, but it can't automatically find my Vista installation - Don't know if that matters..

> 
I'm still a little bit puzzled that the boot info script did not find "winload.exe" So lets make sure that   you really have it:

Go to "Places->Computer" and double click the icon for your Vista partition.  Then navigate to Windows->System32  and see whether you have a file named "winload.exe"  
(Capitalization might be different: So it might the "WINDOWS->SYSTEM32,

It's there ;)

---

### Post by meierfra. on 2010-02-18
> because I am now able to boot my recovery partition 
At least some progress.

> I did that, and it didn't give me an option to write, and so, I still can't boot Vista 
OK.

I still have no clue what is causing your problems.  So I just have to go through  the list of tools to fix boot problems and hope that one of them works.  Since you fixed the boot sector since the last time  your run "chkdsk" and "startup repair" I suggest to do that again.

Before you run "chkdsk" make sure to use the correct drive letter. Type

```
diskpart
list volume
```
at the command prompt of your Vista CD
Determine the correct drive letter and 

```
chkdsk /r [COLOR="Red"]X:[/COLOR]
```
but replace "X:" by the correct drive letter of your Vista partition.


> It's there
I was pretty sure of that, but I just wanted to be sure.

---

### Post by The_Eggert on 2010-02-18
> **meierfra. said:**
> 
I still have no clue what is causing your problems.  So I just have to go through  the list of tools to fix boot problems and hope that one of them works.  Since you fixed the boot sector since the last time  your run "chkdsk" and "startup repair" I suggest to do that again.

Okay, I'll try that ;)
But while I work on it, I've got another little question...Now that I have access to my recovery partition, what would happen if I were to run System restore?

---

### Post by meierfra. on 2010-02-18
> if I were to run System restore?
You have to check the documentation for your recovery partition. It might just try restore all the system files of your Win 7 partition back to default.  But some recovery partition are only able to wipe the whole hard drive and return the hard drive to factory settings, so all Data on your Vista drive  would be lost (if you don't back them up first)

---

### Post by Jackzor on 2010-02-18
The system restore on the recovery should be exactly the same as the system restore on the Vista O/S So running it will not erase all data. But. I do not believe that a system restore will solve the problem. Although I guess its worth a try. There would be no harm done. Just a half hour of possibly wasted time.

---

### Post by The_Eggert on 2010-02-18
> **meierfra. said:**
> You have to check the documentation for your recovery partition. It might just try restore all the system files of your Win 7 partition back to default.  But some recovery partition are only able to wipe the whole hard drive and return the hard drive to factory settings, so all Data on your Vista drive  would be lost (if you don't back them up first)

I believe it restores to factory settings - but all my data is backed up, I was just wondering if it would f*** things even more up..?

---

### Post by Jackzor on 2010-02-18
Plus. You know. You could just install Windows 7 OVER vista without formatting. You lose nothing. All of your files will be in a "windows.old" folder. My friend did that just last week.

---

### Post by The_Eggert on 2010-02-18
> **Jackzor said:**
> There would be no harm done. Just a half hour of possibly wasted time.

At this time, I have already used a good part of my holiday, so I guess that half an hour wouldn't be too much :D

---

### Post by Jackzor on 2010-02-18
> **The_Eggert said:**
> I believe it restores to factory settings - but all my data is backed up, I was just wondering if it would f*** things even more up..?

I seriously doubt it would harm anything.

Quote "seriously doubt"

I'm not saying that its not possible. But its not likely that it will break your system anymore than it is.

---

### Post by The_Eggert on 2010-02-18
> **Jackzor said:**
> I seriously doubt it would harm anything.

Quote "seriously doubt"

I'm not saying that its not possible. But its not likely that it will break your system anymore than it is.

Okay, great ;)
I'll just see how chkdsk and the like works out for me, and just keep it as a last resort then;)

---

### Post by The_Eggert on 2010-02-19
> **meierfra. said:**
> 
I still have no clue what is causing your problems.  So I just have to go through  the list of tools to fix boot problems and hope that one of them works.  Since you fixed the boot sector since the last time  your run "chkdsk" and "startup repair" I suggest to do that again.

Before you run "chkdsk" make sure to use the correct drive letter. Type

```
diskpart
list volume
```
at the command prompt of your Vista CD
Determine the correct drive letter and 

```
chkdsk /r [COLOR="Red"]X:[/COLOR]
```
but replace "X:" by the correct drive letter of your Vista partition.


I did both of those, and neither reported any errors, or the like?

---

### Post by The_Eggert on 2010-02-20
I ran the system recovery, and Vista works now -> Solved ;)

---

### Post by meierfra. on 2010-02-20
> I ran the system recovery, and Vista works now -> Solved
Great. Strange though, I also  thought that the system recovery would not help.  That means that some of your system files were damaged.  Installing grub to a boot sector would not do that. I wonder whether running "chkdsk"  when your boot sector was corrupted might have done that. But I have no idea.

---

### Post by The_Eggert on 2010-02-21
Yeah, I don't know what it should be either, but it also started saying that my sdb HDD was broken, due to bad sectors, so I figured that I'd best get one working OS for now..

---

