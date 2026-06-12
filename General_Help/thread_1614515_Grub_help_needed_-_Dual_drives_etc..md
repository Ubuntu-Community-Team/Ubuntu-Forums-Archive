---
title: "Grub help needed - Dual drives etc."
date: 2010-11-05
forum: General Help
---

### Post by fast_ian on 2010-11-05
Hi,

I'm not a 100% sure how I got here, but my system won't boot anything other than a live CD.....

The 500GB sata drive is half Ubuntu on sda5 with half unallocated but earmarked for CentOS. The system also has a "rack mount" on the IDE bus in which is, currently, a 40GB XP Disk with I don't know what for a boot loader anymore! [It seems to behave differently depending on if it's powered and/or on the bus]

I can't get "bootinfo.sh" to run (mount points are wrong) to run , but here's the output from blkid. Dunno why sda5 isn't showing up....

```
[centos@livecd Desktop]$ /sbin/blkid
/dev/live: LABEL="CentOS-5.5-i386-LiveCD-Release2" TYPE="iso9660" 
/dev/mapper/live-osimg-min: LABEL="CentOS-5.5-i386-" UUID="a4a9523c-920a-4cd0-99cb-d9c89be50855" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/live-rw: LABEL="CentOS-5.5-i386-" UUID="a4a9523c-920a-4cd0-99cb-d9c89be50855" TYPE="ext3" 
/dev/hda1: TYPE="ntfs" 
/dev/loop3: LABEL="CentOS-5.5-i386-" UUID="a4a9523c-920a-4cd0-99cb-d9c89be50855" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: LABEL="CentOS" UUID="b3c870f2-5d17-4e33-a164-94cb14b6b800" TYPE="ext4" 
/dev/sda6: TYPE="swap" LABEL="Swap" UUID="94b87194-41e2-41eb-af40-1934a76cc3f4" 
```

And here's fdisk -l

```
[root@livecd sda2]# /sbin/fdisk -l

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3648    29302528+   7  HPFS/NTFS

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       32706   262710913+   5  Extended
/dev/sda2   *       32707       60801   225673087+  83  Linux
/dev/sda5               1       31954   256670442   83  Linux
/dev/sda6           31955       32706     6040408+  82  Linux swap / Solaris

Disk /dev/dm-0: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
```

I have no idea what /dev/dm* is.......

I'd like to save sda5 as that's where Ubuntu lives, put CentOS on the second partition (sda2) and have the option of booting all three - Along the way I've gotten chainloader errors and more and am now completely confused! Any help much appreciated,

Cheers,
Ian

---

### Post by oldfred on 2010-11-05
Are you booting the Centos as a liveCD? The boot info script expects certain standard linux commands but I am not sure it has been tested on much beside Ubuntu. Can you boot the Ubuntu liveCD and run the boot info script?

Perhaps you need to run fsck on sda5? Some times that causes issues.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sda5
if errors:
sudo e2fsck -f -y -v /dev/sda5

Is centos setting up LVM or did you have RAID. That is what mapper is saying and I know nothing about LVM or RAID.

---

### Post by nl4m on 2010-11-05
Can you go more into the problem? What do you see? Is it the grub command prompt? I'll walk you through reinstalling Grub the MBR.

1. Boot into the CD.
2. Launch the Terminal
3. Find the partition that Ubuntu is on (sda5, was it?) type in small letters: SUDO CAT /PROC/PARTITIONS 
4. To mount the Ubuntu partition from the HDD, type in small letters: SUDO MOUNT /DEV/SDA5 (or whatever the partition is) /HOME/(user name)/Desktop (<capital "D" in "Desktop")
5. Make sure you are connected to the internet and type in small letters: SUDO GRUB-INSTALL --ROOT-DIRECTORY=/HOME/(user name)/Desktop (<capital "D" in "Desktop") /DEV/SDA (only "sda" without the number "5" at the end)
6. Check device map: CAT /BOOT/GRUB/DEVICE.MAP
7. To unmount type in small letters: SUDO UMOUNT /HOME/(user name)/Desktop (< Capital "D" in "Desktop")
8. Reboot 
I think the "(username)" is "Ubuntu". In case I'm wrong you can change "/home/(user name)/Desktop" to "/home/$(whoami)/Desktop" < That will fill in the user name for you.

To backup use the "CPIO" (in small letters) command. To move things from one partition to another use the command "DD IF= OF=" (All small letters). Be careful using "DD".

