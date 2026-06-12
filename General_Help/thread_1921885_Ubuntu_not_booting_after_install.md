---
title: "Ubuntu not booting after install"
date: 2012-02-07
forum: General Help
---

### Post by samitekken on 2012-02-07
Hi Everybody.
I'm a linux nubie, i have installed Ubuntu 11.10 alongside windows 7
After installation, Ubuntu didn't boot, only windows 7 boot.
 
Thanks for any Help.

---

### Post by SuaSwe on 2012-02-07
Hmm, a little bit more info will probably be required here!

How did you install Ubuntu, e.g. was it a Wubi install (within Windows) or did you install Ubuntu on a separate partition? Did the install appear to go through correctly? If you boot back into the LiveCD environment, can you see the partition where Ubuntu was installed? Is there a GRUB menu when booting with Ubuntu listed as an option? Basically, give us as much information on what you did and what happened as you possibly can. :D

---

### Post by samitekken on 2012-02-07
I installed Ubuntu in a separate partition, and the install went through correctly
when the installation was done, it asked me to restart the poc, and then to remove if there is any media, i removed the liveCd and "enter", then only windows 7 boot.
 
about the grub, i don't really know, i did boot from the liveCD again, "try ubuntu" "install ubuntu" i chose to install, and i got few options, whether i want to reinstall ubuntu, or upgrade it, or remove all systems and replace them with ubuntu....there was no advanced options for partitions!!!! i'm totally a nubie in linux.
by the way, i have kubuntu 11.10, i tried to install it, the same problem.
 
I've read on the web, that this is common problem, i just couldn't find solution.

---

### Post by samitekken on 2012-02-08
Is there any solution ? Or I should give up on ubuntu, before even trying it !!!!!

---

### Post by samitekken on 2012-02-08
Ok, I give up.

---

### Post by SuaSwe on 2012-02-08
So you mean you're not getting a menu to select other operating systems? Perhaps it's just that the timeout on the GRUB menu means it's not being displayed. What do you get if you open a Terminal window and type:

```

cat /etc/default/grub | grep TIMEOUT

```

?

---

### Post by SuaSwe on 2012-02-08
No, don't give up, giving up is for quitters. ;)

---

### Post by samitekken on 2012-02-08
you mean i boot from the LiveCd and chose "try Ubuntu" and then enter this Code:
 
cat /etc/default/grub | grep TIMEOUT
Or in another way??
 
Ok, i'll try not to give up.
Thank you.

---

### Post by SuaSwe on 2012-02-08
Oh yeah, haha, forgot that you can't boot into Ubuntu. :D Durrrrrbrain!

Anyway, I'm not able to follow your progress precisely but I think this should work: hop into LiveCD, do Try Ubuntu, go to Home Folder, then find the drive Ubuntu is installed on (will be listed to the left alongside the USB drive and the Windows drive), explore it and navigate to /etc/default/grub, double-click, and copy-paste the content here. :)

---

### Post by SuaSwe on 2012-02-08
Hang on, I'm gonna replicate the steps myself so I can advise you precisely... Hopefully. :D

---

### Post by gsgleason on 2012-02-08
Do you get the grub boot menu where you can pick between Windows and Ubuntu, or does it just boot automatically into Windows?

If the latter, then it sounds like the bootloader (grub) didn't get installed.

Go through the installation again, replacing your existing ubuntu installation.

Pay extra special attention to installing the bootloader during the install.  You want to install to the MBR.

---

### Post by SuaSwe on 2012-02-08
Yeah, might be easier to just go through gsgleason's suggestion! If you'd like to have a look at what the current install is doing though, you could have a go of logging into a LiveCD environment, opening a Terminal window (Alt+F2 then type gnome-terminal) and typing:

```

sudo fdisk -l

```

This will tell you whether there are any Linux partitions installed at all (they'll be labelled "Linux"). If there are, the problem is most likely with GRUB. As stated the GRUB file that indicates what the timeout is will be located in the Home folder > partition where Ubuntu is installed > etc > default > file called grub. Provided you have both Windows and Linux installed according to 'fdisk -l', a sample config for the timeouts that should work would be:

```

#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10

```

It might also be worth having a read of the [GRUB2 support page]("https://help.ubuntu.com/community/Grub2") for further info. :)

---

### Post by sunewbie on 2012-02-08
> **samitekken said:**
> I installed Ubuntu in a separate partition, and the install went through correctly
when the installation was done, it asked me to restart the poc, and then to remove if there is any media, i removed the liveCd and "enter", then only windows 7 boot.
 
about the grub, i don't really know, i did boot from the liveCD again, "try ubuntu" "install ubuntu" i chose to install, and i got few options, whether i want to reinstall ubuntu, or upgrade it, or remove all systems and replace them with ubuntu....there was no advanced options for partitions!!!! i'm totally a nubie in linux.
by the way, i have kubuntu 11.10, i tried to install it, the same problem.
 
