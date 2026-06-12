---
title: "Cloned Ubuntu 11.10 impossible to boot (new UUIDs, updated grub and fstab...)"
date: 2012-01-26
forum: General Help
---

### Post by stonefury208 on 2012-01-26
This is day 2 of my epic struggle to make a bootable clone of my Ubuntu installation and I'm completely out of ideas at this point. 

I have one hard drive with a Windows installation and another with an Ubuntu 11.10 installation and two ntfs partitions. The second drive has developed bad sectors in its second ntfs partition, so worrying about impending drive failure I cloned the whole thing to a third new drive using ddrescue. I am now trying and failing to boot the clone. 

The original installation had separate ext4 partitions for /boot, /, and /home, and a linux-swap partition. After cloning, I set random UUID for each cloned partition. Then I mounted the cloned / and /boot drives and updated the fstab file in the cloned system with the new UUIDs. Finally, I chroot to the mounted file system and ran update-grub. Checking the grub.cfg file and comparing against the original, I confirmed that the old UUID values had changed to reflect the new random ones.

According to various forum posts and tutorials, I thought this should be enough to boot the new cloned filesystem. However, attempting to boot from the new drive for the first time, I got a nice surprise.

[IMG]https://fbcdn-sphotos-a.akamaihd.net/hphotos-ak-ash4/401267_10100472963115090_16912690_49167283_254858280_n.jpg[/IMG]

It was hard to see, but in the upper left there was a blinking white line. On subsequent attempts I haven't seen this again, but just a black screen with a blinking white line. I am unable to type anything, holding or tapping shift does nothing, ctrl-alt-del does nothing. I have to do a hard reboot to get out of it.

I tried following the flowchart in [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) to no avail. For the last step I purged and reinstalled grub on the cloned drive according to [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099). This didn't seem to help. 

The original installation still boots with no problem, so I tried running update-grub in this filesystem too. As I had hoped, this added new options at the bottom of the original grub menu to boot various Ubuntu versions it found on the / partition of the new drive. However, when I select one I get a purple screen and an error message: "no such device f32e7...." where the last number is the UUID of the cloned /boot partition. It then goes back to the menu. 

If anyone sees anything further to try, I'll give it a shot. If not, I guess I'll forget about trying to clone drives...

---

### Post by C.S.Cameron on 2012-01-26
I have cloned failing drives using the simple:

dd if=/dev/sda of=/dev/sdb

with no bs=, count=, etc.

I did this on my old laptop's XP/Ubuntu dual boot drive.

The only problem I had was that the new drive was larger than the old drive and when I tried expanding the XP partition, XP would not boot, (so I added a new NTFS partition for XP to use as storage).

I have been using the cloned drive for over 3 years now.

---

### Post by dcstar on 2012-01-27
> **stonefury208 said:**
> 
...........
The original installation still boots with no problem, so I tried running update-grub in this filesystem too. As I had hoped, this added new options at the bottom of the original grub menu to boot various Ubuntu versions it found on the / partition of the new drive. However, when I select one I get a purple screen and an error message: "no such device f32e7...." where the last number is the UUID of the cloned /boot partition. It then goes back to the menu. 

If anyone sees anything further to try, I'll give it a shot. If not, I guess I'll forget about trying to clone drives...

Double check the UUID entries in the cloned /etc/fstab - use "Copy and paste" from this terminal command to be sure you didn't make an error:

```
ls -al /dev/disk/by-uuid/
```

Ensure that there are no duplicate UUIDs.

There should be no good reason that the cloned drive won't boot after updating Grub if all of this is set up correctly.

---

### Post by stonefury208 on 2012-01-27
I will double check them, but when I updated fstab initially I copy/pasted them from gparted. So I would be surprised if there is a typo somehow. 

One thing that I thought shouldn't matter, but maybe that's my problem, I wasn't able to update the UUIDs of the ntfs partitions. At the time I thought it wouldn't matter for booting since they don't contain any system or boot files, but would UUID conflicts with ntfs storage partitions cause this?

---

### Post by oldfred on 2012-01-27
There is at least one more place where UUID is stored, but I did not think it affected booting. Grub also stores drive to reinstall to on updates which you need to update.

UUID in grub, fstab &
more /etc/initramfs-tools/conf.d/resume

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Post results.txt from boot info script:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

OR:

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration. May be better to run the git/beta version of boot script as it has some fixes.

---

### Post by stonefury208 on 2012-01-27
> There is at least one more place where UUID is stored, but I did not  think it affected booting. Grub also stores drive to reinstall to on  updates which you need to update.

UUID in grub, fstab &
more /etc/initramfs-tools/conf.d/resume

I checked the resume file and found it was still pointing to the swap partition of the old filesystem. I updated the UUID.

> #To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

I tried this in both the original filesystem and chrooted into the mounted clone. I notice that it is not using UUIDs. In the former case, it points to /dev/disk/by-id/ata-ST9500420AS_5VJ47BXY. Here ST...AS is the model number of the drive. In the cloned system, it points to /dev/disk/by-id/usb-BUFFALO_External_HDD_000000003A20C6AB-0:0. I don't know about the numbers but it is a Buffalo drive that contains the cloned system. So I think this is already correct?

> Post results.txt from boot info script:

I tried running the script both from the working filesystem and chrooted into the cloned system / partition. In the latter case, it could only find the / partition. I'm not sure if that's normal. From the working filesystem, I got this:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Windows is installed in the MBR of /dev/sdc.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /BOOTMGR /Boot/BCD 
                       /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    40,965,749    40,963,702  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     40,965,750   285,153,749   244,188,000   7 NTFS / exFAT / HPFS
