---
title: "Error: File not found"
date: 2010-10-03
forum: General Help
---

### Post by oobermensch on 2010-10-03
Hey all.

Before everything, I'd like to express how much I've fallen in love with Ubuntu. I haven't used Windows in 3 weeks, until now, because of this problem that has been driving me crazy. I booted into Windows earlier just for kicks. Did some maintenance, like cleaning up the hard drive, and defragmenting. When I rebooted and attempted to use Ubuntu, I got the:

"Error: File not found." message. After 2 seconds, it reboots automatically. I tried pressing the INS key (and any key for that matter), but to no avail. It just reboots immediately. I did Google for this problem, but none were as exact as my situation.

I'm using a Wubi install. I have 1 hard drive, split into 2 partitions, with Wubi on drive C:.

Any of you geniuses out there know how to fix this? :(

edit: BTW, I'm using 10.04, with all the latest updates. I just updated this morning.

---

### Post by drs305 on 2010-10-03
Take a look at this link by *meierfra*- sounds like the problem you are having. It may look a bit complicated but just take things slowly:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

There is also this possible solution by the same author if you are using 9.10:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

---

### Post by oobermensch on 2010-10-03
Ok I'll give those a read. BTW, if it helps, I have an Ubuntu install on a flash drive, so I have access to an Ubuntu OS. I just want to repair my Wubi install, get my files, and perhaps try a real dual-boot system.

---

### Post by drs305 on 2010-10-03
If you aren't able to resolve it from those links or others' inputs, please run the boot info script and post the contents of RESULTS.txt:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by efflandt on 2010-10-03
It could be this issue with grub2 from manufacturer and other Windows programs storing things in the mbr that step on grub.  It is mentioned in issues for 10.10 under development, but apparently has been an issue since grub2 started being used in 9.10.  grub2 is larger than the Windows mbr, so some Windows programs unknowingly put things in what they think is vacant space in the mbr that is not vacant.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

---

### Post by oobermensch on 2010-10-03
But it's just so weird that it would happen out of the blue. My Wubi install had been running without a hitch for so long. Do you think my Wubi disk got corrupted when I did a defrag?

---

### Post by bcbc on 2010-10-03
it's probably looking for the root.disk. Windows might have flagged it as corrupt and moved it to a hidden folder FOUND.000. Or it might just be sitting in c:\ubuntu\disks\ but not able to be opened.

If it's the first case move it back to c:\ubuntu\disks, in the second run chkdsk (run Check disk for errors from drive tools and tick Automatically fix).

I don't think defrag would damage a root.disk - I've done it before.

---

### Post by oobermensch on 2010-10-03
root.disk is still there. Anyway, I'm going to boot into my flash drive's Ubuntu install and try Bootscript. Will post results after.

---

### Post by oobermensch on 2010-10-03
Already did Bootscript. Here's what I got:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   119,984,064   119,984,002   c W95 FAT32 (LBA)
/dev/sda2         119,984,128   234,439,222   114,455,095   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4060 MB, 4060086272 bytes
47 heads, 47 sectors/track, 3589 cylinders, total 7929856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,929,855     7,921,792   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       ed506e90-72e5-9846-87e6-2222076df9ad   ext2       casper-rw                     
/dev/loop2       669aaa44-a294-4456-82fe-bd243a43e4df   ext4                                     
/dev/sda1        5EF499A8F49982C7                       ntfs       ACER                          
/dev/sda2        C8B43F8FB43F7ECE                       ntfs       DIGITAL MEDIA                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        CCB9-92EE                              vfat       ANDR ATOM                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 5ef499a8f49982c7
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 5ef499a8f49982c7
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5ef499a8f49982c7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro nomodeset  quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5ef499a8f49982c7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single nomodeset
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5ef499a8f49982c7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro nomodeset  quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5ef499a8f49982c7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single nomodeset
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5ef499a8f49982c7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro nomodeset  quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5ef499a8f49982c7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single nomodeset
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5ef499a8f49982c7
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   3.5GB: boot/grub/grub.cfg
   5.5GB: boot/initrd.img-2.6.32-21-generic
   7.6GB: boot/initrd.img-2.6.32-24-generic
   5.8GB: boot/initrd.img-2.6.32-25-generic
   5.5GB: boot/vmlinuz-2.6.32-21-generic
   5.8GB: boot/vmlinuz-2.6.32-24-generic
   5.8GB: boot/vmlinuz-2.6.32-25-generic
   5.8GB: initrd.img
   7.6GB: initrd.img.old
   5.8GB: vmlinuz
   5.8GB: vmlinuz.old
```

BTW, I just remembered. I removed one of the old Linux kernels (is that the right term?) from Synaptic manager prior to booting to Windows. Could that have caused the error? I'm sure I removed 2.6.32.21

---

### Post by drs305 on 2010-10-03
I don't see a problem with what I see in RESULTS.txt except I note two 'loops', but that may be because you ran it from the LiveCD. I am not as familiar with wubi installs as normal ones.

Are you able to to see the Grub 2 menu during the boot? The normal sequence would be you see the menu for Windows/Ubuntu, then select Ubuntu, then see the various menuentries. Do you see multiple Ubuntu entries?

If so, first press "e" with the top menu item highlighted. Look on the "linux" line and note the "loop" designation. (for instance, loop0).

Press ESC to return to the menu, then "c" to go to the Grub2 prompt. Type "ls (loop0)/boot" or whatever loopX was in the menu. Do you see the vmlinuz and initrd entries? If not, try other loop numbers: ls (loop1)/boot, etc.

Let me know if you find anything.

---

### Post by oobermensch on 2010-10-03
Ok a new problem came up. When I tried using /fixboot using a Vista DVD, I get a blinking cursor when I should actually see the boot menu. :/ Now, I'm not able to get to Vista or Ubuntu at all.

I swear this is the worst way to start off the week.

---

### Post by oobermensch on 2010-10-04
OK a little update. Miraculously, the boot loader came up again. :O I'm completely baffled but at the same time very glad because my problems are lessened. I'm using Vista now. Next thing I want to do is recover my 2nd partition. I was playing around with Testdisk earlier and I think I might have lost my second partition (D:/) in the process. Now, it appears as unallocated space. I know Testdisk can undo the damage, but I want to be more careful now and follow advice from the experts.

What should I do to recover/undelete my 2nd partition?

---

### Post by drs305 on 2010-10-04
I'd still try finding your files using the methods I proposed in Post 10 - it may not be a partition table problem.

I've used both these sites for help with TestDisk:
[_TestDisk_Step_By_Step_]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")

[Herman's TestDisk HowTo]("http://members.iinet.net.au/~herman546/p21.html")

---

### Post by oobermensch on 2010-10-04
TestDisk is awesome! :O I ended up reformatting my 2nd partition, but I was able to retrieve my entire music and video collection, as well as my documents. Plus, I got Ubuntu working again. GRUB shows up after the Windows bootloader screen. How it happened, I still don't know.

Cheers drs305!

---

### Post by Weazel86 on 2010-10-08
Hi guys, I'm actually having the exact same problem. Did you guys find the solution to getting access again to the wubi partition ? Because I have a lot of work on there( i know should have gone with a normal dual boot) and i really need to get access to it. pls help :(

tnx

---

### Post by drs305 on 2010-10-08
> **Weazel86 said:**
> Hi guys, I'm actually having the exact same problem. Did you guys find the solution to getting access again to the wubi partition ? Because I have a lot of work on there( i know should have gone with a normal dual boot) and i really need to get access to it. pls help :(

tnx

This is a quick way to *access* the wubi files so you can save them elsewhere (this assumes Windows is on sda1, change if different):

Boot to the LiveCD desktop and open a terminal (Applications, Accessories, Terminal).

```
sudo mkdir /mnt/windows /mnt/wubi
sudo mount /dev/sda1 /mnt/windows
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/wubi
```

---

### Post by bcbc on 2010-10-08
> **Weazel86 said:**
> Hi guys, I'm actually having the exact same problem. Did you guys find the solution to getting access again to the wubi partition ? Because I have a lot of work on there( i know should have gone with a normal dual boot) and i really need to get access to it. pls help :(

tnx

[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)
There are some issues with wubi and updates to grub-pc that can affect users on 10.04.1 as well as those upgrading to 10.10. That link shows a workaround.

---

### Post by drs305 on 2010-10-08
Thanks *bcbc*!

If that workaround will work, you have already mounted the root.disk with the commands I provided. From there:

```
gksu gedit /mnt/wubi/boot/grub/grub.cfg
```
and remove the top lines as *bcbc's* link suggest.

Please let us know if that works for you.

---

### Post by Weazel86 on 2010-10-08
It worked ! Thank you all for the help. the workaround worked and I had no problem changing the top lines in grub.cfg. Just follow the code :)

---

### Post by drs305 on 2010-10-08
I've placed the solution below the warning I had on my [_Grub 2 Basics_]("http://ubuntuforums.org/showthread.php?t=1195275") link so there is a one-stop reference on how to fix this.

Thanks to *bcbc* for providing the link to the solution and to *Weazel86* for confirming it worked. I have subsequently (intentionally) 'broken' a wubi install and successfully repaired it in the same manner.

---

### Post by bcbc on 2010-10-08
Great, thanks drs305

I just wanted to add that when this happened to me with an update to 10.04.1 (from 10.04), running "sudo update-grub" fixed it.  However,  this doesn't work when it occurs after upgrading from 10.04.1 to 10.10. 

Since running update-grub also regenerates the grub.cfg so if it doesn't fix the problem you'll probably need to repeat the workaround. Also after installing a new kernel, removing an old one etc., grub.cfg will be regenerated.

Edit: there's another bug specific to 10.10 for this [https://bugs.launchpad.net/wubi/+bug/653134](https://bugs.launchpad.net/wubi/+bug/653134)

---

