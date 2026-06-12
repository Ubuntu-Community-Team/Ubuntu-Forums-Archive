---
title: "Boot failure - can not find root partition, no uuid"
date: 2010-03-05
forum: General Help
---

### Post by mphatyonah on 2010-03-05
Hi everyone,  I posted this first to thread 'Boot problem - "Gave up waiting for root device.", (initramfs)' then realized that I should start a new thread because the problem is not the same. 
  On boot the splash goes black and nothing happens, On a recovery boot it drops into shell BusyBox and messages indicate that the root partition cannot be found. After booting from CD Gparted GUI partition information shows no label or ssid for the root partition sda2. The data for the root partition appears to be there.
  Does anyone know how to fix this? My /home, swap, and / are on separate partitions formatted ext3. I have a recent backup only for my data. I would like to avoid having to rebuild my system from scratch.

---

### Post by Intrepid Ibex on 2010-03-05
Well is just your grub configured correctly?

---

### Post by mphatyonah on 2010-03-05
Hi there,  I am not 100% sure if the grub is working properly. I did try to boot older kernel and it gave the same results. I think the problem is what gparted information is showing that uuid is blank for the root partition. It knows that it is sda2 the problem is this uuid stuff that I don't understand at all.

---

### Post by Intrepid Ibex on 2010-03-06
Well could you then post your menu.lst by using e.g. livecd?

---

### Post by mphatyonah on 2010-03-06
Thanks for helping. :D I am using 9.10, if I am reading correctly in 9.10 there is no menu.lst 
I can not mount the root partition to get to the /boot, I can mount the home partition though.
If I use gparted to look at the partition information, the partitions other than sda2 the / all show a uuid. The / does not show a uuid.

---

### Post by westernpenguin on 2010-03-06
> **mphatyonah said:**
> Hi everyone,  I posted this first to thread 'Boot problem - "Gave up waiting for root device.", (initramfs)' then realized that I should start a new thread because the problem is not the same. 
  On boot the splash goes black and nothing happens, On a recovery boot it drops into shell BusyBox and messages indicate that the root partition cannot be found. After booting from CD Gparted GUI partition information shows no label or ssid for the root partition sda2. The data for the root partition appears to be there.
  Does anyone know how to fix this? My /home, swap, and / are on separate partitions formatted ext3. I have a recent backup only for my data. I would like to avoid having to rebuild my system from scratch.

This sounds quite a bit like a problem I had before.  There is a command to recreate the UUID for your partitions, but I can't remember it for the life of me.

*edit: Found the correct command, see my later post.  That should serve as a more effective solution.*

These are stored in /dev/disk/by-uuid.  For whatever reason, (I think) the root partition's UUID link was removed.  I'm not as familiar with GRUB2, but with previous versions, disks were loaded by the standard "hd0,0" type IDs. * Usually* UUID problems come up within the fstab file and partition mounting.

Most likely the quickest solution will be to change from "UUID" identifiers to "sda" identifiers in your fstab file.  Boot back up through your installer disk and mount the root partition.  Open up the /etc/fstab file on that partition with
```
gksu gedit
```The important section in this is going to be (in mine for example):
```
# / was on /dev/md4 during installation
UUID=c64ebada-f85f-45ff-a13b-b73123e17a47 /               ext4    errors=remount-ro 0       1
```For you, the /dev/md4 should read /dev/sda2.  Copy the UUID line and then comment out the original.  Change the UUID section to /dev/sda2.  So for me, mine would read:
```
# / was on /dev/md4 during installation
#UUID=c64ebada-f85f-45ff-a13b-b73123e17a47    /               ext4    errors=remount-ro 0       1
/dev/md4     /               ext4    errors=remount-ro 0       1
```Save, give it a reboot, and hope that is the problem.

---

### Post by oldfred on 2010-03-06
Lets see all the results of this script that tells about your configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by meierfra. on 2010-03-06
In addition, to running the boot info script, could you also post the output  of


```
sudo  hexdump -s 0x410 -n 2 /dev/sda2
```

---

