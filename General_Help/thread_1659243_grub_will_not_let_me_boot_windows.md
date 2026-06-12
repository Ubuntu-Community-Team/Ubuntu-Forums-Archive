---
title: "grub will not let me boot windows"
date: 2011-01-03
forum: General Help
---

### Post by klirka on 2011-01-03
hello,

my new internal hard disk is 1000 gb. 

1) i installed windows 7 (running fine)
2) then i repartitioned the disk with gparted in order to free space for kubuntu (see partition table below)
3) next i installed kubuntu 10.10 (running fine)
4) but now the boot loader grub will not let me run windows any more :( . windows notifies me about an error at startup; it says it cannot access a necessary device; it wants me to insert the windows dvd, reboot and start recovery.

now i don't know:

did i trash the windows master boot record and must now start recovery from the windows dvd, as suggested by windows? 
or will it suffice to hit 'e' before booting windows, in order to edit the boot command? because, if i do that, i am given these options:

- insmod part_msdos [preselected, it seems]
- insmod ntfs
- set root='(hd0,msdos1)'
- search --no-floppy -- fs-uuid -- set [string of numbers]
- chainloader +1

or is there anything else i can do?

in case it matters, here is how i partitioned the disk: 

/dev/sda1 primary ntfs (system, windows, boot) 100mb
  -- unallocated 9mb --
/dev/sda2 primary ntfs (windows7) 687gb
/dev/sda3 primary (unformatted, for later use)
/dev/sda4 extended (containing 156 gb with these logical partitions:)
/dev/sda5 logical ext4 (linux /) 48gb
  -- unallocated 5mb --
/dev/sda6 logical ext4 (linux /home) 92gb
/dev/sda7 logical (linux swap) 14gb
  -- unallocated 39gb --
total: 1000gb

while installing kubuntu, i formatted / and /home as ext4. i was also asked to pick a device for boot loader installation, with these 6 options:

/dev/sda [apparently preselected]
/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda5
/dev/sda6

i had no clue what to do, so i did not touch this and selected /dev/sda.

i am not sure what to do.
your advice is appreciated, thank you for your help!

---

### Post by supershin on 2011-01-03
If you can boot into kubuntu run sudo update-grub. That may fix it.

---

### Post by klirka on 2011-01-04
> **supershin said:**
> If you can boot into kubuntu run sudo update-grub. That may fix it.

thank you for help. yes, kubuntu is still running fine. so i did what you suggested and ran "sudo update-grub" and received this: 

> xxx@yyy:~$ sudo update-grub
[sudo] password for xxx: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
xxx@yyy:~$

unfortunately, nothing has changed. i still cannot boot windows. 
note: i can access all my windows-files from kubuntu's file manager, so windows is still there. i just cannot boot it.

any other ideas?

---

### Post by klirka on 2011-01-05
still looking for help, thank you very much!

---

### Post by drs305 on 2011-01-05
Please tell us what happens when you select Windows and then go to the following site, download and run the boot info script, and post the RESULTS.txt so we can take a look at your boot files.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by klirka on 2011-01-05
> **drs305 said:**
> Please tell us what happens when you select Windows i already did that, please have a look at my initial problem description.

> and then go to the following site, download and run the boot info script, and post the RESULTS.txt so we can take a look at your boot files.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net") here you go:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             225,280 1,441,525,759 1,441,300,480   7 HPFS/NTFS
/dev/sda3       1,441,525,760 1,543,925,759   102,400,000  83 Linux
/dev/sda4       1,543,927,806 1,871,605,759   327,677,954   5 Extended
/dev/sda5       1,543,927,808 1,646,327,807   102,400,000  83 Linux
/dev/sda6       1,646,338,048 1,840,885,759   194,547,712  83 Linux
/dev/sda7       1,840,887,808 1,871,605,759    30,717,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D4F0A084F0A06E84                       ntfs       System-reserviert             
/dev/sda2        2CA0A42EA0A40086                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        07d84b0c-148d-4a99-8bcb-f9594df01aa3   ext4                                     
/dev/sda6        f554df13-6bbc-4097-aff0-fda228820395   ext4                                     
/dev/sda7        1ce48b06-a87c-497f-a835-053f5275c378   swap       linuxswap                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)


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
search --no-floppy --fs-uuid --set 07d84b0c-148d-4a99-8bcb-f9594df01aa3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 07d84b0c-148d-4a99-8bcb-f9594df01aa3
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 07d84b0c-148d-4a99-8bcb-f9594df01aa3
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=07d84b0c-148d-4a99-8bcb-f9594df01aa3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 07d84b0c-148d-4a99-8bcb-f9594df01aa3
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=07d84b0c-148d-4a99-8bcb-f9594df01aa3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 07d84b0c-148d-4a99-8bcb-f9594df01aa3
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=07d84b0c-148d-4a99-8bcb-f9594df01aa3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 07d84b0c-148d-4a99-8bcb-f9594df01aa3
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=07d84b0c-148d-4a99-8bcb-f9594df01aa3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 07d84b0c-148d-4a99-8bcb-f9594df01aa3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 07d84b0c-148d-4a99-8bcb-f9594df01aa3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d4f0a084f0a06e84
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
UUID=07d84b0c-148d-4a99-8bcb-f9594df01aa3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=f554df13-6bbc-4097-aff0-fda228820395 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=1ce48b06-a87c-497f-a835-053f5275c378 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 803.5GB: boot/grub/core.img
 792.8GB: boot/grub/grub.cfg
 791.5GB: boot/initrd.img-2.6.35-22-generic
 791.5GB: boot/initrd.img-2.6.35-24-generic
 803.5GB: boot/vmlinuz-2.6.35-22-generic
 803.5GB: boot/vmlinuz-2.6.35-24-generic
 791.5GB: initrd.img
 791.5GB: initrd.img.old
 803.5GB: vmlinuz
 803.5GB: vmlinuz.old


