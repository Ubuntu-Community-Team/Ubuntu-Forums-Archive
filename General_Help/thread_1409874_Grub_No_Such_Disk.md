---
title: "Grub: No Such Disk"
date: 2010-02-18
forum: General Help
---

### Post by phDaemon on 2010-02-18
Hello all. I have an interesting problem.

I was using my computer today, trying to fix my friends computer when i mounted his external to backup his files. After this, the power went out. When i turned my computer back on, grub started, then it showed the ubuntu splash and told me one of the disks could not be mounted. I ran fsck ( usually fixes that when a hard unexpected shutdown happens ) and it didnt do anything. So i rebooted, and now i have this error

Grub: No such Disk

I tried looking in my BIOS and rearranging my boot set up. Nothing. I rebooted without the external on, and nothing.


I have browsed the forums looking for something but i cannot find anything to fix this issue.

I am currently from a live CD. The live CD shows my home drive, and my other two partitions but i do not see my root partition ( for my old installation ) i dont know if this is common.

Any help would be awesome. ( a little ironic that i was fixing someone else's computer and now i need to fix mine! )

Thanks!

---

### Post by phDaemon on 2010-02-18
Also, here is my output for boot info
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=e7cbebbf-52af-467d-9a07-5acef7eae4bc)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001928d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe771e771

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   234,438,655   234,436,608   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a74cf

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   585,938,744   585,938,682  83 Linux
/dev/sdc2         585,938,745 1,953,520,064 1,367,581,320   5 Extended
/dev/sdc5         585,938,808 1,933,599,464 1,347,660,657  83 Linux
/dev/sdc6       1,933,599,528 1,953,520,064    19,920,537  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       3649ed30-d643-4784-abd3-b882b74b049f   ext4                                     
/dev/sda1        82b56365-4e9c-466c-8092-2d191aeca5e9   ext3       Backups                       
/dev/sdb1        A87CF7A97CF77104                       ntfs                                     
/dev/sdc5        6450be21-e98b-4354-8c1b-486d18e6a40e   ext3       Home                          
/dev/sdc6        9f6befd0-84e9-418b-b477-ef26988b1594   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdc5        /media/Home              ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda1        /media/Backups           ext3       (rw,nosuid,nodev,uhelper=devkit)


======================== sdb1/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set a87cf7a97cf77104
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set a87cf7a97cf77104
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e41ce2f11ce2be24
    chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 355fa35b-db87-40f2-be42-fedf88f44a89
    linux /boot/vmlinuz-2.6.31-15-generic root=UUID=355fa35b-db87-40f2-be42-fedf88f44a89 ro quiet splash
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 355fa35b-db87-40f2-be42-fedf88f44a89
    linux /boot/vmlinuz-2.6.31-15-generic root=UUID=355fa35b-db87-40f2-be42-fedf88f44a89 ro single
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 355fa35b-db87-40f2-be42-fedf88f44a89
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdb1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sdb1/Wubi: Location of files loaded by Grub: =================


   2.7GB: boot/grub/grub.cfg
   2.7GB: boot/initrd.img-2.6.31-14-generic
   2.5GB: boot/vmlinuz-2.6.31-14-generic
   2.7GB: initrd.img
   2.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  a4 81 00 00 33 01 00 00  87 12 7c 4b 87 12 7c 4b  |....3.....|K..|K|
00000010  2d ff 79 4b 00 00 00 00  00 00 01 00 08 00 00 00  |-.yK............|
00000020  00 00 00 00 00 00 00 00  8a d1 89 01 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 9c e7 55 f4  00 00 00 00 00 00 00 00  |......U.........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  04 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  a4 81 00 00 20 00 00 00  bd 9d 72 4b bd 9d 72 4b  |.... .....rK..rK|
00000110  bd 9d 72 4b 00 00 00 00  00 00 01 00 08 00 00 00  |..rK............|
00000120  00 00 00 00 00 00 00 00  58 58 89 01 00 00 00 00  |........XX......|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 54 c1 55 f4  00 00 00 00 00 00 00 00  |....T.U.........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  04 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200

```The "Vista" partition it is refering to, is my old vista partition (which is not bootable) that just contains random data.


It seems that my partition for root "/" cannot be found.

as when i type:
```

ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