### Post by westernpenguin on 2010-03-06
Found the correct command to reset the UUID on the partition. [http://manpages.ubuntu.com/manpages/intrepid/man8/tune2fs.8.html](http://manpages.ubuntu.com/manpages/intrepid/man8/tune2fs.8.html)

This should serve as a catch-all answer to any UUID problems whether from GRUB, fstab, mount, etc.  Boot into the live cd and look at your fstab file again.  (See my previous post.)

(I saw something about not being able to mount anything other than /home.  This should do it for you:
```
sudo mkdir /mnt/sda2
sudo mount /dev/sda2 /mnt/sda2
```If there were any problems mounting the root system to work on it, that should resolve them.  The /mnt/sda2 directory will give you direct access.)

Now inside of /etc/fstab, look at what UUID the system is searching for.  In mine:
```
UUID=c64ebada-f85f-45ff-a13b-b73123e17a47 /               ext4    errors=remount-ro 0       1
``` so I would want c64ebada-f85f-45ff-a13b-b73123e17a47.

Now to restore the UUID to the disk partition, we will use the tune2fs command:
```
sudo tune2fs -U <insert UUID here> /dev/sda2
```So my command would read sudo tune2fs -U c64ebada-f85f-45ff-a13b-b73123e17a46 /dev/md4.

Now just double check that the UUID was assigned to the drive:
```
sudo blkid
```Hope that helps.

---

### Post by mphatyonah on 2010-03-06
This is what I did, and what I have. The mount worked, ;) As you see there is no /dev/sda2 in blkid output. Will it have to boot to show up there?

```
ubuntu@ubuntu:/$ sudo mkdir /mnt/sda2
ubuntu@ubuntu:/$ sudo mount /dev/sda2 /mnt/sda2
mount: you must specify the filesystem type
ubuntu@ubuntu:/$ man mount
ubuntu@ubuntu:/$ sudo mount -t ext2 /dev/sda2 /mnt/sda2
ubuntu@ubuntu:/$ sudo tune2fs -U ce6121cb-943c-4365-9fa0-568937d5d094 /dev/sda2
tune2fs 1.41.9 (22-Aug-2009)
ubuntu@ubuntu:/$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="1BD82EDF27D0A815" TYPE="ntfs" 
/dev/sda3: UUID="0a391d13-8d9a-4cbb-9a8a-7010ee0bd196" TYPE="swap" 
/dev/sda4: UUID="070cf141-33ff-41df-b5c1-4079821ea849" TYPE="ext2" 
/dev/ramzswap0: TYPE="swap" 
ubuntu@ubuntu:/$ 

```

---

### Post by mphatyonah on 2010-03-06
This is the script output ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     5,124,734     5,124,672   7 HPFS/NTFS
/dev/sda2    *      5,124,735    17,414,459    12,289,725  83 Linux
/dev/sda3          17,414,460    18,458,684     1,044,225  82 Linux swap / Solaris
/dev/sda4          18,458,685    78,124,094    59,665,410  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        1BD82EDF27D0A815                       ntfs                                     
/dev/sda2: ambivalent result (probably more filesystems on the device)
/dev/sda3        0a391d13-8d9a-4cbb-9a8a-7010ee0bd196   swap                                     
/dev/sda4        070cf141-33ff-41df-b5c1-4079821ea849   ext2                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda2        /mnt/sda2                ext2       (rw)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set ce6121cb-943c-4365-9fa0-568937d5d094
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set ce6121cb-943c-4365-9fa0-568937d5d094
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=ce6121cb-943c-4365-9fa0-568937d5d094 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set ce6121cb-943c-4365-9fa0-568937d5d094
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=ce6121cb-943c-4365-9fa0-568937d5d094 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set ce6121cb-943c-4365-9fa0-568937d5d094
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ce6121cb-943c-4365-9fa0-568937d5d094 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set ce6121cb-943c-4365-9fa0-568937d5d094
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ce6121cb-943c-4365-9fa0-568937d5d094 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=ce6121cb-943c-4365-9fa0-568937d5d094 /               ext2    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=070cf141-33ff-41df-b5c1-4079821ea849 /home           ext2    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=0a391d13-8d9a-4cbb-9a8a-7010ee0bd196 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


   5.2GB: boot/grub/core.img
   5.2GB: boot/grub/grub.cfg
   5.2GB: boot/initrd.img-2.6.31-14-generic
   5.3GB: boot/initrd.img-2.6.31-16-generic
   5.2GB: boot/vmlinuz-2.6.31-14-generic
   5.2GB: boot/vmlinuz-2.6.31-16-generic
   5.3GB: initrd.img
   5.2GB: initrd.img.old
   5.2GB: vmlinuz
   5.2GB: vmlinuz.old