I've read on the web, that this is common problem, i just couldn't find solution.

Please be patient. It can be solved. As I understand, the first time you installed Ubuntu, you have selected the third option 'something else' and created ext4 partitions. 

If this is the case then during partitioning, it asks for the location of GRUB to get installed.

The default option is OK.

Linux does not identity Drives (HDD) by names. it identifies as sdXY

sdA is first HDD, if you have 2 HDD, then second HDD is called sdB. If you insert usb drive it iss identified as sdC (if you have 2 HDD)

so sdA is the HDD and it has partitions
sdA1 (where by defaul win 7 is installed)
sdA2 is where win 7 has created backup / restore partition ( smaller size may be 10 GB or 20 GB)

Linux installs on third partition, which should be formattted to ext4. Please note if you have installed Linux on NTFS, then it may not work properly.

GRUB is a bootloader for Linux and UNIX and UNIX Like systems. So GRUB should be installed in sdA (this is where MBR is located)
Please note it is sdA and not sdA1

If you went for first option i.e. to install Ubuntu along with win 7, then installer will not ask anything and will create necessary partitions automatically. Things should work out fine. 

In your case, do you see GRUB menu which should have 3 options, 3rd being win 7 or do you directly boot into win 7 and do not see any GRUB menu. by default grub waits for 8 seconds before booting into the first option.

You can install GRUB from LIVE CD. Reinstalling also helps to restore GRUB.

If you google for 'reinstall GRUB from LIVE CD' will will find results.

Please let us know what is happening so that someone can guide you.

---

### Post by samitekken on 2012-02-08
First of all, i don't get the grub boot menu where i can pick between Windows and Ubuntu, 
it just boot automatically into Windows.
 
i have 5 partitions, in one HDD, only one. besides very small partition 100 Mb reserved for system windows. which i see it as (sda1)
sda2 is empty, i used it as swap partition
then, sda3 where windows installed and sda5, and sda6, and then sda7 which is the one where i installed ubuntu, and also made sda7 for grub i guess, i don't remember that option's name, it ask where i want to put loader for ubuntu i guess.
 
i reinstalled ubuntu 3 times in the same way, the same problem.
i also downloaded ubuntu 10.04 LTS and installed it in the same way i just described, and it worked fine, also kubuntu 10.04 worked fine, it just had some problems with sound.
 
but i still want ubuntu 11.10 if possible.
 
so why ubuntu 10.04 works well, and not ubuntu 11.10 !!!
 
i wish you can provide me with solution for this.

---

### Post by samitekken on 2012-02-08
First of all, i don't get the grub boot menu where i can pick between Windows and Ubuntu, 
it just boot automatically into Windows.
 
i have 5 partitions, in one HDD, only one. besides very small partition 100 Mb reserved for system windows. which i see it as (sda1)
sda2 is empty, i used it as swap partition
then, sda3 where windows installed and sda5, and sda6, and then sda7 which is the one where i installed ubuntu, and also made sda7 for grub i guess, i don't remember that option's name, it ask where i want to put loader for ubuntu i guess.
and partition where i installed ubuntu, it was formattted to ext4. where i had to add "/"  because when i tried to continue, it said there is no file system.
 
i reinstalled ubuntu 3 times in the same way, the same problem.
i also downloaded ubuntu 10.04 LTS and installed it in the same way i just described, and it worked fine, also kubuntu 10.04 worked fine, it just had some problems with sound.
 
but i still want ubuntu 11.10 if possible.
 
so why ubuntu 10.04 works well, and not ubuntu 11.10 !!!
 
i wish you can provide me with solution for this.

---

### Post by samitekken on 2012-02-08
> **SuaSwe said:**
> Yeah, might be easier to just go through gsgleason's suggestion! If you'd like to have a look at what the current install is doing though, you could have a go of logging into a LiveCD environment, opening a Terminal window (Alt+F2 then type gnome-terminal) and typing:
 
```

sudo fdisk -l

```This will tell you whether there are any Linux partitions installed at all (they'll be labelled "Linux"). If there are, the problem is most likely with GRUB. As stated the GRUB file that indicates what the timeout is will be located in the Home folder > partition where Ubuntu is installed > etc > default > file called grub. Provided you have both Windows and Linux installed according to 'fdisk -l', a sample config for the timeouts that should work would be:
 
```

#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10

```It might also be worth having a read of the [GRUB2 support page]("https://help.ubuntu.com/community/Grub2") for further info. :)
 
I followed the steps. the code : sudo fdisk -l
it showed the partitions labelled "Linux" , i mean for swap partition and partition where i installed ubuntu,
 
