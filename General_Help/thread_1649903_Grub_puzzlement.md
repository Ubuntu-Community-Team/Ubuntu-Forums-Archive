---
title: "Grub puzzlement"
date: 2010-12-20
forum: General Help
---

### Post by T.J. on 2010-12-20
Something I thought I'd post and see if there were any wizards out there with insight. I've been using Linux for over a decade, so no need to worry about the obvious.  I'm positive that I have my partitions/install correct.

What has me baffled is that Fedora 14, which uses GRUB 0.97 (GRUB legacy) - boots Windows flawlessly every single time on the same hardware, but Ubuntu's (or the upstream Debian's) GRUB legacy do not - even though they are based on the same upstream code from the GNU Savannah servers.  No matter what I've tried I cannot get the Debian or Ubuntu version of GRUB/GRUB-legacy to boot any recent Windows 64 beyond XP (Vista or 7).  All that it does is resets the computer when Windows attempts to boot, without an error.

GRUB is notoriously difficult to compile, so before I try to compile code from RedHat's archives - any thoughts,experiences, similar issues - whatever?

---

### Post by Rubi1200 on 2010-12-21
Just out of curiosity, run the boot info script linked at the bottom of my post.

Copy/paste the results back here so we can take a closer look at your setup.

Thanks.

---

### Post by T.J. on 2010-12-21
Thank you, Rubi1200.  I'll do so, but it might be a day or so.  I'm tied up with other things at the moment.  I'd appreciate any thoughts you can offer, as this problem has baffled me for some while. 

I simply ignored the issue by using the Windows BCD bootloader, but I'd personally prefer not to depend on Windows for loading, and if at the same time we could improve Ubuntu - all the better! :D

---

### Post by Rubi1200 on 2010-12-22
You don't mention which version of Ubuntu you are using, but if it is anything after 9.04 it will be using GRUB2.

The reason I want to see the results of the script is because there may be a conflict between the 2 versions of GRUB.

Post when you have the time and I will keep an eye on the thread.

---

### Post by psusi on 2010-12-22
Stop using grub legacy and switch to grub2 ;)

---

### Post by T.J. on 2010-12-23
Hello again, Rubi1200.  

Here is the information you asked for.  This is a fresh install, for the purposes of nailing this down.  Ubuntu boots fine, Windows does not, exhibiting the same behaviour I mentioned.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => Windows is installed in the MBR of /dev/sdc

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

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb2: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

system-os: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

system-swap: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

system-home: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,953,521,663 1,953,314,816   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       321,299       321,237  83 Linux
/dev/sdb2             321,300   625,137,344   624,816,045  8e Linux LVM


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 2,930,274,303 2,930,272,256   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/system-home 326f0535-d5d7-4be2-8e3c-514fcbea17fb   ext4                                     
/dev/mapper/system-os f869d99d-a1e7-402b-94d1-48f99a14a3ae   ext4                                     
/dev/mapper/system-swap 41121ca6-b086-4c10-9182-1b6ea778a378   swap                                     
/dev/sda1        AC0C7F170C7EDBB0                       ntfs       System Reserved               
/dev/sda2        00F8828AF8827DA2                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5a8397aa-02a9-4685-bc60-fbfbc806fb61   ext4                                     
/dev/sdb2        kgimDn-79Pd-navS-4596-cKnS-L5QD-8wdwjV LVM2_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        320658F60658BC93                       ntfs       Backup                        
/dev/sdc: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
system-home
system-os
system-swap

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/system-os /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /boot                    ext4       (rw,commit=0)
/dev/mapper/system-home /home                    ext4       (rw,commit=0)


============================= sdb1/grub/grub.cfg: =============================

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