```

---

### Post by mphatyonah on 2010-03-06
Output of hexdump```
ubuntu@ubuntu:~$ sudo  hexdump -s 0x410 -n 2 /dev/sda2
0000410 138f                                   
0000412
ubuntu@ubuntu:~$ 

```

---

### Post by westernpenguin on 2010-03-06
> **mphatyonah said:**
> Will it have to boot to show up there?

The more important question is does it now boot?

---

### Post by meierfra. on 2010-03-06
> 0000410 138f                                   
0000412


You have this bug:

[http://bugs.launchpad.net/ubuntu/+bug/518582](http://bugs.launchpad.net/ubuntu/+bug/518582)

Luckily the fix is easy. Boot from the LiveCD and


```
sudo mount -t ext2 /dev/sda2 /mnt
ls /mnt 
sudo touch /mnt/empty_file
```
The second command is just to confirm that mounting was successful.
The  third command creates an empty file on /dev/sda2. That should be enough to fix your problem,

Reboot and see whether you can boot into Ubuntu

---

### Post by mphatyonah on 2010-03-06
westernpenguin, No boot to Ubuntu drops to shell as before.

---

### Post by mphatyonah on 2010-03-06
meierfra., No boot to Ubuntu yet, still drops into same shell.
 line 2, ls, did confirm mount.

---

### Post by meierfra. on 2010-03-06
Strange. 
Please post the output of

```
sudo  hexdump -s 0x410 -n 2 /dev/sda2
sudo blkid -p /dev/sda2

```

---

### Post by mphatyonah on 2010-03-06
```
ubuntu@ubuntu:~$ sudo  hexdump -s 0x410 -n 2 /dev/sda2
0000410 138f                                   
0000412
ubuntu@ubuntu:~$ sudo blkid -p /dev/sda2
/dev/sda2: ambivalent result (probably more filesystems on the device)
ubuntu@ubuntu:~$
```

---

### Post by meierfra. on 2010-03-06
Seems the empty file did not get created.  So try again:

```
sudo mount -t ext2 /dev/sda2 /mnt
ls /mnt/empty_file
sudo touch /mnt/empty_file
ls /mnt/empty_file
```


Wait for  a few seconds. Then
```

sudo  hexdump -s 0x410 -n 2 /dev/sda2
sudo blkid -p /dev/sda2

```

Post  the whole  content of the terminal.

---

### Post by westernpenguin on 2010-03-06
Have you tried changing fstab, to work with sda2 instead of uuid?

If that doesn't do anything, can you please post whatever messages you are receiving when being dropped into a terminal?  It may also be necessary to modify grub (is anyone familiar with the inner workings of GRUB2?) to work with sd** identifiers instead of uuid.  I believe this involves editing the grub default config file in /etc/default/grub to disable use of uuid, but I will need to check into that.

---

### Post by mphatyonah on 2010-03-06
```
ubuntu@ubuntu:~$ sudo mount -t ext2 /dev/sda2 /mnt
ubuntu@ubuntu:~$ ls /mnt/empty_file
/mnt/empty_file
ubuntu@ubuntu:~$ sudo touch /mnt/empty_file
ubuntu@ubuntu:~$ ls /mnt/empty_file
/mnt/empty_file
ubuntu@ubuntu:~$ # dee-da-da-da-dee-da-da-dee-da-da-da-awhile
ubuntu@ubuntu:~$ sudo  hexdump -s 0x410 -n 2 /dev/sda2
0000410 138f                                   
0000412
ubuntu@ubuntu:~$ sudo blkid -p /dev/sda2
/dev/sda2: ambivalent result (probably more filesystems on the device)
ubuntu@ubuntu:~$ # doh
ubuntu@ubuntu:~$ 

