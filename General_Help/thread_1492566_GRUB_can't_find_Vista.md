---
title: "GRUB can't find Vista"
date: 2010-05-24
forum: General Help
---

### Post by Callius on 2010-05-24
I had (still have, actually) Vista installed on one of my HDDs and installed 10.04 on one of my other HDDs (both SATA).

Now, I can't boot into Vista. Whenever I do update-grub I get the following output:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

I've tried reading through the grub2 tutorial stuff and holy crap it's confusing... Can anyone help me figure out why my Vista partition isn't being picked up by Grub?

I ran Boot Info Script, in the event that this information can help someone give me info on how to get GRUB to properly see my Vista partition.

```
      Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,046    15,624,191    15,622,146   5 Extended
/dev/sda5               2,048    15,624,191    15,622,144  82 Linux swap / Solaris
/dev/sda2    *     15,624,192    44,920,831    29,296,640  83 Linux
/dev/sda3          44,920,832   156,248,063   111,327,232  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   156,232,124   156,232,062   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        77ddb452-3a4d-48fb-8f67-a7c4e0da87a0   ext4                                     
/dev/sda3        7e619c5d-ce45-43d4-bb27-f2fe19baf767   ext4                                     
/dev/sda5        74778471-e238-4c1d-8890-67967d7f009b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        729C56339C55F259                       ntfs       magrathea                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        ECB89E61B89E29DA                       ntfs       Games                         
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        32CECA2CCEC9E865                       ntfs                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /home                    ext4       (rw)
/dev/sdb1        /media/magrathea         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 77ddb452-3a4d-48fb-8f67-a7c4e0da87a0
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1600x1200
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
search --no-floppy --fs-uuid --set 77ddb452-3a4d-48fb-8f67-a7c4e0da87a0
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
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 77ddb452-3a4d-48fb-8f67-a7c4e0da87a0
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=77ddb452-3a4d-48fb-8f67-a7c4e0da87a0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 77ddb452-3a4d-48fb-8f67-a7c4e0da87a0
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=77ddb452-3a4d-48fb-8f67-a7c4e0da87a0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 77ddb452-3a4d-48fb-8f67-a7c4e0da87a0
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=77ddb452-3a4d-48fb-8f67-a7c4e0da87a0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 77ddb452-3a4d-48fb-8f67-a7c4e0da87a0
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=77ddb452-3a4d-48fb-8f67-a7c4e0da87a0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 77ddb452-3a4d-48fb-8f67-a7c4e0da87a0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 77ddb452-3a4d-48fb-8f67-a7c4e0da87a0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=77ddb452-3a4d-48fb-8f67-a7c4e0da87a0 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=7e619c5d-ce45-43d4-bb27-f2fe19baf767 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=74778471-e238-4c1d-8890-67967d7f009b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  10.3GB: boot/grub/core.img
  15.2GB: boot/grub/grub.cfg
  10.4GB: boot/initrd.img-2.6.32-21-generic
  10.6GB: boot/initrd.img-2.6.32-22-generic
  10.3GB: boot/vmlinuz-2.6.32-21-generic
   8.2GB: boot/vmlinuz-2.6.32-22-generic
  10.6GB: initrd.img
  10.4GB: initrd.img.old
   8.2GB: vmlinuz
  10.3GB: vmlinuz.old
```

Thanks!

---

### Post by ranch hand on 2010-05-24
Well, the first thing I would do is check your /boot/grub/device.map file and make sure all the drives are listed there.

Second I would have to think on what I really want here.  You have MS on the MBR  of three of your four drives.  If you turn off your Ubuntu drive in bios, your W7 should take over the boot of your box.

Your uuid info doesn't look as if there are any conflicts.  OS-prober should find them.

For now I would like you to check just 2 things.  One is the device map and the other is what happens with the Ubuntu drive out of the loop (turn off in bios or just unplug the bugger).

If every thing is good with your MS drives with that disconnected, and the device chart is correct, try running;
```

sudo update-grub

```
and then;
```

sudo grub-mkconfig

```
please post the output of grub-mkconfig.

My device map with only 2 drives looks like this;
> 
(hd0)    /dev/sda
(hd1)    /dev/sdb

Yours should list all 4.  If not;
```

gksudo gedit /boot/grub/device.map

```
and edit the bugger and save it.  Make sure you check it and make it right before running the other commands.

---