---

### Post by fast_ian on 2010-11-05
> **oldfred said:**
> Are you booting the Centos as a liveCD?

Yes indeed. Of note here though is the liveCD is just that - You can run it for testing but it doesn't have any installation capability - For that you need 7 iso's worth of stuff (:eek:)

> The boot info script expects certain standard linux commands but I am not sure it has been tested on much beside Ubuntu. Can you boot the Ubuntu liveCD and run the boot info script?

I had a quick poke, and it's a super clean script, so I'd guess it will run almost everywhere - Great job guys! I was thinking about some sym links, but was hoping I'd get away with it ;) I'll post the output shortly....

> Perhaps you need to run fsck on sda5? Some times that causes issues.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sda5
if errors:
sudo e2fsck -f -y -v /dev/sda5

I dunno how or why it could have got hosed, but I'll certainly give it a go & post back.

> Is centos setting up LVM or did you have RAID. That is what mapper is saying and I know nothing about LVM or RAID.

Awesome! Thanks for that - While poking at CentOS I played with their LVM and created one on the unallocated space - It didn't do me any good and I deleted it, but at least now I know what /dev/dm* is all about - I'd never come across it before - Thanks again. No RAID btw.

Cheers,
Ian

---

### Post by fast_ian on 2010-11-05
> **nl4m said:**
> Can you go more into the problem? What do you see? Is it the grub command prompt?
...
...MUCH good info rm'd in the interests of bandwidth ;)
...


Firstly, thanks for the walk-thru - It may very well come to that....

It's at "grub-rescue>" btw - I can "set prefix" & the like, but haven't (yet)....

In the meantime I did a live boot (to Ubuntu9) and ran the script. It told me sda5 was an "LVM2 Member" - So, I booted back to Centos -> LVManager -> Removed sda5 from membership. [This also of course resulted in loosing the results.txt file.....]

I booted back to live UB9 and am now getting nervous! - I'll attach the new (current) output in the next post. (Different boxes).

Cheers, and thanks for the help

---

### Post by fast_ian on 2010-11-05
> **fast_ian said:**
> ....I booted back to live UB9 and am now getting nervous! - I'll attach the new (current) output in the next post.

OK - The current situation:

- The very first entry caught my eye!..... 
- Then I don't like sda5 being unknown type.... 
- Then I don't like that the start sector has moved...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000eca6

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   525,421,889   525,421,827   5 Extended
/dev/sda5                 126   513,341,009   513,340,884  83 Linux
/dev/sda6         513,341,073   525,421,889    12,080,817  82 Linux swap / Solaris
/dev/sda2    *    525,421,890   976,768,064   451,346,175  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        b3c870f2-5d17-4e33-a164-94cb14b6b800   ext4       CentOS                        
/dev/sda6        94b87194-41e2-41eb-af40-1934a76cc3f4   swap       Swap                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
 
