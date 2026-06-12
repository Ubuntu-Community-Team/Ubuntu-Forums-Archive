---
title: "Grub2 Trouble Recognizing Win7OS"
date: 2011-06-03
forum: General Help
---

### Post by rcayea on 2011-06-03
I recently had a problem where for some reason I couldn't boot into my  computer. Long story, shorter, I just reinstalled Ubuntu and I am fine  with that. The problem now is, Grub2 doesn't recognize my windows7 hard  drive and subsequently doesn't make an option for it in the boot menu. 

My setup is this:
Hard Drive(A): 500GB Windows 7
Hard Drive(B): 320GB (no OS, formatted in NTFS and is used as storage)
Hard Drive(C): 2TB Ubuntu 11.04

The  HD that isn't being seen by Grub2 does show up on Gparted and is  accessible through Nautilus simply by clicking on the drive and it does  the usual mounting. 

I have tried reinstalling grub-pc.

**Here is one error I get that I was able to copy:**
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 129453 files and directories currently installed.)
Preparing to replace grub-pc 1.99~rc1-13ubuntu3 (using .../grub-pc_1.99~rc1-13ubuntu3_amd64.deb) ...
Unpacking replacement grub-pc ...
Processing triggers for man-db ...
Setting up grub-pc (1.99~rc1-13ubuntu3) ...
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup:  warn: Embedding is not possible.  GRUB can only be installed in this  setup by using blocklists.  However, blocklists are UNRELIABLE and their  use is discouraged..
Installation finished. No error reported.

**Here is the result of sudo parted /dev/sda unit s print**


Model: ATA Hitachi HDP72505 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End         Size        Type     File system  Flags
 1      2048s  976771071s  976769024s  primary  ntfs         boot

**And, finally, here is the result of sudo fdisk -l:**
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b799a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001189e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38914   312569856   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243202  1953514583+  ee  GPT
Thanks,
Randy

---

### Post by linuxinstalledfromhdd on 2011-06-03
You can try this:

[http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/](http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/)

---

### Post by rcayea on 2011-06-03
thanks. i'll give it a try and let you know if it works. thanks, randy

---

### Post by oldfred on 2011-06-03
If you are using gpt did you create a bios_grub partition for grub2? Are you installing grub to the 2TB drive?

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on
It only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues

Windows will only boot from gpt if you are using UEFI with 64bit windows 7.

post this so we can see your entire configuration:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by rcayea on 2011-06-03
The first offer of help (video) didn't work. Thanks, though.  

Thanks oldfred for the help. I was acutally hoping you would happen upon my question as I have seen you help others with grub difficulties.

Although I consider myself a step above beginner in the linux knowledge, I don't understand the GPT info you describe. I am sure I could just copy the commands and make it work, but I would like to know what Ia am doing, too - learn :)

Also, is it normal to use gpt? I don't recall trying to do so and based on my questions, I obviously have no idea about it. 

