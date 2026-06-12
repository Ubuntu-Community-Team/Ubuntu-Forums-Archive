---
title: "Severely Corrupted PC"
date: 2010-12-19
forum: General Help
---

### Post by redcape22 on 2010-12-19
Hi all,

A few days ago a friend recommended that I should dual boot ubuntu, alongside with my windows 7. I burned the boot to a blank cd, launched it up and it was fine. The GRUB boot loader worked fine also. After messing with it for a few hours, I rebooted back to windows 7 to resume my usual stuff. Then today, while trying to get back to ubuntu, there is no more GRUB. Instead, after the initial dell loading screen where I can press F2 to go to BIOS or F12 to choose from different boot options, then I get an error screen, and the only solution is to pop the disc back in and boot to ubuntu from the disc. I had installed ubuntu on its own 70 gb-ish partition. It had uninstalled itself. I only have one 1TB hard drive, and it has many files on it that would really suck to lose. I had to partition it for the ubuntu setup. My problem is currently that I am stuck without a way to get back to W7 and every time I boot to ubuntu it is as if I have loaded the disc for the first time (installations do not stay permanent at all). I am writing this post on another laptop, and currently the dualboot machine is on the desktop of ubuntu.

Please help! Thanks.

---

### Post by Rubi1200 on 2010-12-20
Hi and welcome to the forums :)

You need to use a LiveCD to boot the machine in question, choosing to try NOT install.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here so we have a better overview of the setup and can help troubleshoot the problem.

Thanks.

---

### Post by coffeecat on 2010-12-20
Hi, redcape22.

+1 to everything that Rubi1200 posted - we need the output of the bootscript. However, if this problem is what I think it might be from the information you have given, I thought I would post these two links for future reference in case my hunch is right. If my hunch is right, then you won't have lost Ubuntu. What would have happened is that some manufacturer's Windows utility has overwritten some of the grub bootloader files in the embedding area - that's a space between the partition table and the beginning of the first partition. Gory details here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

And here:

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable]("http://www.chiark.greenend.org.uk/ucgi/%7Ecjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable")

So please post details of your hardware - I see you are using a Dell which is one of the offenders - along with the output of the bootscript. Also, were you using any of the utilities in Windows listed in the first link?

---

### Post by redcape22 on 2010-12-20
Well I went to my spare PC and burned a copy of the Windows 7 Recovery Disc and did a few scans with it, and every partition is fine and the only thing wrong is the boot :P go figure. I'll get that boot info script in a jiffy.

---

### Post by redcape22 on 2010-12-20
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sde2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sde3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sde4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sde5 and 
                       looks at sector 1806471208 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63        80,324        80,262  de Dell Utility
/dev/sde2              81,920    20,238,335    20,156,416   7 HPFS/NTFS
/dev/sde3    *     20,238,336 1,763,054,260 1,742,815,925   7 HPFS/NTFS
/dev/sde4       1,763,055,614 1,953,523,711   190,468,098   5 Extended
/dev/sde5       1,813,866,496 1,947,738,111   133,871,616  83 Linux
/dev/sde6       1,947,740,160 1,953,523,711     5,783,552  82 Linux swap / Solaris
/dev/sde7       1,763,055,616 1,811,668,991    48,613,376  83 Linux
/dev/sde8       1,811,671,040 1,813,850,111     2,179,072  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sde1        3030-3030                              vfat       DellUtility                   
/dev/sde2        DA8840E38840BFAD                       ntfs       RECOVERY                      
/dev/sde3        CEE04344E04331CF                       ntfs       OS                            
/dev/sde4: PTTYPE="dos" 
/dev/sde5        613ab6b1-d050-465d-ae5e-119edab7c857   ext4                                     
/dev/sde6        2f815b64-e947-4408-b3f0-d8585ab88f97   swap                                     
/dev/sde7        e83e5c90-67bf-4ac6-9636-e7e19a232a11   ext4                                     
/dev/sde8        16455c74-23ae-4542-bcea-3f78ea3f5bed   swap                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sda: No medium found
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sde5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 613ab6b1-d050-465d-ae5e-119edab7c857
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 613ab6b1-d050-465d-ae5e-119edab7c857
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 613ab6b1-d050-465d-ae5e-119edab7c857
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=613ab6b1-d050-465d-ae5e-119edab7c857 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 613ab6b1-d050-465d-ae5e-119edab7c857
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=613ab6b1-d050-465d-ae5e-119edab7c857 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 613ab6b1-d050-465d-ae5e-119edab7c857
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 613ab6b1-d050-465d-ae5e-119edab7c857
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdf2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set da8840e38840bfad
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

=============================== sde5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdf5 during installation
UUID=613ab6b1-d050-465d-ae5e-119edab7c857 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdf6 during installation
UUID=2f815b64-e947-4408-b3f0-d8585ab88f97 none            swap    sw              0       0

=================== sde5: Location of files loaded by Grub: ===================


 933.1GB: boot/grub/core.img
 980.3GB: boot/grub/grub.cfg
 929.2GB: boot/initrd.img-2.6.35-22-generic
 933.1GB: boot/vmlinuz-2.6.35-22-generic
 929.2GB: initrd.img
 933.1GB: vmlinuz