```

---

### Post by oldfred on 2010-11-05
The fdisk listing see sda5 as linux, but blkid and the parsing at the beginning do not see it. That says there is some inconsistency.(duh:))

I would try the e2fsck. I had similar issue with my NTFS partition but I used windows chkdsk and after rebooting then I could see it. If e2fsck does not solve it then I would try testdisk as it looks a little deeper.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by fast_ian on 2010-11-06
> **oldfred said:**
> ....I would try the e2fsck.....

So, that's what I did - Your cmd line above has a typo (I guess):

```
sudo e2fsck -C -p -f -v /dev/sda5
```

Worked for me [Admittedly, *after* I checked WTF I was about to do! ;)]

It reported bad magic....

Your fix it cmd did lots of stuff (way more than fits in my tty buffer), but it eventually reported that life was good again - And I can indeed boot into Ubuntu10 - Awesome! - *Many* thanks!

This now returns us (somewhat) to the OP - The other drive - It's currently off the bus & powered down but I'll now return it to the configuration and report back..... What I'd really like is Grub to "see" whatever is in that slot, and if it's bootable add it to the other possibilities. A given here is these rm'able drives *will* (should!) be bootable and only ever contain a single OS.

Cheers,
Ian

---

### Post by oldfred on 2010-11-06
Glad it worked. After plugging in your second disk, you need to get grub to find other systems.

```
sudo update-grub
```The C0 is supposed to give a progress bar. Did you type it and use o?

From man e2fsck
If the file descriptor  specified  is  0,  e2fsck  will
              print  a  completion  bar  as  it goes about its business.

---

### Post by fast_ian on 2010-11-06
> **oldfred said:**
> Glad it worked. After plugging in your second disk, you need to get grub to find other systems.

```
sudo grub-update
```

Thanks for that. It turns out that the little 30GB I just plugged in shows up in disk utility  with "Disk failure is imminent!". [Pretty much sums up my day!] However, it contains nothing but a new, patched (to SP3) and AVG Free protected version of XP - I'd love to dump the whole mess off to sda5 so I don't have to do the M$ activate Windows BS - I guess dd as suggested above?

> The C0 is supposed to give a progress bar. Did you type it and use o?

I (thought!) I tried both zero and "o". No problem - I'm booting again!

Cheers,
Ian

---

### Post by fast_ian on 2010-11-06
> **oldfred said:**
> 
```
sudo grub-update
```

"sudo update-grub" :D

I too am having a long day ;)

Cheers,
Ian

---

### Post by oldfred on 2010-11-06
Do not know about reactivation. I had to reactive when I reinstalled a new motherboard and it was hidden behind all sorts of error messages that would not let me update on the internet but until I activated I could not get on Internet.

If you do copy windows be sure to copy to a primary partition. I have seen some make it work in a logical but windows does not normally.

---

### Post by fast_ian on 2010-11-06
Thanks again to all who are following this somewhat sorry tale. An update, and yet more questions follow;

- The 30GB XP drive whose failure was "imminent" has gone to the great disk-recycling center.
- Another (more or less up-to-date) XP drive was inserted, Ubuntu10 was booted, "update-grub" found and added it to the list - Boots fine.
- CentOS was allowed to format (at the time) sda2 and installed wonderfully. I told it to *not* install Grub - I think multiple installs (with different H/W configs!) got me in to this mess in the first place.....
- Update-grub sees Centos, but if I try and boot it can't find the kernel;

> VFS: Cannot open root device sdb2 or unknown-block (0,0) "root=" needed

Now, the temptation is to put grub into CentOS, but as I said I'm nervous and a little wiser - Bootinfo results attached from the current config - How can I tell grub to boot Cent, without breaking anything else is I guess the question....
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.93 is installed in the MBR of /dev/sda and looks at sector 
    503061927 on boot drive #2 for the stage2 file. A stage2 file is at this 
    location on /dev/sdb. Stage2 looks on partition #3 for 
    /boot/grub/grub.conf.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  CentOS release 5.5 (Final) 
                       Kernel on an
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   268,414,019   268,413,957   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   525,421,889   525,421,827   5 Extended
/dev/sdb5                 126   513,341,009   513,340,884  83 Linux
/dev/sdb6         513,341,073   525,421,889    12,080,817  82 Linux swap / Solaris
/dev/sdb2    *    525,421,890   976,768,064   451,346,175  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AE888AF8888ABE79                       ntfs       WindowsXP                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        3152014d-0a02-4d0c-bb55-d532bfc8f15c   ext3       /                             
/dev/sdb5        6af5012c-d24d-4771-86a4-1cf813660c0a   ext4       Ubuntu10                      
/dev/sdb6        94b87194-41e2-41eb-af40-1934a76cc3f4   swap       Swap                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 6af5012c-d24d-4771-86a4-1cf813660c0a
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=6af5012c-d24d-4771-86a4-1cf813660c0a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 6af5012c-d24d-4771-86a4-1cf813660c0a
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=6af5012c-d24d-4771-86a4-1cf813660c0a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 6af5012c-d24d-4771-86a4-1cf813660c0a
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=6af5012c-d24d-4771-86a4-1cf813660c0a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 6af5012c-d24d-4771-86a4-1cf813660c0a
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=6af5012c-d24d-4771-86a4-1cf813660c0a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 6af5012c-d24d-4771-86a4-1cf813660c0a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 6af5012c-d24d-4771-86a4-1cf813660c0a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ae888af8888abe79
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 3152014d-0a02-4d0c-bb55-d532bfc8f15c
	linux /boot/vmlinuz-2.6.18-194.el5 root=/dev/sdb2
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 3152014d-0a02-4d0c-bb55-d532bfc8f15c
	linux /boot/vmlinuz-2.6.18-194.el5xen root=/dev/sdb2
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=6af5012c-d24d-4771-86a4-1cf813660c0a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=d03cad24-2af3-4eba-aa30-7ae34f6144a9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


    .4GB: boot/grub/core.img
   5.4GB: boot/grub/grub.cfg
   1.4GB: boot/initrd.img-2.6.32-24-generic
   1.4GB: boot/initrd.img-2.6.32-25-generic
   1.4GB: boot/vmlinuz-2.6.32-24-generic
   1.3GB: boot/vmlinuz-2.6.32-25-generic
   1.4GB: initrd.img
   1.4GB: initrd.img.old
   1.3GB: vmlinuz
   1.4GB: vmlinuz.old

=============================== sdb2/etc/fstab: ===============================

LABEL=/                 /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
LABEL=Swap              swap                    swap    defaults        0 0

=================== sdb2: Location of files loaded by Grub: ===================


 478.4GB: boot/initrd-2.6.18-194.el5.img
 478.4GB: boot/initrd-2.6.18-194.el5xen.img
 478.5GB: boot/vmlinuz-2.6.18-194.el5
 478.4GB: boot/vmlinuz-2.6.18-194.el5xen
```