Thanks again and here is the output from the script:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid b66e2335-cf5d-4174-8201-729cde542c45 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 
    63576394 of the same hard drive for core.img. core.img is at this location 
    and looks for (,gpt1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   976,771,071   976,769,024   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   625,141,759   625,139,712  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdc1              34    78,125,034    78,125,001 Data partition (Windows/Linux)
/dev/sdc2   3,905,077,963 3,907,029,118     1,951,156 Swap partition (Linux)
/dev/sdc3      78,125,035 3,905,076,206 3,826,951,172 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        84D0578CD057837A                       ntfs       
/dev/sdb1        1DA7C3C2407C920E                       ntfs       cayeastorage
/dev/sdc1        9fa3e834-c803-4277-baf9-b89c96d1e515   ext4       
/dev/sdc2        635591bb-67d5-4db2-80b4-e2bfd15882d7   swap       
/dev/sdc3        be3f52a6-7b86-4793-aedf-62da7a551d16   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/84D0578CD057837A  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc3        /home                    ext4       (rw,commit=0)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(/dev/sdc,gpt1)'
search --no-floppy --fs-uuid --set=root 9fa3e834-c803-4277-baf9-b89c96d1e515
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sdc,gpt1)'
search --no-floppy --fs-uuid --set=root 9fa3e834-c803-4277-baf9-b89c96d1e515
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
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdc,gpt1)'
    search --no-floppy --fs-uuid --set=root 9fa3e834-c803-4277-baf9-b89c96d1e515
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9fa3e834-c803-4277-baf9-b89c96d1e515 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdc,gpt1)'
    search --no-floppy --fs-uuid --set=root 9fa3e834-c803-4277-baf9-b89c96d1e515
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9fa3e834-c803-4277-baf9-b89c96d1e515 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdc,gpt1)'
    search --no-floppy --fs-uuid --set=root 9fa3e834-c803-4277-baf9-b89c96d1e515
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdc,gpt1)'
    search --no-floppy --fs-uuid --set=root 9fa3e834-c803-4277-baf9-b89c96d1e515
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=9fa3e834-c803-4277-baf9-b89c96d1e515 /               ext4    errors=remount-ro 0       1
/dev/sdc3       /home           ext4    defaults        0       2
/dev/sdc2       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  30.315613747 = 32.551142400   boot/grub/core.img                             1
  24.182000160 = 25.965224960   boot/grub/grub.cfg                             1
   0.812516212 = 0.872432640    boot/initrd.img-2.6.38-8-generic               2
  30.275242805 = 32.507794432   boot/vmlinuz-2.6.38-8-generic                  1
   0.812516212 = 0.872432640    initrd.img                                     2
  30.275242805 = 32.507794432   vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error