### Post by john newbuntu on 2010-05-24
Normally, in order to boot Vista, there needs to be the windows boot manager(/bootmgr) and the boot configuration data file(/boot/bcd), in addition to the boot loader (winloader.exe).  The first 2 appear to be missing according to meierfra's boot info script.  I am not a 100% sure if vista can boot without these files.  If this is true, then the boot sector of vista (sdd1?) needs to be fixed after setting the BIOS to boot from sdd.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)
Once this is done, set BIOS back to boot from sda and Grub should be able to detect vista after running the command "sudo update-grub"

---

### Post by ranch hand on 2010-05-25
> **john newbuntu said:**
> Normally, in order to boot Vista, there needs to be the windows boot manager(/bootmgr) and the boot configuration data file(/boot/bcd), in addition to the boot loader (winloader.exe).  The first 2 appear to be missing according to meierfra's boot info script.  I am not a 100% sure if vista can boot without these files.  If this is true, then the boot sector of vista (sdd1?) needs to be fixed after setting the BIOS to boot from sdd.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)
Once this is done, set BIOS back to boot from sda and Grub should be able to detect vista after running the command "sudo update-grub"
I am glad that someone who knows something about MS showed up.

That is why I asked hem to try without the Ubuntu disk connected.  I have no idea where those files went (if really gone- beats me).   I have seen several that have been corrupted by grub being installed on the partition instead of the drive, but they are usually there.

If they are not working I think we can fix it with testdisk.

I think he  has a good bit of playing with bios to do.

---

### Post by wilee-nilee on 2010-05-25
> **john newbuntu said:**
> Normally, in order to boot Vista, there needs to be the windows boot manager(/bootmgr) and the boot configuration data file(/boot/bcd), in addition to the boot loader (winloader.exe).  The first 2 appear to be missing according to meierfra's boot info script.  I am not a 100% sure if vista can boot without these files.  If this is true, then the boot sector of vista (sdd1?) needs to be fixed after setting the BIOS to boot from sdd.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)
Once this is done, set BIOS back to boot from sda and Grub should be able to detect vista after running the command "sudo update-grub"

I think your correct here, and here is the short list of the commands to be run with a Vista disc, same as the link basically. I think it has to be a install disc though as I believe the MS bootrec.exe rebuilds the bcd from the disc information. I'm not certain of this though.

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 

BootRec.exe /fixmbr
chkdsk /r
BootRec.exe /FixBoot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd 

@ranch hand isn't this always fun. ;)

---

### Post by ranch hand on 2010-05-25
Tremendous fun.

---

### Post by Callius on 2010-05-25
Excellent, that worked after a few tries.

Is there any way I can get Linux loading now without having to go through that headache again?

---

### Post by ranch hand on 2010-05-26
You should be able to follow these instructions using your Live CD.

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ignore the file editing part, yours are fine.  Just make sure you do not install grub anywhere but on the drive(s) itself not on any partitions.  In other words sda, not sda1 or sda2.  It should find the other drives and OS'.

You will be able to boot to Ubuntu even if it doesn't find them.  Run the commands;
```

sudo update-grub

```
and 
```

sudo grub-mkconfig

```
after booting to Ubuntu if the MS options do not show up on your menu.

If that does happen also check your /boot/grub/device.map and make sure all drives are listed.

---

### Post by oldfred on 2010-05-26
The fixboot command installed windows boot loader to the MBR. 

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But since you have 4 disks, You should have the windows boot loader in sdd and grub in sda so you have the boot loader and the system on the same drive for both windows and Ubuntu. And then set sda as the boot drive since grub will find and let you boot windows.

---

### Post by Callius on 2010-05-26
> **ranch hand said:**
> You should be able to follow these instructions using your Live CD.

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ignore the file editing part, yours are fine.  Just make sure you do not install grub anywhere but on the drive(s) itself not on any partitions.  In other words sda, not sda1 or sda2.  It should find the other drives and OS'.

You will be able to boot to Ubuntu even if it doesn't find them.  Run the commands;
```

sudo update-grub

```
and 
```

sudo grub-mkconfig

```
after booting to Ubuntu if the MS options do not show up on your menu.

If that does happen also check your /boot/grub/device.map and make sure all drives are listed.

Rad, I'll try this tomorrow.

Thanks

---

### Post by cryingthug on 2010-05-27
Why would you want GRUB to find vista?? Just joking!

I think you should edit GRUB so that it will find where the Vista partition starts.

I had to edit GRUB to find my FreeBSD partition.

---

### Post by tectp on 2010-05-28
> **Callius said:**
> Rad, I'll try this tomorrow.

Thanks

And what do you do if by mistake you did install grub to numbered partitions? Because that is what I did!!

Seems to be the cause of my Vista installation not loading.

---