The second CentOS option is "Xen" btw - I think I know how to delete that when the time comes. Thanks again for any insights!

Cheers,
Ian

---

### Post by oldfred on 2010-11-06
There is another thread with the same issue.
[http://ubuntuforums.org/showthread.php?t=1614974](http://ubuntuforums.org/showthread.php?t=1614974)

Grub's osprober is leaving off the initrd line.

Copy the osprober entry into 40_custom and add the missing line.

---

### Post by fast_ian on 2010-11-07
> **oldfred said:**
> There is another thread with the same issue.

Thx - I was also watching that one.

> Grub's osprober is leaving off the initrd line.

Copy the osprober entry into 40_custom and add the missing line.

I *think* I can figure out how to do that. Although, I don't understand this comment in my grub.cfg;

>  Be careful not to change # the 'exec tail' line above.

There isn't one!....

Anyway, I guess the question becomes "why?" - I'm not be facetious, but it finds the kernel, I don't get why it fails to also find initrd(?) However, having studied the docs I'm about as clear as mud on what's good and what's not - Hence, more questions....

- The "consensus" seems to be that Grub & Grub2 don't play nicely together. From results.txt above:

```
=> Grub 0.93 is installed in the MBR of /dev/sda and looks at sector 
    503061927 on boot drive #2 for the stage2 file. A stage2 file is at this 
    location on /dev/sdb. Stage2 looks on partition #3 for 
    /boot/grub/grub.conf.
```

This is (I think!) telling me two things;

1 - I should really get grub2 onto the XP disk - How?
2 - I don't have a partition #3, unless it's referring to sdb2?

Having said that, the above are minor compared with my now urgent need to boot into CentOS [XP is only for learning to fly R/C planes, CentOS should allow me to pay some bills! ;)]

So, I poked more, and got more confused. [At least this time I haven't done the bull-in-a-china-shop thing!]

- Should I install grub?(2?) into CentOS? - Again, how? 
- Ubuntu mounts it's root from sdb5 at "/", and grub knows to go & look in /boot for it's stuff (I think?) However, when it formatted sdb2 it gave it another "/" label - Surely this will confuse the hell out of grub?

I can change this label from disk utility in Ubuntu and mount it, but the idea of then doing "update-grub" terrifies me!....

Sorry to be a pest, but as already noted I'm really nervous!

TIA, cheers,
Ian

---

### Post by oldfred on 2010-11-07
If your 40_custom was blank you must have opened a new file, either wrong path or names.

gedit /boot/grub/grub.cfg
Copy current entries to this:
gksudo gedit /etc/grub.d/40_custom

This is one the other does not have the xen. Once this works copy it and edit out the xen, so you have two versions.

menuentry "CentOS release 5.5 (Final) (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 3152014d-0a02-4d0c-bb55-d532bfc8f15c
    linux /boot/vmlinuz-2.6.18-194.el5xen root=/dev/sdb2
    initrd /boot/initrd-2.6.18-194.el5xen.img
}



The set root may also need to be changed to (hd0,2) as you should be booting from sdb and the boot drive is always hd0. You can edit while booting using e at the grub menu. search may override & it may still work.