/dev/sda3         285,153,750   976,768,064   691,614,315   f W95 Extended (LBA)
/dev/sda5         285,153,813   976,768,064   691,614,252   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       585,727       583,680  83 Linux
/dev/sdb2         488,366,080   976,768,064   488,401,985   7 NTFS / exFAT / HPFS
/dev/sdb3             587,774   488,359,734   487,771,961   f W95 Extended (LBA)
/dev/sdb5             587,776    20,117,503    19,529,728  83 Linux
/dev/sdb6          20,119,552    27,930,623     7,811,072  82 Linux swap / Solaris
/dev/sdb7          27,932,672    86,523,903    58,591,232  83 Linux
/dev/sdb8          98,576,384   488,359,734   389,783,351   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   976,751,999   976,751,937   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048       585,727       583,680  83 Linux
/dev/sdd2         488,366,080   976,768,064   488,401,985   7 NTFS / exFAT / HPFS
/dev/sdd3             587,774   488,359,734   487,771,961   f W95 Extended (LBA)
/dev/sdd5             587,776    20,117,503    19,529,728  83 Linux
/dev/sdd6          20,119,552    27,930,623     7,811,072  82 Linux swap / Solaris
/dev/sdd7          27,932,672    86,523,903    58,591,232  83 Linux
/dev/sdd8          98,576,384   488,359,734   389,783,351   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3C98-AC5D                              vfat       RECOVERY
/dev/sda2        92FC48C3FC48A2F9                       ntfs       OS
/dev/sda5        CA7401CAE1930D70                       ntfs       DATA
/dev/sdb1        f5bf9df9-77d5-419c-84e4-e359c8ebc267   ext4       
/dev/sdb2        60A4ED2DA4ED05FE                       ntfs       iSDATA2
/dev/sdb5        7d41ce76-4e2a-470c-80f6-65730cfe9055   ext4       
/dev/sdb6        fee9e5d8-7854-4784-9a3d-0c49b18d5ca9   swap       
/dev/sdb7        1dd7661f-c5dd-4093-a10b-e1e7ea2911cd   ext4       
/dev/sdb8        01CCCFFB829697B0                       ntfs       iSDATA
/dev/sdc1        4CE2545CE2544C78                       ntfs       My Book
/dev/sdd1        f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2   ext4       sdc1
/dev/sdd2        60A4ED2DA4ED05FE                       ntfs       iSDATA2
/dev/sdd5        10914a45-eee2-44bf-94e3-e545b28e4d52   ext4       sdc5
/dev/sdd6        d5bb9714-b093-4c39-ac4b-81b54e1aa50a   swap       
/dev/sdd7        40e4d34b-4232-44c4-855e-9c4e19467852   ext4       sdc7
/dev/sdd8        01CCCFFB829697B0                       ntfs       iSDATA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /boot                    ext4       (rw,commit=0)
/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb7        /home                    ext4       (rw,commit=0)
/dev/sdc1        /media/My Book           ntfs       (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)
/dev/sdd1        /media/sdc1              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /mnt/boot                ext4       (rw)
/dev/sdd2        /media/iSDATA2           ntfs       (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)
/dev/sdd5        /media/sdc5              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd5        /mnt                     ext4       (rw)
/dev/sdd7        /media/sdc7              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd8        /media/iSDATA            ntfs       (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)


============================= sdb1/grub/grub.cfg: ==============================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root 7d41ce76-4e2a-470c-80f6-65730cfe9055
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
  set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux    /vmlinuz-3.0.0-15-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /vmlinuz-3.0.0-15-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux    /vmlinuz-3.0.0-14-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /vmlinuz-3.0.0-14-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux    /vmlinuz-3.0.0-12-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 3c98-ac5d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 92FC48C3FC48A2F9
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

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.022944450 = 0.024636416    grub/core.img                                  1
   0.144538879 = 0.155197440    grub/grub.cfg                                  1
   0.047224045 = 0.050706432    initrd.img-3.0.0-12-generic                    2
   0.094175339 = 0.101120000    initrd.img-3.0.0-14-generic                    3
   0.156427383 = 0.167962624    initrd.img-3.0.0-15-generic                    2
   0.017034531 = 0.018290688    vmlinuz-3.0.0-12-generic                       1
   0.022896767 = 0.024585216    vmlinuz-3.0.0-14-generic                       1
   0.081512451 = 0.087523328    vmlinuz-3.0.0-15-generic                       2

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root 7d41ce76-4e2a-470c-80f6-65730cfe9055
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
  set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux    /vmlinuz-3.0.0-15-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /vmlinuz-3.0.0-15-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux    /vmlinuz-3.0.0-14-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /vmlinuz-3.0.0-14-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux    /vmlinuz-3.0.0-12-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 3c98-ac5d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 92FC48C3FC48A2F9
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=f5bf9df9-77d5-419c-84e4-e359c8ebc267 /boot           ext4    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=1dd7661f-c5dd-4093-a10b-e1e7ea2911cd /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=fee9e5d8-7854-4784-9a3d-0c49b18d5ca9 none            swap    sw              0       0

/dev/sg1 /media/cdrom0 udf,iso9660 users,noauto,uid=0,gid=46,mode=0777,dmode=0777,nosuid,noexec 0 0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.302241325 = 0.324529152    boot/grub/core.img                             1
   0.423835754 = 0.455090176    boot/grub/grub.cfg                             1
   0.326520920 = 0.350599168    boot/initrd.img-3.0.0-12-generic               2
   0.373472214 = 0.401012736    boot/initrd.img-3.0.0-14-generic               3
   0.435724258 = 0.467855360    boot/initrd.img-3.0.0-15-generic               2
   0.296331406 = 0.318183424    boot/vmlinuz-3.0.0-12-generic                  1
   0.302193642 = 0.324477952    boot/vmlinuz-3.0.0-14-generic                  1
   0.360809326 = 0.387416064    boot/vmlinuz-3.0.0-15-generic                  2
   0.435724258 = 0.467855360    initrd.img                                     2
   0.373472214 = 0.401012736    initrd.img.old                                 3
   0.360809326 = 0.387416064    vmlinuz                                        2
   0.302193642 = 0.324477952    vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 10 24 00  |.X.MSDOS5.0...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  76 0e 71 02 0f 4e 00 00  00 00 00 00 02 00 00 00  |v.q..N..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 5d ac 98 3c 4e  4f 20 4e 41 4d 45 20 20  |..)]..<NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

Unknown BootLoader on sda3