```

Thanks for all your help. I understand some of this, bits and pieces, but not enough to put it all together.

---

### Post by meierfra. on 2010-03-06
The file was created.  So I don't understand why the number of free inodes did not change.


Lets see what happens if you create a few files:

```
sudo mount -t ext2 /dev/sda2 /mnt
sudo mkdir /mnt/Test_Folder
for i in $(seq 128); do sudo touch /mnt/Test_Folder/$i;done; 
```


Wait for a few seconds. Then

```
sudo  hexdump -s 0x410 -n 2 /dev/sda2
sudo blkid -p /dev/sda2

```

If this still did not work:


> Have you tried changing fstab, to work with sda2 instead of uuid?
This might actually actually work.  You will  also have do edit "grub.cfg". I'll write up instructions, while you try my first suggestion.

---

### Post by mphatyonah on 2010-03-06
I will do that in a few moments.
Is this problem a task for GNU TestDisk?

---

### Post by meierfra. on 2010-03-06
> Is this problem a task for GNU TestDisk? 
No.  I don't think testdisk will be of any use.

If "blkid" still did not recognize /dev/sda2:

```
sudo mount /dev/sda2 /mnt
gksudo gedit /mnt/etc/fstab
```

Change 

UUID=ce6121cb-943c-4365-9fa0-568937d5d094 /               ext2  errors=remount-ro 0   

to

[COLOR="Red"]/dev/sda2[/COLOR]  /               ext2    errors=remount-ro 0   

Save the file.

```
sudo chmod +w /mnt/boot/grub/grub.cfg
gksudo gedit /mnt/boot/grub/grub.cfg

```

Change the first Ubuntu item to

menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	linux	/boot/vmlinuz-2.6.31-16-generic [COLOR="Red"]root=/dev/sda2 [/COLOR]ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}

Save the file.

I know that one is not supposed to edit "grub.cfg" directly since all changes will be overwritten during kernels updates. But that's ok in your case, since the number of free inodes will have changed by then.

This is just a workaround, and I'm not sure whether it will work. As long as blkid does not recognize your Ubuntu partition, you might run into all kinds of problems.  But since the number of free inodes really should change once  you start using Ubuntu, your problem should disappear soon.

---

### Post by westernpenguin on 2010-03-06
> **meierfra. said:**
> I know that one is not supposed to edit "grub.cfg" directly since all changes will be overwritten during kernels updates. But that's ok in your case, since the number of free inodes will have changed by when.

Won't uncommenting ***#GRUB_DISABLE_LINUX_UUID=true*** in /etc/default/grub be necessary to continue the workaround past any kernel updates?

By the way, [https://bugs.launchpad.net/ubuntu/+bug/464411](https://bugs.launchpad.net/ubuntu/+bug/464411) shows a similar if not the same bug, although I think sd** device references will still solve the issue.

---

### Post by mphatyonah on 2010-03-06
```
ubuntu@ubuntu:~$ sudo mount -t ext2 /dev/sda2 /mnt
mount: /dev/sda2 already mounted or /mnt busy
mount: according to mtab, /dev/sda2 is already mounted on /mnt
ubuntu@ubuntu:~$ # from prior mount
ubuntu@ubuntu:~$ sudo mkdir /mnt/Test_Folder
ubuntu@ubuntu:~$ for i in $(seq 128); do sudo touch /mnt/Test_Folder/$i;done;
ubuntu@ubuntu:~$ # a pause
ubuntu@ubuntu:~$ sudo  hexdump -s 0x410 -n 2 /dev/sda2
0000410 138f                                   
0000412
ubuntu@ubuntu:~$ sudo blkid -p /dev/sda2
/dev/sda2: ambivalent result (probably more filesystems on the device)
ubuntu@ubuntu:~$ # DOH
ubuntu@ubuntu:~$ ls /mnt/Test_Folder
1    106  113  120  128  2   27  34  41  49  56  63  70  78  85  92
10   107  114  121  13   20  28  35  42  5   57  64  71  79  86  93
100  108  115  122  14   21  29  36  43  50  58  65  72  8   87  94
101  109  116  123  15   22  3   37  44  51  59  66  73  80  88  95
102  11   117  124  16   23  30  38  45  52  6   67  74  81  89  96
103  110  118  125  17   24  31  39  46  53  60  68  75  82  9   97
104  111  119  126  18   25  32  4   47  54  61  69  76  83  90  98
105  112  12   127  19   26  33  40  48  55  62  7   77  84  91  99
ubuntu@ubuntu:~$ 

