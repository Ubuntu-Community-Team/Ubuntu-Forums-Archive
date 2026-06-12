---
title: "Ubuntu 10.10 not booting - reinstalling Grub question"
date: 2011-03-21
forum: General Help
---

### Post by LeXxPT on 2011-03-21
Edit: Solved -> Did a reinstall.

While trying to boot ubuntu, I noticed that it was taking a long time. A lot longer than usual, in fact.
I then forced a restart on my computer, and noticed that Grub looked different - the resolution was weird.
I then tried again to boot ubuntu, and got the following messages:
[I]vga=792 is deprecated. Use set gfxpayload=1024x768x24,1024x768 before linux command.
mount: mounting /proc/ on /root/proc failed: Input/Output error.[/I]

And then the computer seems to stay idle forever.

Recovery mode is also not useful: I can only see some periodic messages about a failed command: *READ FPDMA QUEUED.*

However, I also noticed that grub showed something before it allowed me to choose which OS I would like to boot (Im running a dualboot configuration with Ubuntu 10.10 and Windows 7).
I managed to get it:
error: hd0, msdos6 out of disk
error: no suitable mode found

Considering that I have no trouble booting into Win 7, and that I can actually access my Ext4 partition from there, Im trying to reinstall Grub from a Live CD.

Heres the output of fdisk -l :

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x869e2b06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1020     8192000   1c  Hidden W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1020       16221   122098688    7  HPFS/NTFS
/dev/sda3           16221       30401   113903297+   f  W95 Ext'd (LBA)
/dev/sda5           16221       28443    98173940    7  HPFS/NTFS
/dev/sda6           28444       30384    15591051   83  Linux
/dev/sda7           30385       30401      136521   82  Linux swap / Solaris

Which commands should I use to reinstall Grub? 

Thanks.

---

### Post by An Sanct on 2011-03-21
To reinstall grub:

> ... From your Live USB, you can probably restore your boot with the  following, replacing X and Y for your drive/partition  information (drive only in the second command):

```
sudo mount /dev/sd**XY** /mnt 
sudo grub-install --root-directory=/mnt /dev/sd**X** 

```Taken from [this thread]("http://ubuntuforums.org/showthread.php?p=10440484"), but I don't know if that will solve tour problem...

---

### Post by oldfred on 2011-03-21
Is this an older system with a newer larger hard drive? Older BIOS have a boot limit of 137GB and often give that out of disk error when beyond the 137GB limit.

If so a separate small boot partition may be required or other changes to get the full bootable Ubuntu system partition within the 137GB, with all your data (/home and a shared NTFS data partition) then beyond the 137 limit.

Also can be caused by some BIOS settings.

---

### Post by LeXxPT on 2011-03-21
Nope, this is a 3 year old laptop, without any modifications.

I have also not changed any BIOS settings since my last successful boot to Ubuntu 10.10.

Heres my RESULTS.txt from the boot info script:

```
               
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 1. But according to the info from fdisk, 
                       sda5 starts at sector 260585472.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    16,386,047    16,384,000  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     16,386,048   260,583,423   244,197,376   7 HPFS/NTFS
/dev/sda3         260,585,470   488,392,064   227,806,595   f W95 Ext d (LBA)
/dev/sda5         260,585,472   456,933,351   196,347,880   7 HPFS/NTFS
/dev/sda6         456,936,858   488,118,959    31,182,102  83 Linux
/dev/sda7         488,119,023   488,392,064       273,042  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8465-B3D6                              vfat       RECOVERY                      
/dev/sda2        C408AE9C08AE8CCC                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        1E00B47000B4508F                       ntfs                                     
/dev/sda6        5f24fb03-b305-4a7d-97d9-953a432d9892   ext4                                     
/dev/sda7        2aa3192c-bc7a-4cca-b1d3-2f08d75c165d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/1E00B47000B4508F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/5f24fb03-b305-4a7d-97d9-953a432d9892 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda6        /mnt                     ext4       (rw)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5f24fb03-b305-4a7d-97d9-953a432d9892
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5f24fb03-b305-4a7d-97d9-953a432d9892
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f24fb03-b305-4a7d-97d9-953a432d9892
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=5f24fb03-b305-4a7d-97d9-953a432d9892 ro  vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f24fb03-b305-4a7d-97d9-953a432d9892
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=5f24fb03-b305-4a7d-97d9-953a432d9892 ro single  vga=792
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f24fb03-b305-4a7d-97d9-953a432d9892
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=5f24fb03-b305-4a7d-97d9-953a432d9892 ro  vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f24fb03-b305-4a7d-97d9-953a432d9892
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=5f24fb03-b305-4a7d-97d9-953a432d9892 ro single  vga=792
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f24fb03-b305-4a7d-97d9-953a432d9892
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f24fb03-b305-4a7d-97d9-953a432d9892
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8465-b3d6
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set c408ae9c08ae8ccc
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

=================== sda6: Location of files loaded by Grub: ===================


 236.2GB: boot/grub/core.img
 234.8GB: boot/grub/grub.cfg
 240.0GB: boot/initrd.img-2.6.35-25-generic
 240.0GB: boot/initrd.img-2.6.35-27-generic
 236.4GB: boot/vmlinuz-2.6.35-25-generic
 237.2GB: boot/vmlinuz-2.6.35-27-generic
 240.0GB: initrd.img
 240.0GB: initrd.img.old
 237.2GB: vmlinuz
 236.4GB: vmlinuz.old

```