00000000  eb 58 90 46 52 44 4f 53  34 2e 31 00 02 10 20 00  |.X.FRDOS4.1... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 d6 19 ff 10  |........?.......|
00000020  3b 8b 38 01 08 27 00 00  00 00 00 00 12 05 00 00  |;.8..'..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f2 2c 9e 58 4e  4f 20 4e 41 4d 45 20 20  |..).,.XNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fc fa 29 c0 8e d8  |  FAT32   ..)...|
00000060  bd 00 7c b8 e0 1f 8e c0  89 ee 89 ef b9 00 01 f3  |..|.............|
00000070  a5 ea 7a 7c e0 1f 00 00  60 00 8e d8 8e d0 8d 66  |..z|....`......f|
00000080  e0 fb 88 56 40 be c1 7d  e8 f4 00 66 31 c0 66 89  |...V@..}...f1.f.|
00000090  46 44 8b 46 0e 66 03 46  1c 66 89 46 48 66 89 46  |FD.F.f.F.f.FHf.F|
000000a0  4c 66 8b 46 10 66 f7 6e  24 66 01 46 4c b8 00 02  |Lf.F.f.n$f.FL...|
000000b0  3b 46 0b 74 08 01 c0 ff  06 34 7d eb f3 66 8b 46  |;F.t.....4}..f.F|
000000c0  2c 66 50 e8 94 00 72 4d  c4 5e 76 e8 b7 00 31 ff  |,fP...rM.^v...1.|
000000d0  b9 0b 00 be f1 7d f3 a6  74 15 83 c7 20 83 e7 e0  |.....}..t... ...|
000000e0  3b 7e 0b 75 eb 4a 75 e0  66 58 e8 34 00 eb d2 26  |;~.u.Ju.fX.4...&|
000000f0  ff 75 09 26 ff 75 0f 66  58 29 db 66 50 e8 5a 00  |.u.&.u.fX).fP.Z.|
00000100  72 0d e8 80 00 4a 75 fa  66 58 e8 14 00 eb ec 8a  |r....Ju.fX......|
00000110  5e 40 ff 6e 76 be ee 7d  e8 64 00 30 e4 cd 16 cd  |^@.nv..}.d.0....|
00000120  19 06 57 53 89 c7 c1 e7  02 50 8b 46 0b 48 21 c7  |..WS.....P.F.H!.|
00000130  58 66 c1 e8 07 66 03 46  48 bb 00 20 8e c3 29 db  |Xf...f.FH.. ..).|
00000140  66 3b 46 44 74 07 66 89  46 44 e8 38 00 26 80 65  |f;FDt.f.FD.8.&.e|
00000150  03 0f 26 66 8b 05 5b 5f  07 c3 66 3d f8 ff ff 0f  |..&f..[_..f=....|
00000160  73 15 66 48 66 48 66 0f  b6 56 0d 66 52 66 f7 e2  |s.fHfHf..V.fRf..|
00000170  66 5a 66 03 46 4c c3 f9  c3 31 db b4 0e cd 10 ac  |fZf.FL...1......|
00000180  3c 00 75 f5 c3 52 56 57  66 50 89 e7 6a 00 6a 00  |<.u..RVWfP..j.j.|
00000190  66 50 06 53 6a 01 6a 10  89 e6 8a 56 40 b4 42 cd  |fP.Sj.j....V@.B.|
000001a0  13 89 fc 66 58 73 08 50  30 e4 cd 13 58 eb d9 66  |...fXs.P0...X..f|
000001b0  40 03 5e 0b 73 07 8c c2  80 c6 10 8e c2 5f 00 fe  |@.^.s........_..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 2c 32 39 29 00 00  |......?...,29)..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb3

00000000  84 2b 64 e3 6b 12 d4 71  38 21 0c 4d fe f6 f7 ef  |.+d.k..q8!.M....|
00000010  df 7e 0a d7 4a 85 b4 10  2f e8 55 e4 0b 16 84 2e  |.~..J.../.U.....|
00000020  b8 c8 82 5d 5e 56 82 93  c0 bb 4a 49 12 48 06 b9  |...]^V....JI.H..|
00000030  35 12 d5 07 ca e8 9d ef  19 2b 5c 32 56 52 92 79  |5........+\2VR.y|
00000040  04 57 ff d8 1e 39 e2 85  59 9d 8a 4d 72 68 42 21  |.W...9..Y..MrhB!|
00000050  ed f0 d1 bd 03 35 c7 fb  2c 9d 2f ee fc c2 af b0  |.....5..,./.....|
00000060  e1 06 4f 28 3c 69 2d 94  85 a3 c9 55 b5 2f d7 fc  |..O(<i-....U./..|
00000070  6c 3b c0 4a f6 c2 36 6d  00 cf 5d bf 9e ea e3 dd  |l;.J..6m..].....|
00000080  5c 63 b3 7a 53 a7 45 dd  9e e4 a9 22 66 a3 ef 84  |\c.zS.E...."f...|
00000090  f5 58 bf 2b b3 bb 84 b7  6d 83 c2 1d 6d 85 29 15  |.X.+....m...m.).|
000000a0  84 13 60 49 61 59 96 74  e5 d3 9c 1c b4 e6 44 a9  |..`IaY.t......D.|
000000b0  b8 b2 b8 62 8d d3 77 a6  7a 75 e5 51 6a f9 90 a5  |...b..w.zu.Qj...|
000000c0  8d 26 6c 3b 6e 9f 26 3b  fb 15 27 26 d5 89 d6 89  |.&l;n.&;..'&....|
000000d0  d7 12 db 3b f4 c4 88 d8  a4 d6 82 76 1d 03 f2 b6  |...;.......v....|
000000e0  e8 03 0c 52 47 d0 f0 75  dc 72 a6 e4 d9 13 63 78  |...RG..u.r....cx|
000000f0  14 a5 cd 34 8a 10 5c 72  9d 6c 1d f8 3a 79 a8 91  |...4..\r.l..:y..|
00000100  e8 2d d8 4a 76 ab 3f 6d  51 fa 65 dc 7b b3 0c 79  |.-.Jv.?mQ.e.{..y|
00000110  54 a4 4a a8 79 33 f7 57  e4 94 97 2c ba ab aa 41  |T.J.y3.W...,...A|
00000120  c2 f3 85 d1 d5 24 3d 83  0c 33 ee 47 eb a3 2d 9d  |.....$=..3.G..-.|
00000130  77 cb ea aa 59 31 ea ef  f1 f3 6c 9d 82 83 4d 52  |w...Y1....l...MR|
00000140  2b 4c 82 84 a3 b2 18 52  a9 06 7a 48 09 74 f8 00  |+L.....R..zH.t..|
00000150  df 4d 12 c9 4d b2 48 5d  05 5b be 7f 2c 63 71 98  |.M..M.H].[..,cq.|
00000160  e3 84 4c fc e7 a2 b1 96  f3 de 3e 6a ed b6 6d 25  |..L.......>j..m%|
00000170  aa ad 46 79 2a e1 3d 92  cf 25 3a a7 9f 01 c0 6b  |..Fy*.=..%:....k|
00000180  a9 40 f0 b6 ed da 03 95  fa 1a 9b 24 b9 66 85 8b  |.@.........$.f..|
00000190  a1 f0 a9 e9 7a 9a cd 95  e5 6d f9 64 5d c5 d9 65  |....z....m.d]..e|
000001a0  3d 83 4c 98 cf 8d dc e2  91 ed 2c 51 54 da 1e a4  |=.L.......,QT...|
000001b0  e3 39 b9 94 f0 9d 41 72  c7 41 8c 10 b6 ba 00 95  |.9....Ar.A......|
000001c0  32 24 83 fe ff ff 02 00  00 00 00 00 2a 01 00 fe  |2$..........*...|
000001d0  ff ff 05 fe ff ff 02 00  2a 01 00 38 77 00 00 00  |........*..8w...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdd3