```

---

### Post by oldfred on 2011-06-03
Your windows is missing two boot files that are normally in a boot/recovery 100MB partition. But your main install starts at the standard 2048, so you did not delete the boot partition from sda. Did you install to another drive and have the boot there?

You should just be able to repair windows in sda. The grub2 boot loader in sda refers to a partition that does not exist so it will not work. I would install a windows boot loader to sda so that sda could be booted without any other drive.

Boot flag is alread on sda1. Change BIOS to boot sda and boot a windows repairCD and run the fixBoot & fixMBR commands. You may need chkdsk also.

I have posted the instructions in post #7 and if you do not have a repairCD a link is in post#9.
oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

For gpt you just need to create another small partition with gparted and set a label bios_grub. Since it is gpt it can be any partition, so just shrink sdc3 and add a new sdc4 of about 1MB and do not format it.
It only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues.

If you have fixed windows and it boots from sda, then change BIOS to boot sdc and to boot your Ubuntu install. Reinstall grub to the MBR.

sudo grub-install /dev/sdc
sudo update-grub

Confirm that grub will reinstall on updates to sdc's hard drive by name:
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by rcayea on 2011-06-03
I'm confirming that I understand your instructions and will give them a try. thanks. i will report back.

---

### Post by srs5694 on 2011-06-04
> **rcayea said:**
> Also, is it normal to use gpt? I don't recall trying to do so and based on my questions, I obviously have no idea about it.

Ubuntu's installer seems to use MBR for disks of up to somewhere between 1 and 2 TB and then switches to GPT for larger disks. MBR's limit is 2 TiB -- that is, 2.2 TB, so the installer is using GPT when it doesn't need to. This wouldn't be a problem except that the installer doesn't give any notice about the desirability of a BIOS Boot Partition on a GPT disk.

[quote=oldfred]For gpt you just need to create another small partition with gparted and  set a label bios_grub. Since it is gpt it can be any partition, so just  shrink sdc3 and add a new sdc4 of about 1MB and do not format it.
It only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues.[/quote]

Don't shrink anything. There's a gap of 1757 sectors (878.5 KiB) between /dev/sdc3 and /dev/sdc2. (They're out of order on the disk, but that's not a problem.) Resizing partitions is always risky, and although the risk would be minimal for such a small resize operation, there's no point in taking it. (See below, though.) If for some reason GParted won't let you create a sub-1 MiB partition, use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) instead. Use the "n" option on the main menu and give the partition a type code of EF02; that's gdisk's way of identifying a BIOS Boot Partition. Be sure to use "w" to save your changes.

One further comment that's unrelated to your problem but that might be very important: Your partitions are not aligned on 4 KiB boundaries. This is fine if your disk uses traditional 512-byte sectors, but a lot of new drives, particularly at the high-capacity end of the scale, are Advanced Format models that use 4 KiB physical sectors but report that they have 512-byte sectors. Such disks suffer from [potentially severe performance problems](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) if their partitions aren't aligned along 8-sector (4 KiB) boundaries. Thus, I recommend you figure out if you've got such a disk, and if you do, correct your alignment problem. Unfortunately, not all manufacturers make this identification easy, but most have some mention of "Advanced Format" on their specifications page or other literature on their Web sites for the drives in question. Post the drive's exact model number if you need help tracking down this information.

---

### Post by rcayea on 2011-06-04
@oldfred: You were definitely correct about my WIN7 missing some files at boot folder. Eventually, I just booted into ubuntu and popped the win7 dvd in my computer and copied over some boot files to the windows hard drive. It was a complete guess and I probably did more harm than good, but the good news is, right after that, Ubuntu was able to "see" the windows hard drive. So, I guess maybe it was looking for a file that wasn't there any longer. Not sure how my windows boot files got messed up but anyway. 

@srs5694
Great knowledge you provide. Thanks a bundle. I do need help with tracking down whether or not my hard drive says anything about Advanced Format. 

Here is the model number of my 2TB Hard drive:
Hitachi HDS5C3020ALA632

Thanks-a-bunch and I'll try the paritioning without shrinking.

---

### Post by oldfred on 2011-06-04
I think you have 512. I saw one boot script so far that said 4k for physical:

> Sector size (logical/physical): 512 bytes / 512 bytes

---

### Post by srs5694 on 2011-06-04
Oldfred, the problem with Advanced Format drives (at least those on which I've seen hard data, from Western Digital and Seagate) is that they ***LIE!*** The "physical" sector size they report, and that's therefore reported by fdisk, parted, and other partitioning tools, ***is a flat-out falsehood!*** Thus, the "sector size" line you've quoted is completely meaningless. This makes it impossible to determine the true sector size from software alone; you *must* refer to the manufacturer's Web site, or perhaps documentation that came with the drive, to be sure of what you've got.

The Hitachi HDS5C3020ALA632 is part of the Deskstar 5K3000 series. Hitachi's Web page on it is at [http://www.hitachigst.com/internal-drives/desktop/deskstar/deskstar-5k3000](http://www.hitachigst.com/internal-drives/desktop/deskstar/deskstar-5k3000), and I don't see any mention there of it using Advanced Format technology. (There is a link on that page to a Hitachi white paper on Advanced Format, though.) I did a Google search and found some conflicting claims. [This post](http://forum.ncixus.com/forums/index.php?mode=showthread&msg_id=2340873&threadid=2340873&forum=103&product_id=59651&msgcount=1&overclockid=0) quotes a Hitachi customer support representative as claiming that the drive is an Advanced Format model, whereas reply #3 in [this thread](http://lime-technology.com/forum/index.php?topic=11808.0) suggests it's not. In the face of this conflicting information, I recommend you contact Hitachi yourself to clear up the confusion. OTOH, customer support representatives are often pretty clueless. It might be safer to just assume that it *is* an Advanced Format drive and repartition your disk, at least if it doesn't yet contain a lot of valuable data that you can't back up.

---

### Post by rcayea on 2011-06-04
I am actually about to partition my disk as I am reinstalling ubuntu. I have a amateur question. If the biosgrub partition I created is located on sdc4, I would select that has my "Device for boot loader installation:", correct?

Thanks,
Randy 

I will give Hitachi a call actually. I would like to know what I am working with.

---

### Post by oldfred on 2011-06-04
You do not install grub2's boot loader to a partition, but to the MBR or the 0 sector of a drive. It should be sdc and give a descrition of the hard drive not of a partition like sdc4. All BIOS boot from MBR or boot sector or the very beginning of a hard drive. With gpt & BIOS you still install to the MBR, but grub puts part of its files that you normally do not see into the bios_grub partition automatically.

---

### Post by rcayea on 2011-06-06
Thanks for the help! 

In short, I copied some windows boot files to my windows hard drive and that allowed me to boot into windows and it also appears to have allowed grub2 to "see" windows to recognize it and list it in the boot options screen at statup.

---