### Post by drs305 on 2010-05-28
> **tectp said:**
> And what do you do if by mistake you did install grub to numbered partitions? Because that is what I did!!

Seems to be the cause of my Vista installation not loading.

If when you try to boot Vista the screen blanks and then returns to the Grub2 menu, see this link:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

---

### Post by tectp on 2010-05-28
> **drs305 said:**
> If when you try to boot Vista the screen blanks and then returns to the Grub2 menu, see this link:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

yes I've worked through this process without any success.
I ran testdisk but the original and backup boot sector are identical. it was unable to fix the problem.

attached bootscript in case that sheds any light.

---

### Post by ranch hand on 2010-05-28
Well, you have a mess don't you.

It looks like grub is installed everywhere.  This is not a good thing.  It should be installed ONLY  on the drive not on partitions.

It is installed on sda1 and sda2.

I do not know much about MS installs but it looks like you are trying to boot to sda1 which is listed as the "Windows Recovery Environment (loader) (on /dev/sda1)" on your grub.cfg file.   As grub is installed there I doubt it is going to boot there.

I believe that you want to boot to sda3 which is the one with what appears to be a working boot sector.

You could try plugging this into your /etc/grub.d/40_custom file;
```

menuentry "Windows (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set AE92823C928208D3
    drivemap -s (hd0) ${root}
    chainloader +1
}

```
and run;
```

sudo update-grub

```
and then
```

sudo grub-mkconfig

```
That should give you a read out of the new grub.cfg file so you can see if the entry is in there near the bottom in the 40_custom section.

If so reboot and try it.  I do not really know if it will work or not, just edited the on you have for a different partition.  Will not hurt anything and if it doesn't work you can remove it.

---

### Post by oldfred on 2010-05-28
You test disk should not give identical results, You have to have a window boot loader in the boot sector of both sda2 & sda3 as you have the win7 install with boot in sda2 and system in sda3.

If not you can from a windows repair CD. You need to fix both sda2 & sda3, but I am not sure that it works on both. You may have to move the boot flag to sda3. Then the repairs will make that both the boot & system partition (obsoleting sda2 boot partition).

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Vista/7
BootRec.exe /FixBoot #updates PBR or partition boot sector
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista possibly 7:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)


set boot flag on for sda3 (off on others)
sudo sfdisk -A3 /dev/sda

---

### Post by tectp on 2010-05-29
Many thanks for your attention to this problem. Yes, quite a mess I got myself into I agree. 
I run a dual boot system for Windows Vista and Ubuntu Lucid. 
sda1 is the windows recovery environment
sda2 is the main windows installation, system files etc and also where the boot flag is set normally.
sda3 is an ntfs partition where i store all my documents and media files so they can be accessed from either of the 2 operating systems
sda4 is a container for my linux partitions
sda5 is the ubuntu installation
sda6 is a swap partition created by the linux installation.

When i upgraded grub2 I used a live cd to boot mounting the drive partitions and running:

dpkg-reconfigure-grub-pc

i became confused when reading on a post that you could install to all drives without causing any problems. I was confusing "drive" or "device" with "partitions" I suppose. These things happen. So i went ahead and installed it to sda1,2 and 5 which is where I thought it would be needed.

Realising my mistake and repeating the install process, I selected only the sda device and de-selected all the partitions, but grub2 remains installed on the partitions 1,2 & 5 
So now when I boot I can start Linux Ubuntu from sda5 but choosing windows I suppose grub goes into a death spiral!!

I've tried to mend the windows installation using a vista recovery disk, the results are that windows does not find any problem with itself.

I will try an entry to the 40_custom file to try and get it to boot from sda2 in the following manner

menuentry "Windows (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 02BE8A2DBE8A1975
    drivemap -s (hd0) ${root}
    chainloader +1
}

---

### Post by tectp on 2010-05-29
Nope, still locked out of windows.

---

### Post by n1ght5t4lk3r on 2010-05-29
> **ranch hand said:**
> 

You could try plugging this into your /etc/grub.d/40_custom file;
```

menuentry "Windows (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set AE92823C928208D3
    drivemap -s (hd0) ${root}
    chainloader +1
}

```and run;
```

sudo update-grub

```and then
```

sudo grub-mkconfig

```That should give you a read out of the new grub.cfg file so you can see if the entry is in there near the bottom in the 40_custom section.
.