insmod lvm
insmod part_msdos
insmod ext2
set root='(system-os)'
search --no-floppy --fs-uuid --set f869d99d-a1e7-402b-94d1-48f99a14a3ae
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 5a8397aa-02a9-4685-bc60-fbfbc806fb61
set locale_dir=($root)/grub/locale
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 5a8397aa-02a9-4685-bc60-fbfbc806fb61
	linux	/vmlinuz-2.6.35-24-generic root=/dev/mapper/system-os ro   quiet splash
	initrd	/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 5a8397aa-02a9-4685-bc60-fbfbc806fb61
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/vmlinuz-2.6.35-24-generic root=/dev/mapper/system-os ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 5a8397aa-02a9-4685-bc60-fbfbc806fb61
	linux	/vmlinuz-2.6.32-21-generic root=/dev/mapper/system-os ro   quiet splash
	initrd	/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 5a8397aa-02a9-4685-bc60-fbfbc806fb61
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/vmlinuz-2.6.32-21-generic root=/dev/mapper/system-os ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 5a8397aa-02a9-4685-bc60-fbfbc806fb61
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 5a8397aa-02a9-4685-bc60-fbfbc806fb61
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ac0c7f170c7edbb0
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

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-21-generic
    .0GB: initrd.img-2.6.35-24-generic
    .0GB: vmlinuz-2.6.32-21-generic
    .0GB: vmlinuz-2.6.35-24-generic

============================= system-os/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/system-os /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=5a8397aa-02a9-4685-bc60-fbfbc806fb61 /boot           ext4    defaults        0       2
/dev/mapper/system-home /home           ext4    defaults        0       2
/dev/mapper/system-swap none            swap    sw              0       0

================= system-os: Location of files loaded by Grub: =================


    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

---

### Post by psusi on 2010-12-23
I think that the problem is that you are booting from sdb, so when grub hands off to windows, it tries to find itself on sdb, but it is on sda.  Reinstall grub on sda, and change your bios boot order to boot from that drive.

---

### Post by T.J. on 2010-12-23
> **psusi said:**
> I think that the problem is that you are booting from sdb, so when grub hands off to windows, it tries to find itself on sdb, but it is on sda.  Reinstall grub on sda, and change your bios boot order to boot from that drive.

Thank you very much for the reply, Psusi! :)  

I'm afraid I've already tried that with both Grub-legacy and Grub 2 to no avail.  Grub 2 searches for  partitions by ID so that usually not the problem.  I've also programmed the parameter file by hand for both Grubs with no success.  Attempting to boot Windows from Grub causes the machine to reset.  The only version of Grub that I've found able to boot Windows 64 Vista/7 in the last few years was Fedora 14's version of Grub-legacy.

---

### Post by psusi on 2010-12-23
The issue is with windows rather than grub.  The windows boot sector always assumes it is on the first disk, so it gets messed up when the bios boots from the other disk, thereby treating it as the first, then windows is looking for itself on the wrong disk.  You can either fix this by changing the bios boot order to actually boot from the windows disk, or by using the grub map command to fool windows into thinking that it's disk is really the first, then it will correctly find itself.

---

### Post by oldfred on 2010-12-23
I do not have Win7 so I do not know all the details of the BCD. But with boot.ini the boot script would show the drive & partition that windows thinks it is installed on. The script does not parse the BCD hive. 
So what does the BCD show?

You have a windows boot loader in sdc but windows in sda. Does your system boot windows if you boot from sdc? That may mean the BCD is not drive 0??

How was grub legacy booting windows. Was it booting sda1 or chainloading to the MBR of sdc?

---

### Post by psusi on 2010-12-23
> **oldfred said:**
> 
How was grub legacy booting windows. Was it booting sda1 or chainloading to the MBR of sdc?

It was probably using the map command.

---

### Post by T.J. on 2010-12-25
Happy Holidays, everyone, and thank you so much for taking the time to comment. :D


I'm afraid if it were as simple the suggestions, I wouldn't have bothered anyone.  I've installed Grub and Grub 2 in the MBR on /dev/sda exactly as recommended using Ubuntu, Debian, and Fedora. They all do the same by default.  I've been over the GRUB configurations by hand.  I've mapped drives and configured BIOS until I've run out of ideas.


I'm afraid that Fedora is the only one that successfully boots Windows for me.  The only difference between Ubuntu's setup and Fedora's is the fact that Fedora uses the older version of GRUB. I've tried Ubuntu's version (called GRUB legacy) and it fails every time, even using Fedora's configuration to boot Windows.  


This suggests to me that Fedora has patched GRUB in some way.  Does anyone have any successful Ubuntu GRUB configurations that they can share?  Maybe that will help.

---

### Post by psusi on 2010-12-26
Did you compare the windows entries in menu.lst?  Did they use the map command?

---

### Post by T.J. on 2010-12-27
Hi, Psusi!  Hope you had a great Holiday!

> **psusi said:**
> Did you compare the windows entries in menu.lst?  Did they use the map command?