```

How can that be?

---

### Post by nexx on 2010-03-06
With karmic I often run into boot problems, black screen...
I just reboot in debug mode, do a few ls and cd in console mode, and sudo reeboot. For some reasons I cannot understand, the reboot is always ok. I hope Lucid will not have these pestering problems.

---

### Post by meierfra. on 2010-03-06
> to continue the workaround past any kernel updates?
The workaround will no longer be necessary since the number of free inodes will have changed.


> [https://bugs.launchpad.net/ubuntu/+bug/464411](https://bugs.launchpad.net/ubuntu/+bug/464411) shows a similar if not the same bug,  
It is  the same bug (blkid getting confused  by traces  of a different file system). But it is triggered differently.  In this case   the particular number of free inodes makes blkid think that /dev/sda2 uses the "minix" file system.  Once the number of free inodes changes, the problem will disappear.

---

### Post by meierfra. on 2010-03-06
```
dev/sda2: ambivalent result (probably more filesystems on the device)
```
Darn.  Maybe a reboot will change the number of free inodes. If not edit "grub.cfg" and "fstab" and see whether that helps.

---

### Post by meierfra. on 2010-03-06
Could you also post the output of

```
sudo BLKID_DEBUG=0xffff blkid -p /dev/sda2
```

---

### Post by mphatyonah on 2010-03-06
Restart did not load ubuntu, ..waiting for root, then to shell. Trying post #22,30. If I understand correct this mod. will revert back to UUID on a kernel update?

---

### Post by mphatyonah on 2010-03-06
```
ubuntu@ubuntu:~$ sudo BLKID_DEBUG=0xffff blkid -p /dev/sda2
libblkid: debug mask set to 0xffff.
reseting blkid_probe
ready for low-probing, offset=0, size=0
--> starting probing loop [idx=-1]
linux_raid_member: call probefunc()
ddf_raid_member: call probefunc()
isw_raid_member: call probefunc()
lsi_mega_raid_member: call probefunc()
via_raid_member: call probefunc()
silicon_medley_raid_member: call probefunc()
nvidia_raid_member: call probefunc()
promise_fasttrack_raid_member: call probefunc()
highpoint_raid_member: call probefunc()
adaptec_raid_member: call probefunc()
jmicron_raid_member: call probefunc()
ext4dev: magic sboff=56, kboff=1
ext4dev: call probefunc()
ext4: magic sboff=56, kboff=1
ext4: call probefunc()
ext3: magic sboff=56, kboff=1
ext3: call probefunc()
ext2: magic sboff=56, kboff=1
ext2: call probefunc()
ext2_sb.compat = 00000000:00000002:00000001
assigning UUID
assigning VERSION
assigning TYPE
assigning USAGE
<-- leaving probing loop (type=ext2) [idx=23]
--> starting probing loop [idx=23]
jbd: magic sboff=56, kboff=1
jbd: call probefunc()
ufs: call probefunc()
sysv: call probefunc()
minix: magic sboff=16, kboff=1
minix: call probefunc()
assigning VERSION
assigning TYPE
assigning USAGE
<-- leaving probing loop (type=minix) [idx=40]
--> starting probing loop [idx=40]
<-- leaving probing loop (failed) [idx=49]
ERROR: ambivalent result detected (2 filesystems)!
/dev/sda2: ambivalent result (probably more filesystems on the device)
ubuntu@ubuntu:~$ 


