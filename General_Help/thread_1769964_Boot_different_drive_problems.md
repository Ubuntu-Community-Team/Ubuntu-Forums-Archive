---
title: "Boot different drive problems"
date: 2011-05-28
forum: General Help
---

### Post by aata844 on 2011-05-28
Hello,
I've had Windows 7 installed for a while on C:, obviously, on a 60 gb hard drive. I then booted into the 11.04 installer and installed it on an 80 gb internal hard drive, known to windows as F:. I restarted my computer, and it booted into Windows. So, I took a look at EasyBCD and added a NeoSmart Linux for ubuntu, but that wouldn't work. So I went over to my live USB ubuntu and mounted the 80 gb hard drive, found it was /dev/sdb, with a UUID of lets say 2e. So I ran grub-install --boot-directory=/media/2e/boot /dev/sda
/dev/sda is Windows. 
it's grub version 1.99 so I used boot-dir instead of root-dir
I reboot, and I get something like:
```
error: no such device: 2e
grub restore>
```
It seems like the Ubuntu drive isn't mounted at boot before grub runs, so it's not finding it. At least, thats my guess. No knowledge of this stuff. 
Anyone know how to fix this?

---

### Post by aata844 on 2011-05-29
Considering this forum gets new topics constantly, bump?

Also, when I boot super grub2 disk, when listing all OS's, I don't get Ubuntu, only Windows. 

Another argument that the drive isn't mounting is in super grub2 disk, when listing all partitions, it does not appear.

---

### Post by oldfred on 2011-05-29
Supergrub disk is usually very good at booting anything that is bootable.

This will show what you have installed where, run from Ubuntu liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by aata844 on 2011-05-30
It only seems to confirm my suspicions that the drive isn't mounting when the computer starts :(
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 2e26120a-754e-437d-9f78-8646ab405f20 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.01 debian-20100714 ...........>...r>..........4...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1411000 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *        286,720   117,227,519   116,940,800   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   146,480,669   146,480,607  83 Linux
/dev/sdb2         146,480,670   156,248,189     9,767,520   5 Extended
/dev/sdb5         146,480,733   156,248,189     9,767,457  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2062 MB, 2062548992 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4028416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62     4,027,519     4,027,458   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       e313c047-f9fc-4fd9-ba96-47c6dd786d72   ext3       
/dev/sda1        22B0CB5DB0CB3657                       ntfs       
/dev/sdb1        43a513fb-61a8-4e5e-8b3a-6fb31720f0a9   ext4       
/dev/sdb5        10e0b31b-175a-490f-a0a5-735fcf5c26ac   swap       
/dev/sdc1        0263-5182                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/22B0CB5DB0CB3657  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 43a513fb-61a8-4e5e-8b3a-6fb31720f0a9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 43a513fb-61a8-4e5e-8b3a-6fb31720f0a9
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 43a513fb-61a8-4e5e-8b3a-6fb31720f0a9
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=43a513fb-61a8-4e5e-8b3a-6fb31720f0a9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 43a513fb-61a8-4e5e-8b3a-6fb31720f0a9
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=43a513fb-61a8-4e5e-8b3a-6fb31720f0a9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 43a513fb-61a8-4e5e-8b3a-6fb31720f0a9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 43a513fb-61a8-4e5e-8b3a-6fb31720f0a9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 22B0CB5DB0CB3657
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=43a513fb-61a8-4e5e-8b3a-6fb31720f0a9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=10e0b31b-175a-490f-a0a5-735fcf5c26ac none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  24.134063244 = 25.913753088   boot/grub/core.img                             1
  42.412799358 = 45.540396544   boot/grub/grub.cfg                             1
   6.554717541 = 7.038074368    boot/initrd.img-2.6.38-8-generic               2
  24.132335186 = 25.911897600   boot/vmlinuz-2.6.38-8-generic                  1
   6.554717541 = 7.038074368    initrd.img                                     2
  24.132335186 = 25.911897600   vmlinuz                                        1

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```The grub on /dev/sda is from the grub-install command, sdb is where I installed ubuntu. by the way, tried reinstalling ubuntu, changed nothing.

---

### Post by Allavona on 2011-05-30
Try reinstalling Grub to the Ubuntu partition not the windows partition. Then use EasyBCD to once again make an entry for it.

---

### Post by aata844 on 2011-05-30
How is EasyBCD supposed to work? does it put the boot file on c: or on the drive its booting? First time i tried, i got a file not found error or something of the sort. anyway, ill try what you say.

and by reinstalling grub onto the ubuntu drive you mean
```
sudo grub-install --boot-directory=/media/2e26120a-754e-437d-9f78-8646ab405f20/boot /dev/sdb
```
right?

---

### Post by aata844 on 2011-05-30
sdb or sdb1? I used sdb. Now ill boot windows and do easybcd.

well sdb1 gives
```
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