=========================== sde7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set e83e5c90-67bf-4ac6-9636-e7e19a232a11
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set e83e5c90-67bf-4ac6-9636-e7e19a232a11
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e83e5c90-67bf-4ac6-9636-e7e19a232a11
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e83e5c90-67bf-4ac6-9636-e7e19a232a11 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e83e5c90-67bf-4ac6-9636-e7e19a232a11
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e83e5c90-67bf-4ac6-9636-e7e19a232a11 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e83e5c90-67bf-4ac6-9636-e7e19a232a11
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e83e5c90-67bf-4ac6-9636-e7e19a232a11
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sde2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set da8840e38840bfad
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sde5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 613ab6b1-d050-465d-ae5e-119edab7c857
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=613ab6b1-d050-465d-ae5e-119edab7c857 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sde5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 613ab6b1-d050-465d-ae5e-119edab7c857
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=613ab6b1-d050-465d-ae5e-119edab7c857 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sde7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde7 during installation
UUID=e83e5c90-67bf-4ac6-9636-e7e19a232a11 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde8 during installation
UUID=16455c74-23ae-4542-bcea-3f78ea3f5bed none            swap    sw              0       0

=================== sde7: Location of files loaded by Grub: ===================


 924.9GB: boot/grub/core.img
 920.1GB: boot/grub/grub.cfg
 903.6GB: boot/initrd.img-2.6.35-22-generic
 924.9GB: boot/vmlinuz-2.6.35-22-generic
 903.6GB: initrd.img
 924.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sda sdb sdc sdd sdf sdg 