```

---

### Post by meierfra. on 2010-03-06
I don't think doing post 22 again will help. I  worked on  six of these cases in the last four weeks and they all have been solved just by creating one file.  But all of those six cases had an "ext4" or "ext3" filesystem and not "ext2". Maybe that's why creating file does not help.

> minix: magic sboff=16, kboff=1

This is your problem.  blkid  detects traces of "minix" and gets confused.

Anyway, try the instruction from post 24.  There is a good chance that it will let you boot into Ubuntu.

---

### Post by meierfra. on 2010-03-06
> If I understand correct this mod. will revert back to UUID on a kernel update?

Yes. I told you to directly edit grub.cfg, since  otherwise you would have to chroot into "/dev/sda2" and then run update-grub. Making  the changes permanent will be easier once you booted into Ubuntu.

But I really think we should be able to fix your "blkid" problem, once you successfully booted into Ubuntu.
And once you fixed the blkid problem, I would recommend to undo the changes in "fstab" and "grub.cfg". UUID's usually work better.

---

### Post by mphatyonah on 2010-03-06
Changing the fstab and grub.cfg worked, it booted to ubuntu. I will tidy up tomorrow.

Thank you all for the great help, and for the education. :popcorn:

ps: Just the thought of having to use windoZe next week until I rebuilt my system was very depressing. Oh wait using windows I cant do what I need to because the cost of the software would make my work unprofitable, to time consuming and very labor intensive, not worth the effort. Thanks Again!

---

### Post by meierfra. on 2010-03-07
I just did some testing:  Ext2 does indeed behave differently than ext3 and ext4:  Ext3 and Ext4 automatically  update the free inode count, but ext2 does not.  The free inode count in ext2 seems to be updated  by the kernel. And since you were not able to boot the kernel,  the free inode count never was changed.

If my theory is correct, your problem should be fixed.


So run 

```
sudo blkid -p /dev/sda2
```
blkid should  detect your partition again.

If blkid did detect your partition, I recommend to unto the changes in fstab and grub.cfg.  fstab has  to be edit manually. But  you can revert grub.cfg via

```
sudo update-grub
```


Could you do me a favor? Go to 

[https://bugs.launchpad.net/ubuntu/+bug/518582](https://bugs.launchpad.net/ubuntu/+bug/518582)

click on "This bug affects you" and let launchpad know that you have been affected by this bug.

---

### Post by mphatyonah on 2010-03-07
blkid did see the / partition, I updated grub. All seems to be working correctly. A couple of side notes, after the undo, on the first reboot, it did a series of disk checks, came back clean. Also after login, as gnome desktop opened 4 or 5 small notification windows flashed by with some type of error, and just as quickly disappear from the desktop, on a second reboot, same, third reboot, no error messages, forth reboot, no error messages. Everything seems to be working correctly. One other note, it seems to get to the login screen muck faster now, no complaint about that. Going over to bugs.launchpad.net now. Thanks again, You are showing the world that GNU idea is the superior way. This is another reason I use Linux. BTW I'll date myself, the first computer that I ever used was the GA. Tech Cyber74 (in the olden days of emulators and punched IBM cards) Wow that is...history.

---

### Post by meierfra. on 2010-03-07
> All seems to be working correctly.
Great.

 > A couple of side notes, after the undo, on the first reboot, it did a series of disk checks, came back clean. 
That's expected. Actually there never was anything wrong with your disk. Only that blkid thought  there was something was wrong
> Also after login, as gnome desktop opened 4 or 5 small notification windows flashed by with some type of error, and just as quickly disappear from the desktop,
I guess they were generated before the free inode counts was updated.

> 
 on a second reboot, same, third reboot, no error messages, forth reboot, no error messages.[
Good.

> Going over to bugs.launchpad.net now. 
Thanks.

---

### Post by eaglemystic69 on 2010-03-08
Hi,
I'ld like to join in, looks like your getting somewhere.  Im mainly a GUI guy, and do the code when all else fails (I go cross-eyed with too much) . .. anyway.  

Im on a HPG71, 9.10 fresh install, dual boot with Windows7 installed 1st.  Jaunty/ grub works fine on 2 other machines . . .  not Karmic.

Below are the recommended outputs requested earlier in this thread.  AND, I noticed at the grub screen in "e" its looking for an ext2, and mine in ext4 shown in gparted.

This gets me in manually everytime (for two weeks):
[SIZE=1]1. **ls**[/SIZE] 
    [SIZE=1][/SIZE][SIZE=1]2. **set prefix=(hdX,Y)/boot/grub**[/SIZE]  
    [SIZE=1][/SIZE][SIZE=1]3*. **set root=(hdX,Y)**[/SIZE] 
    [SIZE=1][/SIZE][SIZE=1]4. **set**[/SIZE] 
    [SIZE=1][/SIZE][SIZE=1]5. **ls /boot**[/SIZE] 
    [SIZE=1][/SIZE][SIZE=1]6. **insmod /boot/grub/linux.mod**[/SIZE] 
    [SIZE=1][/SIZE][SIZE=1]7*. **linux /vmlinuz root=/dev/sd*xY* ro**[/SIZE] 
    [SIZE=1][/SIZE][SIZE=1]8. **initrd /initrd.img**[/SIZE] 
    [SIZE=1][/SIZE][SIZE=1]9. **boot**[/SIZE] 
 =====================================
/boot/grub/menu.lst   . . . came up empty


=====================================
sudo  hexdump -s 0x410 -n 2 /dev/sda5
0000410 00be                                   
0000412


=====================================
sudo blkid
/dev/sda1: UUID="E09ADDD29ADDA4F6" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda2: UUID="8C80C01180C00424" LABEL="Windows7" TYPE="ntfs" 
/dev/sda4: UUID="5C483C78483C534E" LABEL="Storage" TYPE="ntfs" 
/dev/sda5: UUID="e24d7934-1843-4bda-924c-d655df287c84" TYPE="ext4" 


=====================================
fstab output
proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=e24d7934-1843-4bda-924c-d655df287c84 / ext4 errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda4 /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/Windows7 ntfs-3g defaults,locale=en_US.UTF-8 0 0


=====================================
Apologies for not knowing howto make this in its own scrolled window.
Boot Info Script 0.55    dated February 15th, 2010                    

Boot Info Summary: 

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 69311051 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe7e8e0a0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             433,755    61,866,314    61,432,560   7 HPFS/NTFS
/dev/sda3          61,882,380   124,391,294    62,508,915   5 Extended
/dev/sda5    *     61,882,443   124,391,294    62,508,852  83 Linux
/dev/sda4         124,391,295   625,137,344   500,746,050   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E09ADDD29ADDA4F6                       ntfs       SYSTEM                        
/dev/sda2        8C80C01180C00424                       ntfs       Windows7                      
/dev/sda4        5C483C78483C534E                       ntfs       Storage                       
/dev/sda5        e24d7934-1843-4bda-924c-d655df287c84   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda4        /media/Storage           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/Windows7          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set e24d7934-1843-4bda-924c-d655df287c84
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e24d7934-1843-4bda-924c-d655df287c84
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=e24d7934-1843-4bda-924c-d655df287c84 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e24d7934-1843-4bda-924c-d655df287c84
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=e24d7934-1843-4bda-924c-d655df287c84 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e24d7934-1843-4bda-924c-d655df287c84
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=e24d7934-1843-4bda-924c-d655df287c84 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e24d7934-1843-4bda-924c-d655df287c84
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=e24d7934-1843-4bda-924c-d655df287c84 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e09addd29adda4f6
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 8c80c01180c00424
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=e24d7934-1843-4bda-924c-d655df287c84 / ext4 errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda4 /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/Windows7 ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


  31.8GB: boot/grub/core.img
  35.3GB: boot/grub/grub.cfg
  32.8GB: boot/initrd.img-2.6.31-19-generic
  33.2GB: boot/initrd.img-2.6.31-19-generic.bak
  33.1GB: boot/initrd.img-2.6.31-20-generic
  33.1GB: boot/initrd.img-2.6.31-20-generic.bak
  33.3GB: boot/vmlinuz-2.6.31-19-generic
  32.8GB: boot/vmlinuz-2.6.31-20-generic
  33.1GB: initrd.img
  32.8GB: initrd.img.old
  32.8GB: vmlinuz
  33.3GB: vmlinuz.old

---

### Post by reese.mitchell on 2010-04-22
> **mphatyonah said:**
> Hi everyone,  I posted this first to thread 'Boot problem - "Gave up waiting for root device.", (initramfs)' then realized that I should start a new thread because the problem is not the same. 
  On boot the splash goes black and nothing happens, On a recovery boot it drops into shell BusyBox and messages indicate that the root partition cannot be found. After booting from CD Gparted GUI partition information shows no label or ssid for the root partition sda2. The data for the root partition appears to be there.
  Does anyone know how to fix this? My /home, swap, and / are on separate partitions formatted ext3. I have a recent backup only for my data. I would like to avoid having to rebuild my system from scratch.


I am not sure if this will help or not but what I did was unplug my internal dvd drive cable. after that it worked like a charm.

---