00000000  84 2b 64 e3 6b 12 d4 71  38 21 0c 4d fe f6 f7 ef  |.+d.k..q8!.M....|
00000010  df 7e 0a d7 4a 85 b4 10  2f e8 55 e4 0b 16 84 2e  |.~..J.../.U.....|
00000020  b8 c8 82 5d 5e 56 82 93  c0 bb 4a 49 12 48 06 b9  |...]^V....JI.H..|
00000030  35 12 d5 07 ca e8 9d ef  19 2b 5c 32 56 52 92 79  |5........+\2VR.y|
00000040  04 57 ff d8 1e 39 e2 85  59 9d 8a 4d 72 68 42 21  |.W...9..Y..MrhB!|
00000050  ed f0 d1 bd 03 35 c7 fb  2c 9d 2f ee fc c2 af b0  |.....5..,./.....|
00000060  e1 06 4f 28 3c 69 2d 94  85 a3 c9 55 b5 2f d7 fc  |..O(<i-....U./..|
00000070  6c 3b c0 4a f6 c2 36 6d  00 cf 5d bf 9e ea e3 dd  |l;.J..6m..].....|
00000080  5c 63 b3 7a 53 a7 45 dd  9e e4 a9 22 66 a3 ef 84  |\c.zS.E...."f...|
00000090  f5 58 bf 2b b3 bb 84 b7  6d 83 c2 1d 6d 85 29 15  |.X.+....m...m.).|
000000a0  84 13 60 49 61 59 96 74  e5 d3 9c 1c b4 e6 44 a9  |..`IaY.t......D.|
000000b0  b8 b2 b8 62 8d d3 77 a6  7a 75 e5 51 6a f9 90 a5  |...b..w.zu.Qj...|
000000c0  8d 26 6c 3b 6e 9f 26 3b  fb 15 27 26 d5 89 d6 89  |.&l;n.&;..'&....|
000000d0  d7 12 db 3b f4 c4 88 d8  a4 d6 82 76 1d 03 f2 b6  |...;.......v....|
000000e0  e8 03 0c 52 47 d0 f0 75  dc 72 a6 e4 d9 13 63 78  |...RG..u.r....cx|
000000f0  14 a5 cd 34 8a 10 5c 72  9d 6c 1d f8 3a 79 a8 91  |...4..\r.l..:y..|
00000100  e8 2d d8 4a 76 ab 3f 6d  51 fa 65 dc 7b b3 0c 79  |.-.Jv.?mQ.e.{..y|
00000110  54 a4 4a a8 79 33 f7 57  e4 94 97 2c ba ab aa 41  |T.J.y3.W...,...A|
00000120  c2 f3 85 d1 d5 24 3d 83  0c 33 ee 47 eb a3 2d 9d  |.....$=..3.G..-.|
00000130  77 cb ea aa 59 31 ea ef  f1 f3 6c 9d 82 83 4d 52  |w...Y1....l...MR|
00000140  2b 4c 82 84 a3 b2 18 52  a9 06 7a 48 09 74 f8 00  |+L.....R..zH.t..|
00000150  df 4d 12 c9 4d b2 48 5d  05 5b be 7f 2c 63 71 98  |.M..M.H].[..,cq.|
00000160  e3 84 4c fc e7 a2 b1 96  f3 de 3e 6a ed b6 6d 25  |..L.......>j..m%|
00000170  aa ad 46 79 2a e1 3d 92  cf 25 3a a7 9f 01 c0 6b  |..Fy*.=..%:....k|
00000180  a9 40 f0 b6 ed da 03 95  fa 1a 9b 24 b9 66 85 8b  |.@.........$.f..|
00000190  a1 f0 a9 e9 7a 9a cd 95  e5 6d f9 64 5d c5 d9 65  |....z....m.d]..e|
000001a0  3d 83 4c 98 cf 8d dc e2  91 ed 2c 51 54 da 1e a4  |=.L.......,QT...|
000001b0  e3 39 b9 94 f0 9d 41 72  c7 41 8c 10 b6 ba 00 95  |.9....Ar.A......|
000001c0  32 24 83 fe ff ff 02 00  00 00 00 00 2a 01 00 fe  |2$..........*...|
000001d0  ff ff 05 fe ff ff 02 00  2a 01 00 38 77 00 00 00  |........*..8w...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
boot_info_script.sh: line 2457: cd: /media/sdc1
/mnt/boot/: No such file or directory
boot_info_script.sh: line 2457: cd: /media/sdc5
/mnt/: No such file or directory

```

sda has the Windows system, sdb has the working Ubuntu, sdc is a  storage drive and sdd contains the cloned Ubuntu. 

sdb1 is /boot, sdb5 is / and sdb6 is swap

sdd should be analogous but I notice that no boot files are found on sdd1 or sdd5 by the script, while they are found in sdb1 and sdb5. I can mount sdd5 and sdd1 though and see all the grub files.

---

### Post by dcstar on 2012-01-27
> **stonefury208 said:**
> 
.........
One thing that I thought shouldn't matter, but maybe that's my problem, I wasn't able to update the UUIDs of the ntfs partitions. At the time I thought it wouldn't matter for booting since they don't contain any system or boot files, but would UUID conflicts with ntfs storage partitions cause this?

This will allow you to change NTFS UUIDs:

[http://ubuntuforums.org/showpost.php?p=10042585&postcount=17](http://ubuntuforums.org/showpost.php?p=10042585&postcount=17)

---

### Post by dcstar on 2012-01-27
> **stonefury208 said:**
> I checked the resume file and found it was still pointing to the swap partition of the old filesystem. I updated the UUID.
............
I tried running the script both from the working filesystem and chrooted into the cloned system / partition. In the latter case, it could only find the / partition. I'm not sure if that's normal. From the working filesystem, I got this:

```
                  Boot Info Script 0.60    from 17 May 2011
.........

```


There don't seem to be any Grub entries for the cloned partitions.

What is reported when you do this on the "normal" Ubuntu system:

```
sudo update-grub
```

---

### Post by Quackers on 2012-01-27
It appears that none of the Ubuntu systems are showing on the cloned drive.
It may be worth trying to clone again with something like clonezilla.

---

### Post by stonefury208 on 2012-01-27
> This will allow you to change NTFS UUIDs:

[http://ubuntuforums.org/showpost.php...5&postcount=17]("http://ubuntuforums.org/showpost.php?p=10042585&postcount=17")

Thanks, I'll look into this.

> There don't seem to be any Grub entries for the cloned partitions.

What is reported when you do this on the "normal" Ubuntu system:

 	Code:
 	sudo update-grub 


Funny, now that you mention it... I had done this before and it had added options to the menu to boot from the cloned / partition (Ubuntu on sdd5). But recently those menu entries have disappeared. I'll try again and see what happens.

---

### Post by oldfred on 2012-01-27
If you see files but script cannot mount them and see the files, then that probably is the same with grub not being able to mount them and find its boot files.

Separate issue. Does Windows work? Windows is not case sensitive and should see this in sda2 as the same and get very confused.

/bootmgr /BOOTMGR

---

### Post by stonefury208 on 2012-01-27
Thanks for the suggestions so far.

sudo update-grub yields:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-15-generic
Found initrd image: /boot/initrd.img-3.0.0-15-generic
Found linux image: /boot/vmlinuz-3.0.0-14-generic
Found initrd image: /boot/initrd.img-3.0.0-14-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Ubuntu 11.10 (11.10) on /dev/sdc5
done

```

Note that I disconnected the storage drive that had been sdc so now sdc5 is now the location of the cloned filesystem / partition.

Running the bash script again gives this output:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /BOOTMGR /Boot/BCD 
                       /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    40,965,749    40,963,702  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     40,965,750   285,153,749   244,188,000   7 NTFS / exFAT / HPFS
/dev/sda3         285,153,750   976,768,064   691,614,315   f W95 Extended (LBA)
/dev/sda5         285,153,813   976,768,064   691,614,252   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       585,727       583,680  83 Linux
/dev/sdb2         488,366,080   976,768,064   488,401,985  17 Hidden NTFS / HPFS
/dev/sdb3             587,774   488,359,734   487,771,961   f W95 Extended (LBA)
/dev/sdb5             587,776    20,117,503    19,529,728  83 Linux
/dev/sdb6          20,119,552    27,930,623     7,811,072  82 Linux swap / Solaris
/dev/sdb7          27,932,672    86,523,903    58,591,232  83 Linux
/dev/sdb8          98,576,384   488,359,734   389,783,351   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048       585,727       583,680  83 Linux
/dev/sdc2         488,366,080   976,768,064   488,401,985   7 NTFS / exFAT / HPFS
/dev/sdc3             587,774   488,359,734   487,771,961   f W95 Extended (LBA)
/dev/sdc5             587,776    20,117,503    19,529,728  83 Linux
/dev/sdc6          20,119,552    27,930,623     7,811,072  82 Linux swap / Solaris
/dev/sdc7          27,932,672    86,523,903    58,591,232  83 Linux
/dev/sdc8          98,576,384   488,359,734   389,783,351   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3C98-AC5D                              vfat       RECOVERY
/dev/sda2        92FC48C3FC48A2F9                       ntfs       OS
/dev/sda5        CA7401CAE1930D70                       ntfs       DATA
/dev/sdb1        f5bf9df9-77d5-419c-84e4-e359c8ebc267   ext4       
/dev/sdb2        60A4ED2DA4ED05FE                       ntfs       iSDATA2
/dev/sdb5        7d41ce76-4e2a-470c-80f6-65730cfe9055   ext4       
/dev/sdb6        fee9e5d8-7854-4784-9a3d-0c49b18d5ca9   swap       
/dev/sdb7        1dd7661f-c5dd-4093-a10b-e1e7ea2911cd   ext4       
/dev/sdb8        01CCCFFB829697B0                       ntfs       iSDATA
/dev/sdc1        f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2   ext4       sdc1
/dev/sdc2        60A4ED2DA4ED05FE                       ntfs       iSDATA2
/dev/sdc5        10914a45-eee2-44bf-94e3-e545b28e4d52   ext4       sdc5
/dev/sdc6        d5bb9714-b093-4c39-ac4b-81b54e1aa50a   swap       
/dev/sdc7        40e4d34b-4232-44c4-855e-9c4e19467852   ext4       sdc7
/dev/sdc8        01CCCFFB829697B0                       ntfs       iSDATA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /boot                    ext4       (rw,commit=0)
/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb7        /home                    ext4       (rw,commit=0)
/dev/sdc1        /media/sdc1              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc2        /media/iSDATA2           ntfs       (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)
/dev/sdc5        /media/sdc5              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc7        /media/sdc7              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc8        /media/iSDATA            ntfs       (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)


============================= sdb1/grub/grub.cfg: ==============================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root 7d41ce76-4e2a-470c-80f6-65730cfe9055
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
  set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux    /vmlinuz-3.0.0-15-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /vmlinuz-3.0.0-15-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux    /vmlinuz-3.0.0-14-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /vmlinuz-3.0.0-14-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux    /vmlinuz-3.0.0-12-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 3c98-ac5d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 92FC48C3FC48A2F9
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-15-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux /vmlinuz-3.0.0-15-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro quiet splash vt.handoff=7
    initrd /initrd.img-3.0.0-15-generic
}
menuentry "Ubuntu, with Linux 3.0.0-15-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux /vmlinuz-3.0.0-15-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro recovery nomodeset
    initrd /initrd.img-3.0.0-15-generic
}
menuentry "Ubuntu, with Linux 3.0.0-14-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux /vmlinuz-3.0.0-14-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro quiet splash vt.handoff=7
    initrd /initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-14-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux /vmlinuz-3.0.0-14-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro recovery nomodeset
    initrd /initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux /vmlinuz-3.0.0-12-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro quiet splash vt.handoff=7
    initrd /initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux /vmlinuz-3.0.0-12-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro recovery nomodeset
    initrd /initrd.img-3.0.0-12-generic
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

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.022944450 = 0.024636416    grub/core.img                                  1
   0.143075943 = 0.153626624    grub/grub.cfg                                  1
   0.047224045 = 0.050706432    initrd.img-3.0.0-12-generic                    2
   0.094175339 = 0.101120000    initrd.img-3.0.0-14-generic                    3
   0.156427383 = 0.167962624    initrd.img-3.0.0-15-generic                    2
   0.017034531 = 0.018290688    vmlinuz-3.0.0-12-generic                       1
   0.022896767 = 0.024585216    vmlinuz-3.0.0-14-generic                       1
   0.081512451 = 0.087523328    vmlinuz-3.0.0-15-generic                       2

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root 7d41ce76-4e2a-470c-80f6-65730cfe9055
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
  set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux    /vmlinuz-3.0.0-15-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /vmlinuz-3.0.0-15-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux    /vmlinuz-3.0.0-14-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /vmlinuz-3.0.0-14-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux    /vmlinuz-3.0.0-12-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f5bf9df9-77d5-419c-84e4-e359c8ebc267
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 3c98-ac5d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 92FC48C3FC48A2F9
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-15-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux /vmlinuz-3.0.0-15-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro quiet splash vt.handoff=7
    initrd /initrd.img-3.0.0-15-generic
}
menuentry "Ubuntu, with Linux 3.0.0-15-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux /vmlinuz-3.0.0-15-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro recovery nomodeset
    initrd /initrd.img-3.0.0-15-generic
}
menuentry "Ubuntu, with Linux 3.0.0-14-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux /vmlinuz-3.0.0-14-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro quiet splash vt.handoff=7
    initrd /initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-14-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux /vmlinuz-3.0.0-14-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro recovery nomodeset
    initrd /initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux /vmlinuz-3.0.0-12-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro quiet splash vt.handoff=7
    initrd /initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux /vmlinuz-3.0.0-12-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro recovery nomodeset
    initrd /initrd.img-3.0.0-12-generic
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=7d41ce76-4e2a-470c-80f6-65730cfe9055 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=f5bf9df9-77d5-419c-84e4-e359c8ebc267 /boot           ext4    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=1dd7661f-c5dd-4093-a10b-e1e7ea2911cd /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=fee9e5d8-7854-4784-9a3d-0c49b18d5ca9 none            swap    sw              0       0

/dev/sg1 /media/cdrom0 udf,iso9660 users,noauto,uid=0,gid=46,mode=0777,dmode=0777,nosuid,noexec 0 0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.302241325 = 0.324529152    boot/grub/core.img                             1
   0.422372818 = 0.453519360    boot/grub/grub.cfg                             1
   0.326520920 = 0.350599168    boot/initrd.img-3.0.0-12-generic               2
   0.373472214 = 0.401012736    boot/initrd.img-3.0.0-14-generic               3
   0.435724258 = 0.467855360    boot/initrd.img-3.0.0-15-generic               2
   0.296331406 = 0.318183424    boot/vmlinuz-3.0.0-12-generic                  1
   0.302193642 = 0.324477952    boot/vmlinuz-3.0.0-14-generic                  1
   0.360809326 = 0.387416064    boot/vmlinuz-3.0.0-15-generic                  2
   0.435724258 = 0.467855360    initrd.img                                     2
   0.373472214 = 0.401012736    initrd.img.old                                 3
   0.360809326 = 0.387416064    vmlinuz                                        2
   0.302193642 = 0.324477952    vmlinuz.old                                    1

============================= sdc1/grub/grub.cfg: ==============================

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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 10914a45-eee2-44bf-94e3-e545b28e4d52
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos1)'
  search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
  set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux    /vmlinuz-3.0.0-15-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /vmlinuz-3.0.0-15-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux    /vmlinuz-3.0.0-14-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /vmlinuz-3.0.0-14-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux    /vmlinuz-3.0.0-12-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 3c98-ac5d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 92FC48C3FC48A2F9
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

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.017084122 = 0.018343936    grub/core.img                                  1
   0.142594337 = 0.153109504    grub/grub.cfg                                  1
   0.047224045 = 0.050706432    initrd.img-3.0.0-12-generic                    2
   0.094175339 = 0.101120000    initrd.img-3.0.0-14-generic                    3
   0.074615479 = 0.080117760    initrd.img-3.0.0-15-generic                    3
   0.017034531 = 0.018290688    vmlinuz-3.0.0-12-generic                       1
   0.022896767 = 0.024585216    vmlinuz-3.0.0-14-generic                       1
   0.048310280 = 0.051872768    vmlinuz-3.0.0-15-generic                       3

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=10914a45-eee2-44bf-94e3-e545b28e4d52 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=f32e78a0-ecdf-4684-9ba9-e51bb8bb44a2 /boot           ext4    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=40e4d34b-4232-44c4-855e-9c4e19467852 /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=d5bb9714-b093-4c39-ac4b-81b54e1aa50a none            swap    sw              0       0

/dev/sg1 /media/cdrom0 udf,iso9660 users,noauto,uid=0,gid=46,mode=0777,dmode=0777,nosuid,noexec 0 0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.435724258 = 0.467855360    initrd.img                                     2
   0.373472214 = 0.401012736    initrd.img.old                                 3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 10 24 00  |.X.MSDOS5.0...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  76 0e 71 02 0f 4e 00 00  00 00 00 00 02 00 00 00  |v.q..N..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 5d ac 98 3c 4e  4f 20 4e 41 4d 45 20 20  |..)]..<NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

Unknown BootLoader on sda3

00000000  eb 58 90 46 52 44 4f 53  34 2e 31 00 02 10 20 00  |.X.FRDOS4.1... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 d6 19 ff 10  |........?.......|
00000020  3b 8b 38 01 08 27 00 00  00 00 00 00 12 05 00 00  |;.8..'..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f2 2c 9e 58 4e  4f 20 4e 41 4d 45 20 20  |..).,.XNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fc fa 29 c0 8e d8  |  FAT32   ..)...|
00000060  bd 00 7c b8 e0 1f 8e c0  89 ee 89 ef b9 00 01 f3  |..|.............|
00000070  a5 ea 7a 7c e0 1f 00 00  60 00 8e d8 8e d0 8d 66  |..z|....`......f|
00000080  e0 fb 88 56 40 be c1 7d  e8 f4 00 66 31 c0 66 89  |...V@..}...f1.f.|
00000090  46 44 8b 46 0e 66 03 46  1c 66 89 46 48 66 89 46  |FD.F.f.F.f.FHf.F|
000000a0  4c 66 8b 46 10 66 f7 6e  24 66 01 46 4c b8 00 02  |Lf.F.f.n$f.FL...|
000000b0  3b 46 0b 74 08 01 c0 ff  06 34 7d eb f3 66 8b 46  |;F.t.....4}..f.F|
000000c0  2c 66 50 e8 94 00 72 4d  c4 5e 76 e8 b7 00 31 ff  |,fP...rM.^v...1.|
000000d0  b9 0b 00 be f1 7d f3 a6  74 15 83 c7 20 83 e7 e0  |.....}..t... ...|
000000e0  3b 7e 0b 75 eb 4a 75 e0  66 58 e8 34 00 eb d2 26  |;~.u.Ju.fX.4...&|
000000f0  ff 75 09 26 ff 75 0f 66  58 29 db 66 50 e8 5a 00  |.u.&.u.fX).fP.Z.|
00000100  72 0d e8 80 00 4a 75 fa  66 58 e8 14 00 eb ec 8a  |r....Ju.fX......|
00000110  5e 40 ff 6e 76 be ee 7d  e8 64 00 30 e4 cd 16 cd  |^@.nv..}.d.0....|
00000120  19 06 57 53 89 c7 c1 e7  02 50 8b 46 0b 48 21 c7  |..WS.....P.F.H!.|
00000130  58 66 c1 e8 07 66 03 46  48 bb 00 20 8e c3 29 db  |Xf...f.FH.. ..).|
00000140  66 3b 46 44 74 07 66 89  46 44 e8 38 00 26 80 65  |f;FDt.f.FD.8.&.e|
00000150  03 0f 26 66 8b 05 5b 5f  07 c3 66 3d f8 ff ff 0f  |..&f..[_..f=....|
00000160  73 15 66 48 66 48 66 0f  b6 56 0d 66 52 66 f7 e2  |s.fHfHf..V.fRf..|
00000170  66 5a 66 03 46 4c c3 f9  c3 31 db b4 0e cd 10 ac  |fZf.FL...1......|
00000180  3c 00 75 f5 c3 52 56 57  66 50 89 e7 6a 00 6a 00  |<.u..RVWfP..j.j.|
00000190  66 50 06 53 6a 01 6a 10  89 e6 8a 56 40 b4 42 cd  |fP.Sj.j....V@.B.|
000001a0  13 89 fc 66 58 73 08 50  30 e4 cd 13 58 eb d9 66  |...fXs.P0...X..f|
000001b0  40 03 5e 0b 73 07 8c c2  80 c6 10 8e c2 5f 00 fe  |@.^.s........_..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 2c 32 39 29 00 00  |......?...,29)..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb3