Not when installed on the sda device, no. I read the menu.list very carefully.

rootnoverify (hd0,0)
chainloader +1

As far as I know, this should work, but I've been unable to boot Windows on my hardware, except using Fedora.

---

### Post by oldfred on 2010-12-27
All grub does is jump to the partition boot sector and then windows loads just as if it had use the MBR with windows boot loader to jump to the partition boot sector or Fedora's grub legacy. Grub2 does seem to do some additional checking that valid windows code it there to jump to, so it can recover if not.

You can try this in 40_custom

# Chainload another bootloader
menuentry "Chainload winodws partition 1" {
set root=(hd0,1)
chainloader +1
}

gksudo gedit /etc/grub.d/40_custom
Then:
sudo update-grub


Which leaves out the extra modules. If that does not work, then something in windows changed from your install of Fedora to your install of Ubuntu. I would then try windows repairs. We often see that chkdsk, boot sector rebuild or replacing the boot programs in the windows partition repairs it.

oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

---

### Post by psusi on 2010-12-28
> **T.J. said:**
> Hi, Psusi!  Hope you had a great Holiday!



Not when installed on the sda device, no. I read the menu.list very carefully.

rootnoverify (hd0,0)
chainloader +1

As far as I know, this should work, but I've been unable to boot Windows on my hardware, except using Fedora.

That won't work because your bios is booting from sdb instead of sda, making sda, which has windows on it, hd1 instead of hd0, and windows doesn't like that.

---

### Post by T.J. on 2010-12-29
Hi, Psusi! :D

> **psusi said:**
> That won't work because your bios is booting from sdb instead of sda, making sda, which has windows on it, hd1 instead of hd0, and windows doesn't like that.

Yes, I know. I know you need to have Windows first in order or map the drive.  What I'm trying to say is that even when it is first in order, this did not work. I'm thinking it's a software flaw. Fedora's patched version seems to work, but Ubuntu's does not.

---

### Post by psusi on 2010-12-30
> **T.J. said:**
> Hi, Psusi! :D



Yes, I know. I know you need to have Windows first in order or map the drive.  What I'm trying to say is that even when it is first in order, this did not work. I'm thinking it's a software flaw. Fedora's patched version seems to work, but Ubuntu's does not.

When was it first in order?  Can you try that again?  You will need to reinstall grub on sda for it to be bootable.

---

### Post by T.J. on 2010-12-30
> **psusi said:**
> When was it first in order?  Can you try that again?  You will need to reinstall grub on sda for it to be bootable.

Hi, Psusi!  Of course! :D I've tried that actually, but I tried again a just few days ago with the latest version of Ubuntu. I ended up having to restore the Windows MBR. I suspect someone might say just use "alien" to convert the package from an RPM, but in my experience at least - that leads to dependency problems. 

I suspect that the only practical way that I'll have a chance to solve this problem is to take the Fedora 14 SRPMS package and compile it myself. I just hate the idea because compiling GRUB from source is a real pain. I've never been fond of SRPMS, and I would rather use Debian's packaging.  


I think I'll set up a VirtualBox instance, make sure the source builds cleanly on Fedora, then bring it over and then recompile it on Ubuntu. Would you be interested in knowing the results?

---

### Post by psusi on 2010-12-30
I'd be more interested in figuring out why the Ubuntu package doesn't work when the Windows drive is the boot drive ;)

If you could make that drive the bios boot device and run grub-install /dev/sda, and then post the bootinfo script results again if it still fails to boot windows, it would give me something to work with.

---

### Post by T.J. on 2011-10-22
While I don't believe in resurrecting dead threads, I thought I'd post the solution in case someone else ever has the same problem.

It turned out that Grub 2 simply does not like some older motherboards.  After switching to a newer hardware, it works flawlessly.  I'd suggest that if anyone else cannot get Grub 2 to dualboot Windows - don't use it.

Use Grub 1 (grub-legacy) instead on older hardware.

---

### Post by coffeecat on 2011-10-22
@T.J., thanks for posting your discovery. That is a most interesting and useful finding.

> **T.J. said:**
> While I don't believe in resurrecting dead threads,

Indeed! :)

I'll close this one, but if anyone else has an issue of grub2 with old motherboards, or needs help with installing legacy grub to replace grub2, please start your own support thread, linking back to this one if necessary.

Thread closed.

---