```

Thats the error i get.

---

### Post by phDaemon on 2010-02-18
BTW, is there any way to reset the information for my root partition?

---

### Post by jessel on 2010-02-18
phDaemon,

1) if you have a problem mounting a partition, there should be an error on dmesg, so check your log files

2) the grub error may reflect a grub configuration issue. i know that it is typically straightforward to simply say 'update-grub' BUT as my configuration became more customized I found that the 'update-grub' script does not work for me...

let me know how you make out

---

### Post by jessel on 2010-02-18
sorry, i guess i forgot you were using the live-cd, so i guess dmesg is out.

you want to get to the command prompt. grub 2 still has a command prompt right? with grub i can find the path to the boot partition using the shell autocomplete feature pretty easily...

---

### Post by phDaemon on 2010-02-18
When grub gives me that error, it only lets me input using the "grub recovery>" prompt.

So i have no access to any linux shell other than the live cd one. Unless there is some grub commands i can try to run i dont know how to get to the shell.

---

### Post by jessel on 2010-02-18
> When grub gives me that error, it only lets me input using the "grub recovery>" prompt.I think thats what I'm after. In grub there is a command line interface that is built to act somewhat like a bash shell.

DON'T ASSUME THIS WILL WORK FOR YOU, please see your man pages. the thing is i bet the operations in grub 2 are similiar to grub. so, here's how i re-install grub (onto my first hard drive MBR)
1) get to the grub interface, then

```
grub> root (hd0,0)
```         note that hd0,0 is /dev/sda1 and /dev/sdb2 would be hd1,2
```
grub> setup (hd0)
```          thats it, and there is output that will show you success or failure

---

### Post by phDaemon on 2010-02-18
Those commands didnt work.

I booted back into the liveCD and a bit of an idea hit me. I went into gparted to see what partitions it listed.

It seems that my root partition ( sdc1 ) is corrupted ( or damaged ) as it is not recognized at all. So I ran the command
sudo fsck.ext3 -f /dev/sdc1

And i am currently in the process of trying to recover it.

Ill post my results.

---

### Post by jessel on 2010-02-18
> It seems that my root partition ( sdc1 ) is corruptedsounds like that would do it.

> Those commands didnt work.i am guessing that "grub 2" is much different from the original, so i figured that my note would probably only have a limited use for you. when you say the commands didn't work, did you mean that the command names are different? or just that grub didn't like the idea of installing onto a corrupted partition?

let me know, i'll check this thread again tomorrow. til then i'm off the computer. good luck!

---

### Post by phDaemon on 2010-02-18
The commands were "unknown". I went to the grub2 page, and most of those were unknown as well, including ones that are supposed to work under the rescue prompt.

When i tried to boot back up it said files were missing, but a lot of stuff was moved to lost and found so im probably going to have to re-install my root partition ( is there any way of doing this? just the root? ) and leave /home untouched?

anyways, im running fsck on everything now and seeing how it goes.
Ill keep updating this thread as i make progress.

I just went into the lost and found folder on root, ( i recovered it ) BUT a lot of folders and files are in there now. Guess i AM going to have to re-install ubuntu ( this is crappy, all because of a power outage! ).

[Crazyness...](http://i116.photobucket.com/albums/o2/phdaemon/root_lost_and_found.png)

And thats not even all of it, thats just inside one of the folders :O

---

### Post by jessel on 2010-02-18
ok, i'm trying to get off the computer! i feel your pain here, i became familier with grub becuase of some problems and spent quite a bit of time trying to restore grub, only to find out that it is very simple. the thing is it was hard to learn under the circumstances.

the general advice is that you should not re-install over that partition. take your time and try not to be frustrated.

it should be possible to re-install grub using the live cd. the way it works on jaunty is that i boot the live-cd then choose an option to get to the boot prompt. the grub interface will now work, so since you've looked up the commands take it from there!

i think the reason grub isn't working right is that the MBR is on the corrupted partition and grub was damaged.

---

### Post by phDaemon on 2010-02-18
Well, no matter what, i have to reinstall root. A lot of files are missing, so....Im going to try to go into the advanced settings during a new install and see how it goes...

---

### Post by phDaemon on 2010-02-18
Yey, recovered my computer with minial loss.

I used the live cd to delete my old root, create a new one, mount my old home and swap to the new installation mountpoints, and all my files are there, just a few programs that i have to reinstall.

---

### Post by jessel on 2010-02-19
> **phDaemon said:**
> Yey, recovered my computer with minial loss.

I used the live cd to delete my old root, create a new one, mount my old home and swap to the new installation mountpoints, and all my files are there, just a few programs that i have to reinstall.

glad to hear it the loss was minimal. your story reinforces my desire to get a UPS...

what do you do for backups? i have a pretty simple system of backing up my drive onto a second hard drive. the second drive is bootable, so if the primary drive became unbootable, i would just boot the backup drive. for the basic layout see [http://www.jwz.org/doc/backups.html](http://www.jwz.org/doc/backups.html)

---

### Post by phDaemon on 2010-02-19
I just have 3 different drives inside my computer. 1 is set to mount root or "/". The other one (1TB) is set to mount home. and the third i use for backing up any data i need.

So when my root got corrupted, i just used the Live CD to re-format and reinstall root, and mount home to the current home, without reformating home. Leaving all my data intact and minimizing collateral. I only had to re-install a few programs, but everything went pretty good.

---

### Post by jessel on 2010-02-19
having the /home partition separate is definitely smart, and for this very reason.

---

