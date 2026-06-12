---
title: "Help! Ubuntu won't boot."
date: 2011-09-27
forum: General Help
---

### Post by Will1978 on 2011-09-27
I'm from a Windows background so please accept my apologies in advance if I don't understand some Linux terminology.

I've been successfully using Ubuntu 11.04 64 bit for a month.

When I installed Ubuntu I used a new SSD for Ubuntu and removed the old hard drive with Windows 7 - placing the Windows 7 drive in an eSATA enclosure.

Today I had to boot Windows 7 again - by plugging in the drive in enclosure to the eSATA port and changing the BIOS boot order to boot from the Windows 7 drive - this glitched at first then went fine and I was able to boot Windows 7.

After I shut down and unplugged the Windows 7 drive and tried to boot as normal using Ubuntu things went horribly, horribly wrong.

First Grub came up - this is the first time I've seen Grub when booting my machine - it used to just boot directly into Ubuntu. Then I selected Ubuntu and got:

init: failed to spawn hostname main process: unable to execute: input/output error

General error mounting filesystems.

I tried booting from the Ubuntu CD and used the Install -> Update option to try to fix the problem (I'd guessed that some files had become corrupt and that the update option would hopefully overwrite the corrupt files with new ones).

Unfortunately, this seemed to fail and made things worse - now I get the following when I try to boot:

BusyBox V1.17.1... built-in-shell

initramfs

I've no idea what this is or what to do.

When I run the Ubuntu installation software now it says that there is no operating system on the drive.

I began to sense that I was in the claws of defeat so I decided to boot again from the Ubuntu CD and try to make a copy of all the data I needed to keep from the SSD so that I could then reinstall Ubuntu from scratch. I was able to copy my documents correctly but when I tried to copy the files for some VirtualBox VMs I'd created I was refused permission to copy the files.

Do I have any hope of rescuing my Ubuntu installation?

If not, how do I avoid the permissions problem when copying my files to another drive before reinstalling from scratch?

I've no idea why things went so badly wrong - any advice is very gratefully accepted.

The hardware I'm using (a Samsung laptop) is only a few months old and the SSD from a good manufacturer (Kingston) - I've never had any problems with either before and overnight scans of the memory using Memtest found no problems so I don't think it's a hardware issue.

---

### Post by Sean22 on 2011-09-27
I literally just had this same problem happen to me. grub suddenly stopped automatically selecting the kernel to load and when I do select it, I get the same error:

init: failed to spawn hostname main process: unable to execute: input/output error

In grub, I'm selecting Ubuntu, with Linux 2.6.35-28-generic-pae.

This is happening to me on a Zotac ZBOX HD-ID40 that I use as a HTPC.

When I picked recovery mode, I see a ton of DRDY ERR status messages for ata1 with error IDNF and failed command: READ DMA. Also seeing some "unable to read inode" messages scrolling by. Looks like it might be a bad disk. Here's what I could capture once it stopped scrolling:

ata1.00: status: { DRDY ERR }
ata1.00: error: { IDNF }
ata1.00: configured for UDMA/133
sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
Descriptor sense data with sense descriptors (in hex):
	72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00
	05 ec 5a 91
sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
sd 0:0:0:0: [sda] CDB: Read(10): 28 00 05 ec 5a 18 00 00 f0 00
end_request: I/O error, dev sda, sector 99375640
EXT4-fs error (device sda7): __ext4_get_inode_loc: inode #794046: (comm bash)
ata1: EH complete
unable to read inode block 3146331

Brings me to a root prompt that won't take any input. The disk itself is a Western Digital Scorpio Black WD3200BEKT 320GB 7200 RPM that I just bought from Newegg on 12/21/2010, so it's only 9 months old.

Anyone else having this problem?

---

### Post by drs305 on 2011-09-27
Will1978

Welcome to the Ubuntu forums.

I have no idea what has happened. As far as permissions, you may be able to copy the files if you become 'root'. You can do this by opening the browser with:```

gksu nautilus
```
or if you have been using the "cp" command, try using "sudo cp" which will ask for your password. (You won't see it as you enter it).

As far as your boot status, if you boot the LiveCD and download and run the boot info script it will give us information on your file and boot status. After running the script, post the contents of RESULTS.txt

You can get to the script download page by clicking the "BIS" link in my signature line.

---

### Post by Will1978 on 2011-09-28
Thank you very much for your help. I managed to use gksu nautilus to copy most of what I needed (sudo cp -r wouldn't work - it didn't prompt for a password - I'm not sure why).

Is there any diagnostic I should run to confirm that the SSD is working correctly and that it definitely isn't a hardware problem? (I'm fairly sure that it isn't a hardware problem but it would be good to be certain - this might also be helpful to the other person who posted on this topic.)

Thank you very much for explaining everything so clearly, carefully and thoughtfully. 

Maybe a fresh install is the best way forward now that the VM files seem to be rescued. Is there anything that might go wrong when moving a VirtualBox VM from one system to another by copying the files like this?

Here are the results from the BIS script. I don't know why Grub has found something it calls msdos1 - that seems odd - maybe the machine accidentally booted in Linux with the Win7 drive connected and Grub tried to create a dual-boot system but things went wrong.  Here are full results:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   237,924,351   237,922,304  83 Linux
/dev/sda2         237,926,398   250,068,991    12,142,594   5 Extended
/dev/sda5         237,926,400   250,068,991    12,142,592  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        72331ad0-3cc9-47ea-8c59-6b5f4fa0b244   ext4       
/dev/sda5        c3b0ca9b-85c5-4362-a961-7aa13472c9b2   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/72331ad0-3cc9-47ea-8c59-6b5f4fa0b244 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 72331ad0-3cc9-47ea-8c59-6b5f4fa0b244
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 72331ad0-3cc9-47ea-8c59-6b5f4fa0b244
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 72331ad0-3cc9-47ea-8c59-6b5f4fa0b244
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=72331ad0-3cc9-47ea-8c59-6b5f4fa0b244 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 72331ad0-3cc9-47ea-8c59-6b5f4fa0b244
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=72331ad0-3cc9-47ea-8c59-6b5f4fa0b244 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 72331ad0-3cc9-47ea-8c59-6b5f4fa0b244
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=72331ad0-3cc9-47ea-8c59-6b5f4fa0b244 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 72331ad0-3cc9-47ea-8c59-6b5f4fa0b244
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=72331ad0-3cc9-47ea-8c59-6b5f4fa0b244 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 72331ad0-3cc9-47ea-8c59-6b5f4fa0b244
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 72331ad0-3cc9-47ea-8c59-6b5f4fa0b244
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=72331ad0-3cc9-47ea-8c59-6b5f4fa0b244 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c3b0ca9b-85c5-4362-a961-7aa13472c9b2 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  74.135513306 = 79.602401280   boot/grub/core.img                             1
  64.185417175 = 68.918566912   boot/grub/grub.cfg                             1
   4.896030426 = 5.257072640    boot/initrd.img-2.6.38-11-generic              1
   1.005405426 = 1.079545856    boot/initrd.img-2.6.38-8-generic               2
   4.688789368 = 5.034549248    boot/vmlinuz-2.6.38-11-generic                 1
  74.133792877 = 79.600553984   boot/vmlinuz-2.6.38-8-generic                  1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 48 b9 00 00 00  |...........H....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Will1978 on 2011-09-29
I made an error in my original post - I should have said Ubuntu 11.04 not Ubuntu 10.04 - corrected.

---

### Post by Will1978 on 2011-09-30
I ran

sudo fsck -f -a /dev/sda1

This reported an unexpected error and said to run in manual mode so I did this

sudo fsck -f /dev/sda1

A very large number of inconsistencies were found in the SSD - I left fsck running overnight with the y key pressed so that it could carry our repairs - running it again in the morning reported more inconsistencies. I'm not sure what this indicates - maybe  big problem with the SSD - I don't have a lot of experience of using fsck

---

### Post by drs305 on 2011-09-30
I don't see any obvious errors in your RESULTS.txt  Although there can be other problems, it would tend to support your finding that there are possibly errors on the disk.

I don't know a lot about repairing disks. Usually my advice is to boot the LiveCD, make sure the Ubuntu partition is not mounted, and then run a modified fsck check:
```
sudo umount /dev/sda1 # It should indicate sda1 is not mounted
sudo e2fsck -f -y -v /dev/sda1
```

---

### Post by Will1978 on 2011-10-09
Thank you very much for your help. Sorry I haven't been in touch - had to work on something else over the last week.

Your suggestion of

 sudo e2fsck -f -y -v /dev/sda1

reported that the filesystem still had errors (have copied the output below) - after running it all the directories on the filesystem had vanished except lost+found but after remounting they were visible again.

Based on the number printed on the SSD the manufacturers suspect that it is faulty and should be returned for replacement. It is a shame there isn't a diagnostic utility that can confirm this.

I had difficulty copying my files using the Live CD so I set up Ubuntu on a separate hard drive and was able to rescue my files.

Here's the last of the output (I left out the first part which just listed a lot of fixes) from sudo e2fsck -f -y -v /dev/sda1

```
Inode 1310675 was part of the orphaned inode list.  FIXED.
Inode 1310678 was part of the orphaned inode list.  FIXED.
Pass 2: Checking directory structure
i_faddr for inode 1306066 (/lost+found/#1306066) is 234507736, should be zero.
Clear? yes

Pass 3: Checking directory connectivity
'..' in /lost+found/#1306066 (1306066) is <The NULL inode> (0), should be /lost+found (11).
Fix? yes

Couldn't fix parent of inode 1306066: Couldn't find parent directory entry

Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

/dev/sda1: ********** WARNING: Filesystem still has errors **********


  177792 inodes used (2.39%)
     343 non-contiguous files (0.2%)
     282 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 9206/1089/9024
         Extent depth histogram: 137806/41
15871261 blocks used (53.37%)
       0 bad blocks
     125 large files

  109310 regular files
   20769 directories
    2445 character device files
    2513 block device files
    3027 fifos
     285 links
   37702 symbolic links (29511 fast symbolic links)
    2017 sockets
--------
  178068 files
will@Samsung200B:~$ 

```

---