```

As to why there are two linux partitions - it had tried to install twice x.x
Also, under the list of the 8 partitions, the big one is set to boot because I had tried this solution previously using gparted to edit the partition flags.

---

### Post by searchfgold6789 on 2010-12-20
There can only be 4 partitions on a hard drive. Only 1 of them can be an Extended one. Otherwise, you WILL encounter problems.
As I am aware, your MBR is having some sort of conflict. The surefire way of solving this problem is to delete every partition on your hard disk except the Windows one, move Windows all the way to the left, fix the Windows MBR from the Windows 7 DVD ("Fix Boot Problems"), and then reinstall Ubuntu.
About the Utility thing you had: You probably will not miss much - There are probably many software substitutes for whatever tools were on that partition.
Good Luck,
 - search

---

### Post by coffeecat on 2010-12-20
> **redcape22 said:**
> did a few scans with it, and every partition is fine and the only thing wrong is the boot :P go figure. 

No figuring necessary. That was exactly what I expected. :wink: All that has happened is that a Windows utility has borked the grub bootloader. Which is why I asked you what hardware you were running and whether you recognised any of the offending Windows software listed in the first link I posted. If you don't identify the culprit, this will happen again... and again... and again... every time you boot into Windows.

Now to your bootscript. The fix is easy for this issue, but I can't give you this yet because there is something odd about the bootscript. It identifies your hard drive as sde - i.e. the **fifth** detected drive. But the /etc/fstab for your partition 5 Ubuntu installation says that it was on sdf (the **sixth** drive) when installed. And then your two grub.cfg files (these are the grub bootloader config files) seem to think that everything is on what grub refers to as hd0 - the **first** drive. Which would be sda in the above terminology.

We must sort this out because the terminal commands you need to repair grub have to refer to either sda or sde, and we need to decide which. Questions: did you use a live CD or live USB to run the bootscript? Have you changed the SATA connectors to your drives/motherboard headers at any time? Have you changed any BIOS settings with regard to boot order?

Also, your script output suggests to me that we need to restore the grub menu currently on partition #5, not #7. Perhaps you could confirm this.

---

### Post by oldfred on 2010-12-20
I do not think you have to reinstall windows. It will boot fine from any primary partition. Ubuntu boots fine from any primary or logical partition. You may want to houseclean the extra install, but I keep several / (root) partitions and alternate them, as I prefer clean installs. It also is useful just as a root to install any other system to test.

Go back to Post#3, by coffeecat. There are a variety of windows programs that corrupt grub2 in the MBR (and the area after the MBR). Those areas are supposed to be used for booting, but some windows programs hide serial numbers or DRM code into that area.

---

### Post by redcape22 on 2010-12-20
Alright. I am booting from a CD which I have written the 695 MB .iso to.  I am in the Disk Utility window at the moment (under System > Admin)  and deleted the DellUtility partition. I also deleted the two linux  subpartitions under the extended drive, which were the two occasions  that ubuntu had installed (under a 25gb partition and a 69gb partition).  The 1.1 gb Unknown is the swap for the 25gb partition. 

I have not changed any SATA connectors and as far as BIOS, I was messing  around with it a bit to try to get the OS drive to boot first instead  of checking for boot media in my CD drives, and I assume that it does do  this but I still get the error, as if the boot is broken for that  drive. But the BIOS settings are still the default ones because the  default settings were the logical boot order, so BIOS is still the same  as it was.

Addition - Last night I had used system recovery from the Windows 7  Recovery Disk to try to reset the system to December 15th (Before any  Ubuntu CD was ever set in the drive) and to no avail- boot was still  broken.

Attached is a screenshot of my disk utility window, and also the gparted window.

---

### Post by coffeecat on 2010-12-20
> **redcape22 said:**
> deleted the DellUtility partition.

Why did you do that?

I see that you have also deleted **all** of your Ubuntu partitions. Why did you do that?

---

### Post by redcape22 on 2010-12-20
> **searchfgold6789 said:**
> The surefire way of solving this problem is to delete every partition on your hard disk except the Windows one

I don't want to delete the recovery partition yet if I have to, but the utility partition was listed as one of the offending things on the sourceforge wiki link you gave in post number 3 (
Dell:  Recovery Tools,    DataSafe Local Backup)


For the Ubuntu partitions- Honestly, I just want windows only for a functioning computer x.x I may try ubuntu again somewhere down the road but for now I just want what I had before.

---

### Post by coffeecat on 2010-12-20
> **redcape22 said:**
> I don't want to delete the recovery partition yet if I have to, but the utility partition was listed as one of the offending things on the sourceforge wiki link you gave in post number 3 (
Dell:  Recovery Tools,    DataSafe Local Backup)

No, I gave you that link, not searchfgold6789. In my opinion, that poster's advice to delete partitions is most unwise. The Dell utilities may be the cause of the grub problem, but deleting a whole partition that contains stuff that might be useful is like demolishing a building because it has dirty windows.

> **redcape22 said:**
>  Honestly, I just want windows only for a functioning computer

Why did you not say so in the first place? You need to run bootrec.exe /FixMbr from the command prompt of the Windows 7 repair disc. See here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you only want Windows, then the Dell utility partition definitely did not need to be deleted. The issue was only with the grub bootloader.

---

### Post by oldfred on 2010-12-20
You can use a windows repair CD to fix the windows boot loader with the command BootRec.exe /fixmbr.
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)


Easier from the Ubuntu liveCD:
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

The reason your hard drive is becoming sde or sdf is you have a multicard reader and BIOS for whatever reason is promoting each of those devices above the hard drive.

---

### Post by redcape22 on 2010-12-20
> **coffeecat said:**
> No, I gave you that link, not searchfgold6789. In my opinion, that poster's advice to delete partitions is most unwise. The Dell utilities may be the cause of the grub problem, but deleting a whole partition that contains stuff that might be useful is like demolishing a building because it has dirty windows.



Why did you not say so in the first place? You need to run bootrec.exe /FixMbr from the command prompt of the Windows 7 repair disc. See here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you only want Windows, then the Dell utility partition definitely did not need to be deleted. The issue was only with the grub bootloader.

Yea, I was referring to you giving me the link, not search :P I assume there is no way to get the utility partition back, but I didn't really need it anyways (disregarding search's statement)

---

### Post by coffeecat on 2010-12-20
The recovery partition may give you the utility partition back - but I can't guarantee it.

Good luck, and don't let this episode put you off Ubuntu. Had you wanted to restore the grub bootloader for dual-booting Windows and Ubuntu it would have been quite straightforward - and without any partition deletion :p - but nevermind.

Just keep that sourceforge link for if you ever decide to install Ubuntu on a Dell again.

Or on HP, or Samsung, or.... :(

---

### Post by redcape22 on 2010-12-20
Okay, I'm back on windows (finally! :D) but I notice a few things-

The DellUtility drive is gone (expected)
The Recovery drive is unaccessible- attempting to access it twice made it disappear completely and is now gone.

My 1tb drive is now at a capacity of 831 gb (as opposed to 980ish from before) so I'm guessing those linux partitions I had have eaten up space. Any way to get those empty partitions merged back on to the main drive? 

Edit: I went into windows' partition editor and merged the 90gb I had back into C:/, and now it's at 921gb. The 10gb recovery partition still shows up, even though it doesn't show up under Computer (listing the drives). Then there is the 40 mb partition for the utility drive, although it is unallocated now.

---

### Post by coffeecat on 2010-12-20
> **redcape22 said:**
> Edit: I went into windows' partition editor and merged the 90gb I had back into C:/, and now it's at 921gb. The 10gb recovery partition still shows up, even though it doesn't show up under Computer (listing the drives). Then there is the 40 mb partition for the utility drive, although it is unallocated now.

The various sizes are probably in gibibytes (GiB) which are base 2 (divisible by 1024), whereas the 1TB drive is 1000 gigabytes (base 10 - divisible by 1000). 1000 gigabytes is the same as 931.3 gibibytes, so that's about right.

I wonder if the hidden flag is set on the recovery partition, which would explain why you can't see it in Computer but you can in Disk Management. Is there a key press at the POST screen to get into the recovery partition?

---

### Post by searchfgold6789 on 2010-12-21
You can use Testdisk for data recovery :) It has never failed me. Ever.
Clonezilla is always the expert's first suggestion as a backup tool.
I second coffecat's post: is there still an option for it when you start the PC? Can you BIOS detect it?

---