I would not worry about the MBR in sda, that is some old install that will not work. But as long as you boot sdb, the MBR insda does not matter. Nor would I install grub2 to centos.

I have several / partitions. It is just when you install grub2 to the MBR you have to tell it which one you are using.

---

### Post by fast_ian on 2010-11-08
> **oldfred said:**
> If your 40_custom was blank you must have opened a new file, either wrong path or names.

My bad! I was looking for the "exec tail" in grub.cfg - Sorry, I found it.

> gedit /boot/grub/grub.cfg
Copy current entries to this:
gksudo gedit /etc/grub.d/40_custom

This is one the other does not have the xen. Once this works copy it and edit out the xen, so you have two versions.

menuentry "CentOS release 5.5 (Final) (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 3152014d-0a02-4d0c-bb55-d532bfc8f15c
    linux /boot/vmlinuz-2.6.18-194.el5xen root=/dev/sdb2
    initrd /boot/initrd-2.6.18-194.el5xen.img
}

So, I added  that menuentry into 40_custom, did a grub update & rebooted - I did indeed have a new menuentry at the end, but when selected I got an ugly;

"Error - You need to load the kernel first" message :eek: I got the same msg regardless of "set root" - I tried both (hd1,2) and (hd0,2)

However, I really freaked when my Ubuntu hung at the login screen! [No user names to select]..... Fortunately, recovery mode -> vi 40_custom and rm the above lines "fixed" it. Whew!....

I dunno why it couldn't find a kernel? - *Unless* all "menuentry"s from .cfg need adding to 40_custom?

Again, TIA, cheers,
Ian

---

### Post by oldfred on 2010-11-08
Because you are booting from the second drive but at boot it is hd0, you probably have to change both hd0,2 and the kernel line that says sdb2 to sda2 as it boots it may be sda? Not sure but you can edit in the grub menu with e.

---

### Post by fast_ian on 2010-11-10
Back again!

The good news is it boots after I edit the grub entry to, as you suspected, sda2. [I must have also messed up one of the xen files as that version doesn't boot - The least of my worries right now.]

However, I'm so nervous about "update-grub" every time I boot [which isn't very often now :)] I go and make the changes then "ctrl-x" to boot!

The two "dead" CentOS entries also remain, but again, I don't want to screw up again.....

*Many* thanks for the help,

Cheers,
Ian

---

### Post by oldfred on 2010-11-11
Every new kernel &change to grub's files will automatically rerun a grub update.

You can turn off osprober so it does not find the other systems. If you install another system then you can turn it back on to find the correct entries for 40_custom. Also if Centos updates a kernel you will have to manually edit your 40_custom.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by fast_ian on 2010-11-11
Oh dear!.....

Firstly, thanks again for those links - I've now done *lots* of reading and am slowly starting to "get it" - But see below!.....

OT - A little suggestion - I (and I'm sure others) didn't notice the entire "tutorials & tips" forum that's buried in "Other community discussions". I think it should also be at least a sticky in the "Absolute beginner talk" & maybe even "front & Center" on the home page?.... In my limited experience reading many of these threads the answer is often; "read this......"

My 02c. 

Anyway, with my new found knowledge (a little being dangerous as we know ;)) I popped the corrected menuentry for CentOS into 40_custom and disabled the prober. Update grub and now all I've got is my two Ubuntu kernels & memtest! [Windoze is gone and Cent isn't there!....]

However, "grub-mkconfig" appears to do it correctly.....

I'll continue poking and report back- May as well document this nausea here as anywhere I guess!

Cheers,
Ian

---

### Post by oldfred on 2010-11-11
You would have to copy all other systems. So turn prober on and update, then copy the windows entry also. 

But why is the update not including 40_custom in your grub? Did you turn something else off also? You can check recent commands with this 

```
history
```

---

### Post by fast_ian on 2010-11-22
Oh dear oh dear! 

I eventually got 'er going to my satisfaction, and had been (working!) in CentOS land for the past week.... I needed a reboot, and that reminded me that I should really update this thread.

Then the wheels fell off.....

The reboot defaulted (as expected) to Ubuntu10.04, and auto-update suggested I update "stuff" - It obviously updated grub as it asked me to confirm any changes it would make - I declined ("leave it as is").

Now when I boot I get:

Grub loading
error: the symbol 'grub_puts_' not found
grub rescue>