```

---

### Post by drs305 on 2011-01-05
Thanks for posting the results.

I'm not a Windows guy but it appears you have the necessary boot files/folders.

It doesn't appear to be a Grub2 problem from your description and the RESULTS.txt.

Repartitioning with non-Windows apps (even gparted) sometimes causes problems and we usually recommend you resize partitions from within Windows. That could be the cause of your problem. Did you try booting Windows after resizing and before installing Kubuntu?

If you have the Windows repair/recovery CD, it would be best to repair Windows. *oldfred* has a good series of links for that:
[http://ubuntuforums.org/showthread.php?p=9826152]("http://ubuntuforums.org/showthread.php?p=9826152")
These links concern primarily the bootloader and may help you with the partitioning issues as well.

If you want to confirm that it is not a G2 issue, you can easily restore the Windows bootload by running some commands from linux. However, this will leave you with no Kubuntu and no Windows if indeed it is a Windows issue. If you want to try that let us know.

---

### Post by klirka on 2011-01-05
> **drs305 said:**
> Thanks for posting the results.

I'm not a Windows guy but it appears you have the necessary boot files/folders.

It doesn't appear to be a Grub2 problem from your description and the RESULTS.txt.

Repartitioning with non-Windows apps (even gparted) sometimes causes problems and we usually recommend you resize partitions from within Windows. That could be the cause of your problem. Did you try booting Windows after resizing and before installing Kubuntu?
Not 100% sure, but if i remember correctly: yes, i booted into windows after resizing and before installing kubuntu.
thank you very much for your help so far! i will try the windows recovery dvd then. thank you for the links you gave me.
i might be able to restore windows this way, but i am afraid it might as well wipe out my kubuntu. let's see... :)  is there anything i should pay more attention to during my next kubuntu install then? if i made a mistake, at least i don't want to repeat it... - if i manage to recover windows, but cannot boot into kubuntu any more, what then? leave partitions as they are and start a fresh new kubuntu install? and when it takes me to the point again where i should select a device for boot loader installation, should i select /dev/sda again?

> If you have the Windows repair/recovery CD, it would be best to repair Windows. *oldfred* has a good series of links for that:
[http://ubuntuforums.org/showthread.php?p=9826152]("http://ubuntuforums.org/showthread.php?p=9826152")
These links concern primarily the bootloader and may help you with the partitioning issues as well.

If you want to confirm that it is not a G2 issue, you can easily restore the Windows bootload by running some commands from linux. However, this will leave you with no Kubuntu and no Windows if indeed it is a Windows issue. If you want to try that let us know.

---

### Post by Rubi1200 on 2011-01-05
I don't know if this is significant, but what was on sda3?
> Mounting failed:
mount: unknown filesystem type ''

---

### Post by drs305 on 2011-01-05
Get Windows working first; then:

Restoring Windows should not touch or affect your Kubuntu partitions. You should be able to boot the Ubuntu installation CD, mount your Kubuntu partition, and simply reinstall grub. That should restore the linux bootloader. 
From the LiveCD:
```
sudo mount /dev/sda5
sudo grub-install --root-directory=/mnt /dev/sda

```
Do not include the partition number in the second command.
Reboot.

When you reboot, you should either have a menu with both Kubuntu and Windows, or be booted directly into Kubuntu. 

If it boots directly, it means the initial installation didn't pickup the Windows OS. In this case, run the following command and Windows should be located and placed in the Grub menu on your next boot.
```
sudo update-grub
```

---

### Post by klirka on 2011-01-05
yaaaaaayyyyyyyy :) it worked!
i put in the windows dvd, picked "recovery". it did a short check and suggested to repair a start option. i hit "details" and from what i got, it simply replaced "Windows 7" by "Windows 7 Home Premium". i rebooted and now both windows and kubuntu are running fine, i just checked both.

i am very happy and will mark this thread as solved. 
thanks all for taking your precious time, especially drs305!

---