```So i guess I'm sticking with sdb.

Well jesus, in windows, the ubuntu hard drive is not showing. However, in disk management, it's there, but has no drive letter. Disk management won't let me click "Change drive letters and paths".

---

### Post by oldfred on 2011-05-30
Since you have two drives, you should just have a windows boot loader in sda. The boot script showed a non-working grub2 in sda. Then you put grub2's boot loader in sdb and set BIOS to boot sdb. 

Grub will let you boot Ubuntu or windows. And if you want you can boot windows directly with BIOS or one time boot key.

If in BIOS or one time boot key you select sdb the 80GB drive, does it boot Ubuntu? Boot script looks like it should work. But sometimes it needs reinstalling of the grub2 boot loader to the MBR of sdb.

From liveCD if you cannot boot.
sudo mount /dev/sdb1 /mnt
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sdb

After rebooting
sudo update-grub

---

### Post by aata844 on 2011-05-30
The thing is, the reason I'm messing with this bootloader stuff is because I can't change to a different drive letter or /dev/sdb in the BIOS or one time boot menu.
Here, take a look at the images.
Maybe someone can tell me where I can select which drive to boot from.
[http://aata844.imgur.com/bios](http://aata844.imgur.com/bios)
By the way, couldn't take a picture or the one time boot key thing, but again, no drive letters. something like...
1. Diskette drive 
2. IDE CD-ROM
3. Hard Drive
4. Normal
5. USB flash device
6. Diagnostic
7. System recovery
8. ??
EDIT: ah, found the boot menu:
4. is IDE CD-ROM device
[IMG]http://www.majotphotography.com/TestingGrounds/Leopard.5/DSC_4167.JPG[/IMG]
> From liveCD if you cannot boot.
sudo mount /dev/sdb1 /mnt
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sdb

After rebooting
sudo update-grubAfter rebooting, where will I end up? Will the above commands let me get into Ubuntu or will I have to get into Ubuntu myself with the BIOS/one time boot key?

---

### Post by oldfred on 2011-05-30
The BIOS screens you posted do not even show a second device. Boot script showed it so I do not understand where it is. It should show as another device.

Are these both IDE drives and you only can set boot with jumpers on drive? Old IDE systems only booted primary master. Often the CD was on the secondary channel and if you have a second drive it was slave and not bootable. If that is the case you can either use grub in the MBR of sda or EasyBCD to boot windows & grub. I do not know anything about EasyBCD but some have posted it works. You still should install grub to sdb so if you change Ubuntu drive to master it would then boot.

But it looks like BIOS will let you boot a second drive. Sometimes if jumpers are not set correctly or if using cable select & jumpers are not set correctly that can cause boot issues or using cable select with 40 conductor cable.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by aata844 on 2011-06-01
I have a parallel ATA and cable select. Blue is going into the motherboard, the second one is plugged into the 80 gig, and the last one is plugged into the 60. I can't see a color difference between the two.

Where do I go from here? Grub on the primary (60 gb)?

---

### Post by oldfred on 2011-06-01
If that is the only choice then you have to install grub to the primary master or sda.

---

### Post by aata844 on 2011-06-01
I'm sorry, I'm new to Ubuntu, how should I go about installing grub on sda?

---

### Post by oldfred on 2011-06-01
Your Ubuntu install is in sdb1 but you will have to install grub2's boot loader to sda.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdb1 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sdb1 if not correct:
sudo fdisk -l
#confirm that linux is sdb1
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by aata844 on 2011-06-01
If it wants boot directory, shouldn't it be 
```
sudo grub-install --boot-directory=/mnt/boot /dev/sda/boot
```
or 
```
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```
because if you take a look [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting the Master Boot Record"), it doesn't show /dev/sda/boot but /dev/sda.

Wait wait wait, what this is doing is getting grub to boot sdb1 from sda right? But I already tried that! 
> So I ran grub-install --boot-directory=/media/2e/boot /dev/sda
/dev/sda is Windows. 
it's grub version 1.99 so I used boot-dir instead of root-dir
I reboot, and I get something like:
Code:
error: no such device: 2e
grub restore>

---

### Post by glene77is on 2011-06-01
> **aata844 said:**
> in windows, the ubuntu hard drive is not showing. However, in disk management, it's there, but has no drive letter. Disk management won't let me click "Change drive letters and paths".

Aata, 
M$ Windows may never recognize a Linux formatted HD.    Mine never have.  
Linux OS will recognize M$ and 14 other formats of HD.    

hda and sda will address the base of the device.   (this is wherre the MBR is written). 
hda1 and sda1 will address the first partition/sector of the device. (this is where files are written). 

Read OldFred,  He has been around this tree at least three times !       :smile:

HTH

---

### Post by aata844 on 2011-06-01
I guess i'll try those commands for installing grub again, worth a try. didn't work the first time.

---

### Post by oldfred on 2011-06-01
Your install is not in /media/2e/boot, so that will give an error. Your install is in /dev/sdb1.

You may have been looking at it from liveCD with a /media mount, but grub has to find the rest of its files as it boots with just the hard drives. 

If the short method does not work, then you have to do the full chroot method.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by aata844 on 2011-06-08
Alright, still, nothing works. Are there any bootloaders that let you mount drives? so i can boot into the bootloader and then boot ubuntu?

---

### Post by oldfred on 2011-06-08
did you correctly install grub2's boot loader to sda?

Sometimes you have to do the full chroot method posted above if the quick version does not work.

Rerun boot info script to see details of what you have done.

---

### Post by aata844 on 2011-06-11
I can't use the chroot method, because sda1 is windows 7.

---

### Post by oldfred on 2011-06-11
The guides are examples, you have to change the instructions to match your exact configuration. So if you install is not sda1 use what ever is.

---

### Post by aata844 on 2011-06-13
I was under the impression you wanted me to install grub2 on C: (sda) (primary hard drive). However, that is Windows. Do you want me to install grub where I installed Ubuntu?

---

### Post by oldfred on 2011-06-13
C: is a partition in Ubuntu it will be sda1 - first drive a and first partition #1. You need to install to the MBR of sda note that there is no number. 

From post #14 using liveCD:

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda

You never install grub2's boot loader to a windows partition as that overwrites code that windows has to have.

---

### Post by aata844 on 2011-06-21
Well, I tried the chroot method, which did not work. 

I swapped the drives so ubuntu (sdb) was primary, and it booted into grub, which, from there, let me boot Ubuntu and Windows. Works for me.

---