00000000  84 2b 64 e3 6b 12 d4 71  38 21 0c 4d fe f6 f7 ef  |.+d.k..q8!.M....|
00000010  df 7e 0a d7 4a 85 b4 10  2f e8 55 e4 0b 16 84 2e  |.~..J.../.U.....|
00000020  b8 c8 82 5d 5e 56 82 93  c0 bb 4a 49 12 48 06 b9  |...]^V....JI.H..|
00000030  35 12 d5 07 ca e8 9d ef  19 2b 5c 32 56 52 92 79  |5........+\2VR.y|
00000040  04 57 ff d8 1e 39 e2 85  59 9d 8a 4d 72 68 42 21  |.W...9..Y..MrhB!|
00000050  ed f0 d1 bd 03 35 c7 fb  2c 9d 2f ee fc c2 af b0  |.....5..,./.....|
00000060  e1 06 4f 28 3c 69 2d 94  85 a3 c9 55 b5 2f d7 fc  |..O(<i-....U./..|
00000070  6c 3b c0 4a f6 c2 36 6d  00 cf 5d bf 9e ea e3 dd  |l;.J..6m..].....|
00000080  5c 63 b3 7a 53 a7 45 dd  9e e4 a9 22 66 a3 ef 84  |\c.zS.E...."f...|
00000090  f5 58 bf 2b b3 bb 84 b7  6d 83 c2 1d 6d 85 29 15  |.X.+....m...m.).|
000000a0  84 13 60 49 61 59 96 74  e5 d3 9c 1c b4 e6 44 a9  |..`IaY.t......D.|
000000b0  b8 b2 b8 62 8d d3 77 a6  7a 75 e5 51 6a f9 90 a5  |...b..w.zu.Qj...|
000000c0  8d 26 6c 3b 6e 9f 26 3b  fb 15 27 26 d5 89 d6 89  |.&l;n.&;..'&....|
000000d0  d7 12 db 3b f4 c4 88 d8  a4 d6 82 76 1d 03 f2 b6  |...;.......v....|
000000e0  e8 03 0c 52 47 d0 f0 75  dc 72 a6 e4 d9 13 63 78  |...RG..u.r....cx|
000000f0  14 a5 cd 34 8a 10 5c 72  9d 6c 1d f8 3a 79 a8 91  |...4..\r.l..:y..|
00000100  e8 2d d8 4a 76 ab 3f 6d  51 fa 65 dc 7b b3 0c 79  |.-.Jv.?mQ.e.{..y|
00000110  54 a4 4a a8 79 33 f7 57  e4 94 97 2c ba ab aa 41  |T.J.y3.W...,...A|
00000120  c2 f3 85 d1 d5 24 3d 83  0c 33 ee 47 eb a3 2d 9d  |.....$=..3.G..-.|
00000130  77 cb ea aa 59 31 ea ef  f1 f3 6c 9d 82 83 4d 52  |w...Y1....l...MR|
00000140  2b 4c 82 84 a3 b2 18 52  a9 06 7a 48 09 74 f8 00  |+L.....R..zH.t..|
00000150  df 4d 12 c9 4d b2 48 5d  05 5b be 7f 2c 63 71 98  |.M..M.H].[..,cq.|
00000160  e3 84 4c fc e7 a2 b1 96  f3 de 3e 6a ed b6 6d 25  |..L.......>j..m%|
00000170  aa ad 46 79 2a e1 3d 92  cf 25 3a a7 9f 01 c0 6b  |..Fy*.=..%:....k|
00000180  a9 40 f0 b6 ed da 03 95  fa 1a 9b 24 b9 66 85 8b  |.@.........$.f..|
00000190  a1 f0 a9 e9 7a 9a cd 95  e5 6d f9 64 5d c5 d9 65  |....z....m.d]..e|
000001a0  3d 83 4c 98 cf 8d dc e2  91 ed 2c 51 54 da 1e a4  |=.L.......,QT...|
000001b0  e3 39 b9 94 f0 9d 41 72  c7 41 8c 10 b6 ba 00 95  |.9....Ar.A......|
000001c0  32 24 83 fe ff ff 02 00  00 00 00 00 2a 01 00 fe  |2$..........*...|
000001d0  ff ff 05 fe ff ff 02 00  2a 01 00 38 77 00 00 00  |........*..8w...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdc3

00000000  84 2b 64 e3 6b 12 d4 71  38 21 0c 4d fe f6 f7 ef  |.+d.k..q8!.M....|
00000010  df 7e 0a d7 4a 85 b4 10  2f e8 55 e4 0b 16 84 2e  |.~..J.../.U.....|
00000020  b8 c8 82 5d 5e 56 82 93  c0 bb 4a 49 12 48 06 b9  |...]^V....JI.H..|
00000030  35 12 d5 07 ca e8 9d ef  19 2b 5c 32 56 52 92 79  |5........+\2VR.y|
00000040  04 57 ff d8 1e 39 e2 85  59 9d 8a 4d 72 68 42 21  |.W...9..Y..MrhB!|
00000050  ed f0 d1 bd 03 35 c7 fb  2c 9d 2f ee fc c2 af b0  |.....5..,./.....|
00000060  e1 06 4f 28 3c 69 2d 94  85 a3 c9 55 b5 2f d7 fc  |..O(<i-....U./..|
00000070  6c 3b c0 4a f6 c2 36 6d  00 cf 5d bf 9e ea e3 dd  |l;.J..6m..].....|
00000080  5c 63 b3 7a 53 a7 45 dd  9e e4 a9 22 66 a3 ef 84  |\c.zS.E...."f...|
00000090  f5 58 bf 2b b3 bb 84 b7  6d 83 c2 1d 6d 85 29 15  |.X.+....m...m.).|
000000a0  84 13 60 49 61 59 96 74  e5 d3 9c 1c b4 e6 44 a9  |..`IaY.t......D.|
000000b0  b8 b2 b8 62 8d d3 77 a6  7a 75 e5 51 6a f9 90 a5  |...b..w.zu.Qj...|
000000c0  8d 26 6c 3b 6e 9f 26 3b  fb 15 27 26 d5 89 d6 89  |.&l;n.&;..'&....|
000000d0  d7 12 db 3b f4 c4 88 d8  a4 d6 82 76 1d 03 f2 b6  |...;.......v....|
000000e0  e8 03 0c 52 47 d0 f0 75  dc 72 a6 e4 d9 13 63 78  |...RG..u.r....cx|
000000f0  14 a5 cd 34 8a 10 5c 72  9d 6c 1d f8 3a 79 a8 91  |...4..\r.l..:y..|
00000100  e8 2d d8 4a 76 ab 3f 6d  51 fa 65 dc 7b b3 0c 79  |.-.Jv.?mQ.e.{..y|
00000110  54 a4 4a a8 79 33 f7 57  e4 94 97 2c ba ab aa 41  |T.J.y3.W...,...A|
00000120  c2 f3 85 d1 d5 24 3d 83  0c 33 ee 47 eb a3 2d 9d  |.....$=..3.G..-.|
00000130  77 cb ea aa 59 31 ea ef  f1 f3 6c 9d 82 83 4d 52  |w...Y1....l...MR|
00000140  2b 4c 82 84 a3 b2 18 52  a9 06 7a 48 09 74 f8 00  |+L.....R..zH.t..|
00000150  df 4d 12 c9 4d b2 48 5d  05 5b be 7f 2c 63 71 98  |.M..M.H].[..,cq.|
00000160  e3 84 4c fc e7 a2 b1 96  f3 de 3e 6a ed b6 6d 25  |..L.......>j..m%|
00000170  aa ad 46 79 2a e1 3d 92  cf 25 3a a7 9f 01 c0 6b  |..Fy*.=..%:....k|
00000180  a9 40 f0 b6 ed da 03 95  fa 1a 9b 24 b9 66 85 8b  |.@.........$.f..|
00000190  a1 f0 a9 e9 7a 9a cd 95  e5 6d f9 64 5d c5 d9 65  |....z....m.d]..e|
000001a0  3d 83 4c 98 cf 8d dc e2  91 ed 2c 51 54 da 1e a4  |=.L.......,QT...|
000001b0  e3 39 b9 94 f0 9d 41 72  c7 41 8c 10 b6 ba 00 95  |.9....Ar.A......|
000001c0  32 24 83 fe ff ff 02 00  00 00 00 00 2a 01 00 fe  |2$..........*...|
000001d0  ff ff 05 fe ff ff 02 00  2a 01 00 38 77 00 00 00  |........*..8w...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```

It seems update-grub forced it to recognize boot files to sdc1 (/boot) and sdc5 (/), but sdc5 shows only fstab while sdb5 (the original system /) shows fstab and grub.cfg and core.img. I would guess this is because sdb1 is currently mounted as /boot within sdb5, whereas sdc1 and sdc5 are currently mounted as separate (not nested) partitions within /media. 

(By the way, minor tangent but how can I get it to stop auto-mounting these on boot?)

---

### Post by oldfred on 2012-01-27
No, it is more like grub2 is not properly installed in sdc. A install of grub puts the grub2 boot loader in the MBR, creates a core.img and puts a core.img in the sectors just after the MBR, and creates the grub.cfg menu.

When you copied, did you copy drive or each partition?

---

### Post by Rebelli0us on 2012-01-27
> **oldfred said:**
> No, it is more like grub2 is not properly installed in sdc. A install of grub puts the grub2 boot loader in the MBR, creates a core.img and puts a core.img in the sectors just after the MBR, and creates the grub.cfg menu.

When you copied, did you copy drive or each partition?

I think he copied the whole drive, partitions and all on a larger disk with possibly different geometry. I think if he just did a new install and then copied over the files it would work.

---

### Post by oldfred on 2012-01-27
I think these type of issues are not uncommon, although I have seen some where they are able to clone relatively easily. But UUID issues, grub, fstab and other settings become difficult to track down. 

I prefer a new drive should get a new install. It then has housecleaned all cruft that accumulates. Then you can copy /home over. If desired you can still review any system settings in /etc & copy those. I normally export  a list of installed apps as part of my normal backup, so it is relatively easy to reinstall all apps. But that does require High Speed Internet to make it relatively easy.

---

### Post by stonefury208 on 2012-01-27
Well, rebooting after update-grub did the same thing as before. Still black screen with blinking cursor if I try to boot from sdc, and still a blank purple screen if I select Ubuntu on sdc from the sdb grub menu. 

I think I am leaning now toward the last couple suggestions to just do a new install and copy the home folder over. It may actually be necessary at this point, because the damaged sdb drive is now hanging and making angry sounds when I try to boot that system. Windows on sda still boots fine for now. If I can copy the sdb home folder files in liveCD to some free storage space, then I will do a new installation on sdc and move them to that. 

Thanks to everyone for your input.

---

### Post by stonefury208 on 2012-01-27
Well first I attempted to just reformat and reinstall the old /boot, /, swap and /home partitions, but it still wouldn't boot. I kept getting kicked back to the ASUS screen just when it looked like it was about to give me a grub menu. So the problem must have something to do with the cloned partition table itself rather than individual partitions, or the presence of the ntfs partitions. I tried again with a new partition table (abandoning the ntfs partitions) and now I am booted into a new installation on the new drive. 

As for moving the old home folder, it occurred to me that there are a lot of hidden folders related to specific packages that had been installed on the old system. It seems like I could risk configuration problems if I just replace the new home folder with the old one? So I think I will opt or caution and just move specific folders like downloads, pictures, etc.

---

### Post by C.S.Cameron on 2012-01-27
I recall that to get everything when copying a home folder you must use **rsync** and not **copy**.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by oldfred on 2012-01-28
A default /home is small and easy to back up, if you want to save the new settings for any reason.

I also like rsync for copying data over. I use it for backup of my /home.
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

---