I'm now booted into a 10.10 LiveCD and bootinfo output is below - Sorry 'bout this guys - I thought I had this down! I really can't afford to lose sda2 or 5.... Any help much appreciated,

Cheers,
Ian
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  CentOS release 5.5 (Final) 
                       Kernel on an
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   525,421,889   525,421,827   5 Extended
/dev/sda5    *            126   513,341,009   513,340,884  83 Linux
/dev/sda6         513,341,073   525,421,889    12,080,817  82 Linux swap / Solaris
/dev/sda2    *    525,421,890   976,768,064   451,346,175  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        3152014d-0a02-4d0c-bb55-d532bfc8f15c   ext3       CentOS                        
/dev/sda5        6af5012c-d24d-4771-86a4-1cf813660c0a   ext4       Ubuntu10                      
/dev/sda6        94b87194-41e2-41eb-af40-1934a76cc3f4   swap       Swap                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/Ubuntu10          ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/_                 ext3       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 6af5012c-d24d-4771-86a4-1cf813660c0a
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
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 6af5012c-d24d-4771-86a4-1cf813660c0a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=20
fi
insmod play
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6af5012c-d24d-4771-86a4-1cf813660c0a
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6af5012c-d24d-4771-86a4-1cf813660c0a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6af5012c-d24d-4771-86a4-1cf813660c0a
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6af5012c-d24d-4771-86a4-1cf813660c0a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6af5012c-d24d-4771-86a4-1cf813660c0a
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6af5012c-d24d-4771-86a4-1cf813660c0a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6af5012c-d24d-4771-86a4-1cf813660c0a
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6af5012c-d24d-4771-86a4-1cf813660c0a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6af5012c-d24d-4771-86a4-1cf813660c0a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6af5012c-d24d-4771-86a4-1cf813660c0a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "CentOS release 5.5 (Final) (on /dev/sdb2)" {
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 3152014d-0a02-4d0c-bb55-d532bfc8f15c
linux /boot/vmlinuz-2.6.18-194.el5 root=/dev/sdb2
initrd /boot/initrd-2.6.18-194.el5.img
}
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=6af5012c-d24d-4771-86a4-1cf813660c0a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=d03cad24-2af3-4eba-aa30-7ae34f6144a9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   5.4GB: boot/grub/grub.cfg
   1.4GB: boot/initrd.img-2.6.32-24-generic
   1.6GB: boot/initrd.img-2.6.32-25-generic
   1.4GB: boot/vmlinuz-2.6.32-24-generic
   1.3GB: boot/vmlinuz-2.6.32-25-generic
   1.6GB: initrd.img
   1.4GB: initrd.img.old
   1.3GB: vmlinuz
   1.4GB: vmlinuz.old

=============================== sda2/etc/fstab: ===============================

LABEL=/                 /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
LABEL=Swap              swap                    swap    defaults        0 0

=================== sda2: Location of files loaded by Grub: ===================


 478.4GB: boot/initrd-2.6.18-194.17.4.el5.img
 478.4GB: boot/initrd-2.6.18-194.17.4.el5xen.img
 478.4GB: boot/initrd-2.6.18-194.26.1.el5.img
 478.4GB: boot/initrd-2.6.18-194.26.1.el5xen.img
 478.4GB: boot/initrd-2.6.18-194.el5.img
 478.4GB: boot/initrd-2.6.18-194.el5xen.img
 478.5GB: boot/vmlinuz-2.6.18-194.17.4.el5
 478.5GB: boot/vmlinuz-2.6.18-194.17.4.el5xen
 478.4GB: boot/vmlinuz-2.6.18-194.26.1.el5
 478.4GB: boot/vmlinuz-2.6.18-194.26.1.el5xen
 478.5GB: boot/vmlinuz-2.6.18-194.el5
 478.4GB: boot/vmlinuz-2.6.18-194.el5xen

```

---

### Post by oldfred on 2010-11-22
On sda you have two boot flags. grub does not use a boot flag, windows has to have one, and some BIOS will not let you boot without one on a primary partition, but you never should have two. Use gparted or command line to remove the one on sda5.
grub puts error - reinstall grub worked
Different drive
[http://ubuntuforums.org/showthread.php?t=1467514](http://ubuntuforums.org/showthread.php?t=1467514)
Chroot & install grub2
[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)

Basically the fix is to reinstall grub. Whether the quick version will work or if you have to use the full chroot verison. lets try the quick version.

#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