and when i checked the grub file, i got this :
 
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
# info -f grub -n 'Simple configuration'
 
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
 
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
 
# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
 
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
 
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"
 
# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by samitekken on 2012-02-08
im using ubuntu from the liveCD
i tried to update the grub using update-grub 
i got this message :

/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

---

### Post by samitekken on 2012-02-08
Is There Something Else I Could Do ?

---

### Post by oldfred on 2012-02-08
If you are directly booting Windows, you did not install the grub2 boot loader to the MBR. The MBR controls all booting.

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Often this will fix boot issues and if not please post the link to a run of the boot info script that it can run for your. Then we can give specific instructions.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by samitekken on 2012-02-08
> **oldfred said:**
> If you are directly booting Windows, you did not install the grub2 boot loader to the MBR. The MBR controls all booting.
 
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
 
Often this will fix boot issues and if not please post the link to a run of the boot info script that it can run for your. Then we can give specific instructions.
 
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.
 
 
This is the run of my boot info script:
 
 
```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 1010. But according to the info from fdisk, 
                       sda6 starts at sector 450560000.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda7 
                       and looks at sector 602235408 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    40,964,095    40,757,248  82 Linux swap / Solaris
/dev/sda3          40,966,144   245,759,999   204,793,856   7 NTFS / exFAT / HPFS
/dev/sda4         245,762,431   625,139,711   379,377,281   f W95 Extended (LBA)
/dev/sda5         245,762,433   450,558,989   204,796,557   7 NTFS / exFAT / HPFS
/dev/sda6         450,560,000   559,103,999   108,544,000   7 NTFS / exFAT / HPFS
/dev/sda7         559,106,048   625,139,711    66,033,664  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        D8C85060C8503EC6                       ntfs       Réservé au système
/dev/sda2        3ac6346d-d233-4a7a-82a8-774aae8b6608   swap       
/dev/sda3        34FC27A8FC27637A                       ntfs       FILES
/dev/sda5        8CCCF307CCF2EA7A                       ntfs       Sami DATA
/dev/sda6        68FE4AD9FE4A9EE6                       ntfs       
/dev/sda7        f66fd6c6-0132-422b-893a-10aa56e6ebb1   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/FILES             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root f66fd6c6-0132-422b-893a-10aa56e6ebb1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root f66fd6c6-0132-422b-893a-10aa56e6ebb1
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root f66fd6c6-0132-422b-893a-10aa56e6ebb1
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=f66fd6c6-0132-422b-893a-10aa56e6ebb1 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root f66fd6c6-0132-422b-893a-10aa56e6ebb1
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=f66fd6c6-0132-422b-893a-10aa56e6ebb1 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root f66fd6c6-0132-422b-893a-10aa56e6ebb1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root f66fd6c6-0132-422b-893a-10aa56e6ebb1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root D8C85060C8503EC6
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
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=f66fd6c6-0132-422b-893a-10aa56e6ebb1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=3ac6346d-d233-4a7a-82a8-774aae8b6608 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     3
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

---

### Post by oldfred on 2012-02-08
Does your Windows boot ok. It looks like you boot from sda1, but the real install is in sda6?

You installed the grub2 boot loader to the Partition Boot Sector - PBR, not the hard drive's boot sector or MBR.

Boot repair should let you reinstall grub2's boot loader to the MBR.

Or you can manually do it using liveCD. With grub2 version 1.99, the liveCD needs to be the same version.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda7 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda7 if not correct:
sudo fdisk -l
#confirm that linux is sda7
sudo mount /dev/sda7 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by samitekken on 2012-02-09
I have 100 Mb reserved for system windows 7 where the boot.ini, is that the MBR of the hard drive ?
 
something is confusing me, when i installed ubuntu 10.04 LTS and i installed the grub in the partition boot sector, as i did with 11.10, and it worked fine, even the grub wasn't in the MBR.
 
Ok i'll try to do it as you described, and i'll let you know.
Thanks.

---

### Post by oldfred on 2012-02-09
MBR is the very first sector of a hard drive. It is not part of any partition.

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

You cannot install a boot loader to a PBR or partition boot sector unless you have another boot loader that can chain load to that install. A PBR is like a MBR except it is the first sector of the partition and is not used for anything else. Windows uses the PBR and grub normally chain loads to the Windows PBR to boot Windows.

---

### Post by samitekken on 2012-02-09
The problem is solved, i used this command :
```
 sudo mount /dev/sda7 /mnt 
```

And then just to make sure, i used the second command :
```
 sudo grub-install --boot-directory=/mnt/boot /dev/sda 
```

There were  no errors on both previous commands, i rebooted, and it worked, i got boot list.

Thank you oldfred you are a genius :)

---