I am having pretty much the same issue here, installed lucid on my laptop on  an empty partition along side existing 9.04 and windows vista, everything seemed to be well, but at boot grub lists lucid (2 kernels, original from install and new one after update manager ran after install) and lists my 9.04 kernels, and the only mention of vista is the Windows Recovery Environment, 
my partitions are - 
sda1 = windows recovery environment
sda2 = windows vista
sda3=extended partition which consists of sda5+6=ubuntu 9.04 and its swap, and sda7+8 ubuntu 10.04 and its swap
I saw the above quoted code, of which I think I have to change to sda2 which is where my main vista install is, but although I can read the " /etc/grub.d/40_custom" file I cannot write anything to it, how do I go about adding this entry?

---

### Post by n1ght5t4lk3r on 2010-05-29
Actually forget my post above, after following another link I decided to try and run the Windows Recovery Environment (loader) entry from Grub at boot, thinking I would rebuild the boot rec using the bootrec.exe from command prompt, however when I selected the recovery entry it actually just booted straight into windows, so in actual fact although my Grub entry claims its windows recovery environment it is in fact Not the recovery utility, the name of the entry is listed wrongly (which of course throws up some other questions like where is my actual recovery environment...which luckily I have on a DVD anyway since my machine came with vista OEM and first thing i did was create this disc)

Anyway seems I don't actually have a problem with multi boot

---

### Post by drs305 on 2010-05-29
> **n1ght5t4lk3r said:**
> Actually forget my post above, after following another link I decided to try and run the Windows Recovery Environment (loader) entry from Grub at boot, thinking I would rebuild the boot rec using the bootrec.exe from command prompt, however when I selected the recovery entry it actually just booted straight into windows, so in actual fact although my Grub entry claims its windows recovery environment it is in fact Not the recovery utility, the name of the entry is listed wrongly (which of course throws up some other questions like where is my actual recovery environment...which luckily I have on a DVD anyway since my machine came with vista OEM and first thing i did was create this disc)

Anyway seems I don't actually have a problem with multi boot

There is a fairly simple tweak you can make to /etc/grub.d/30_os-prober to at least get the menuentry title to reflect that it is your Windows OS and not the Recovery partition. It wouldn't fix why the entry is being mis-identified but it would let you at least *see* a more correct title.

If you want to pursue this, please repost in the Grub2 Title Tweaks thread, and let me know which partition it is that contains the actual OS and what you want the title to read. The link to the Tweaks thread is in my signature line.

---

### Post by n1ght5t4lk3r on 2010-05-29
Thanks, I have bookmarked that link for later reading (is quite extensive)

---

### Post by tectp on 2010-05-30
Getting back to the origins of this thread...grub2 persists in my system preventing me from getting into windows. I have uninstalled it using synaptic, also using "apt-get --purge remove" in a terminal but as the bootscript shows it remains alive and well on my system. 
I have run the windows recovery disk and this has overwritten the mbr i suppose which again should have gotten rid of it. The only thing I can think of doing is to wipe out the linux partition where it resides and re-install my linux system from scratch. Drastic but perhaps the only way forward at this stage.

grub is a great program, but when things go wrong (my own fault i realise) there seems to be no way to wipe it off and start again without destroying your system.

---

### Post by oldfred on 2010-05-30
tectp- We have seen where with vista or 7 this can be a problem. 
/dev/sda1    *             63   142,898,174   142,898,112   7 HPFS/NTFS

The normal install starts at 2048, only installs over XP or manually created may start at 63. If the start of the partition was moved windows is lost and need repairs. I am not sure what it is that is wrong but this is a set of windows repairs.

Vista or 7 repair
Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors 
BootRec.exe /FixBoot  #updates PBR partition boot sector 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

The issue is not grub or grub2 as we have seen the partition starting at 63  and windows not working before grub2 came out.

If you installed the windows boot loader and after the repairs windows should boot. If so you can then reinstall grub2 and should be able to choose what to boot.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by tectp on 2010-05-30
> **oldfred said:**
> tectp- We have seen where with vista or 7 this can be a problem. 
/dev/sda1    *             63   142,898,174   142,898,112   7 HPFS/NTFS

The normal install starts at 2048, only installs over XP or manually created may start at 63. If the start of the partition was moved windows is lost and need repairs. I am not sure what it is that is wrong but this is a set of windows repairs.

Vista or 7 repair
Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors 
BootRec.exe /FixBoot  #updates PBR partition boot sector 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

The issue is not grub or grub2 as we have seen the partition starting at 63  and windows not working before grub2 came out.

If you installed the windows boot loader and after the repairs windows should boot. If so you can then reinstall grub2 and should be able to choose what to boot.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


Many thanks old fred..I'll do my homework and get back to you.
best regards, tectp

---