Reinstalling Grub had no effect at all, as I kept getting the* vga=792 is deprecated* message...

Edit:
Running the Check Filesystem option on the Disk Utility application on the Live CD gave me a *Filesystem is NOT clean* message.

Running fsck on the command line gives something like:

```

buntu@ubuntu:~$ sudo fsck /dev/sda6
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda6 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 3376646 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>?

Force rewrite<y>?

Inode 524515 has an invalid extent node (blk 3376646, lblk 0)
Clear<y>?

Inode 524515, i_blocks is 336, should be 0.  Fix<y>?

```

---

### Post by oldfred on 2011-03-21
Did you run the full fsck?

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

In this line you have to remove the vga= entry. It is obsolete. YOu must have this from an upgrade?

linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=5f24fb03-b305-4a7d-97d9-953a432d9892 ro  [COLOR=Red]vga=792[/COLOR]  quiet splash

vga=xxx is a deprecated boot option
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)
"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

---

### Post by LeXxPT on 2011-03-21
I am currently running it, but with the command that I posted earlier. (sudo fsck /dev/sda6)

It seems that it is having reading errors on every block...

I will leave the *sudo e2fsck -f -y -v /dev/sda6* command running through the night (Im based in Europe).

And yes, I believe that the vga entry was caused because of an upgrade.

Edit:

After cancelling my previous command, and mounting and acessing the filesystem so I could change the grub config file (to edit out the vga entry), I got this:
[I]
ls: cannot access proc: Input/output error
ls: cannot access etc: Input/output error
ls: cannot access selinux: Input/output error[/I]

---

### Post by LeXxPT on 2011-03-22
Ok, so fsck ended, with the following results:

/dev/sda6: ***** FILE SYSTEM WAS MODIFIED *****

  264182 inodes used (27.10%)
     272 non-contiguous files (0.1%)
     327 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 234857/127
 1843062 blocks used (47.29%)
       0 bad blocks
       1 large file

  194666 regular files
   32713 directories
      59 character device files
      26 block device files
       0 fifos
4294962217 links
   36900 symbolic links (29294 fast symbolic links)
      10 sockets
--------
  253918 files
ubuntu@ubuntu:~$ 

I can still not boot Ubuntu though, as I get a message saying: *mount: mounting /proc on /root/proc failed:[I] No such file or directory*[/I]. And as I did not change the Grub config file, it still shows the vga entry message.

However, when mouting the filesystem on the LiveCD, I cannot find the /etc folder.

I have removed the vga entry from /boot/grub/grub.cfg, which caused for the message to now be showed anymore.

However, the *"error: hd0, msdos6 out of disk"* message is now: "*error: file not found*"

How can I fix this?

---

### Post by oldfred on 2011-03-22
Sometimes BIOS settings can cause issues. What are yours. I saved these comments from others.

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

Oldfred was right on, it was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.

---

### Post by LeXxPT on 2011-03-22
The only ones that I found on my BIOS Setup Utility were the SATA mode and the Disk mode.
SATA mode was set to Enhanced (there was only one other option, Compatibility).
Disk mode was set to Auto (there was no LBA option).

---

### Post by oldfred on 2011-03-22
Did it boot before the upgrade?

Can you boot into the recovery mode?

---

### Post by LeXxPT on 2011-03-22
Yes it did boot before the upgrade.

No, I can't. It hangs after discovering my USB devices.

And I do seem to be missing my /etc and /root/proc folders  on the filesystem... If this is the cause of the problem, is there any way that I can recover them? (I do have the files on my home folder backed-up)

---

### Post by oldfred on 2011-03-22
I do not know of any easy way to recover those folders. I do backup some of my /etc as I have some manually configured system settings, but do not backup all of /etc normally as I plan on just reinstalling.

If /home is fully backed up then reinstalling may be the quickest solution. Now may be a good time to create a separate /home partition and then use that in your new install as well. You can set root to 10 to 20GB and the rest as /home.

Is hard drive showing ok in system, administration, disk utility. It shows smart status. I do not know details but it shows an overall ok if errors are normally low.

---

### Post by LeXxPT on 2011-03-22
On Disk Utility it says: *SMART Status: Not supported*

Everything else was just disk characteristics (the rotation rate was blank though).

I guess I will just go ahead with a re-install, as I only had a couple of system files edited.

Thank you for all the help.

---

