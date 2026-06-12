---
title: "Strange booting problem XP and Mint"
date: 2010-12-03
forum: General Help
---

### Post by moon_raker on 2010-12-03
I wonder if someone would be kind enough to assist with this question I was asked:- 

> I have linux mint debian on my master drive and windows xp on my slave drive (why I have no clue!!!)...

When I turn the computer on, it boots to the slave drive (a quick check in the bios and it says boot master drive 1st!)

If I turn on the computer and bring up the boot options and choose boot master drive, it goes right to grub and boots perfectly!

What am I missing ?

Boot Info script attached.

I see that the boot flag points to XP, but as I don't use Windows I'd rather not be blamed later on for messsing things up. Thanks in advance.

---

### Post by wilee-nilee on 2010-12-03
Not sure how you did this nor the fix but the highlighted area in sda3 should be between the red and green of sda1


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 270848 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #1 for (,msdos1)/grub.
    Operating System:  
    Boot files/dirs:   [COLOR="Red"]/grub/grub.cfg[/COLOR] [COLOR="SeaGreen"]/grub/core.img[/COLOR]

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint Debian Edition
    Boot files/dirs:   **/etc/fstab**

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     4,098,047     4,096,000  83 Linux
/dev/sda2           4,098,048    12,290,047     8,192,000  82 Linux swap / Solaris
/dev/sda3          12,290,048    43,010,047    30,720,000  83 Linux
/dev/sda4          43,010,048   398,297,087   355,287,040  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   234,420,479   234,420,417   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3aa2c19f-5d20-4913-a4de-db255dc9ab14   ext4                                     
/dev/sda2        33c12a14-809f-42fb-8cfa-72194e7b29da   swap       swap                          
/dev/sda3        26095430-0ce1-4d67-bc0e-0f58a6373df5   ext4                                     
/dev/sda4        87dde05c-7eaf-465f-b0c7-3e3ea14fb99c   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        842099F22099EB84                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda4        /home                    ext4       (rw,errors=remount-ro)
/dev/sda1        /boot                    ext4       (rw,errors=remount-ro)
/dev/sr1         /media/TRISTANIA_LIVE    udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


============================= sda1/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 26095430-0ce1-4d67-bc0e-0f58a6373df5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 3aa2c19f-5d20-4913-a4de-db255dc9ab14
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 3aa2c19f-5d20-4913-a4de-db255dc9ab14
insmod png
if background_image /grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-686' --class linuxmint --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3aa2c19f-5d20-4913-a4de-db255dc9ab14
	echo	'Loading Linux 2.6.32-5-686 ...'
	linux	/vmlinuz-2.6.32-5-686 root=UUID=26095430-0ce1-4d67-bc0e-0f58a6373df5 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-5-686
}
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3aa2c19f-5d20-4913-a4de-db255dc9ab14
	echo	'Loading Linux 2.6.32-5-686 ...'
	linux	/vmlinuz-2.6.32-5-686 root=UUID=26095430-0ce1-4d67-bc0e-0f58a6373df5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-5-686
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 842099f22099eb84
	drivemap -s (hd0) ${root}
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

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .1GB: initrd.img-2.6.32-5-686
    .1GB: vmlinuz-2.6.32-5-686

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=39dce7bc-28c6-4d48-a3e1-b2d48712856e /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f5355ad1-6de9-497b-a8d4-e2abe7336d4d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda4	/home	ext4	rw,errors=remount-ro	0	0
/dev/sda1	/boot	ext4	rw,errors=remount-ro	0	0
/dev/sda3	/	ext4	rw,errors=remount-ro	0	0

=================== sda3: Location of files loaded by Grub: ===================


   6.4GB: initrd.img
   6.4GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

### Post by sikander3786 on 2010-12-03
You need to chroot/purge Grub2 as advised here and then re-install it.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
(courtesy of forum member **drs305**)

As a basic setup, Grub shouldn't be installed to the boot sector of a partition, instead it just needs to be in the MBR of the HDD.

Sda1 doesn't seem to be a /boot partition. If it was, then the script seems ok to me (except an instance of Grub2 is also present in the boot sector of sda1).

Anyhow, chroot, purge and re-install will take care of all the stuff itself.

---

### Post by wilee-nilee on 2010-12-03
> **sikander3786 said:**
> You need to chroot/purge Grub2 as advised here and then re-install it.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
(courtesy of forum member **drs305**)

As a basic setup, Grub shouldn't be installed to the boot sector of a partition, instead it just needs to be in the MBR of the HDD.

Sda1 doesn't seem to be a /boot partition. If it was, then the script seems ok to me but then there shouldn't be any problems with booting Grub.

Anyhow, chroot, purge and re-install will take care of all the stuff itself.

+1 I suspect your right on this one for sure, I'm just familiar with that chroot purge and reload of grub2.;)

---

### Post by moon_raker on 2010-12-03
> **sikander3786 said:**
> You need to chroot/purge Grub2 as advised here and then re-install it.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
(courtesy of forum member **drs305**)

As a basic setup, Grub shouldn't be installed to the boot sector of a partition, instead it just needs to be in the MBR of the HDD.

Sda1 doesn't seem to be a /boot partition. If it was, then the script seems ok to me (except an instance of Grub2 is also present in the boot sector of sda1).

Anyhow, chroot, purge and re-install will take care of all the stuff itself.
Many thanks sikander3786 and wilee-nilee. Strange that some Grub2 files decided to install to sda1 boot sector.
Anyway I appreciate such prompt advice from you - holding thimbs that all will be OK.

---

### Post by nixie21 on 2010-12-03
Hi, moon_raker was helping me with this and I have a question..

I want to make sure I follow these instructions correctly!!!

I can boot into my linux debian so I can start at step 2 (which I know has internet,LOL, so I can go to 3)

so I (When presented with the device option, use the UP/DN keys to select the correct drive (sdX).) use SDA?

Do you all agree I can skip step 1?

Can I figure out what I did wrong here?  I had XP installed on the computer as the master drive.  I then put another drive into the master and moved the XP to the slave.  I then installed Mint Debian.  Is it just me picking the wrong spot for Grub during install? 

Thank you all so much for the help, it is MUCH appreciated!!!!!:popcorn:

---

### Post by nixie21 on 2010-12-03
WELL, I did everything, but the same issue is here...new log attached!

Thanks

---

### Post by drs305 on 2010-12-03
> **nixie21 said:**
> WELL, I did everything, but the same issue is here...new log attached!

Thanks

Boot to the grub menu. Highlight the first entry. Cursor to the linux line.
Change:
> linux	/vmlinuz-2.6.32-5-686 root=UUID=26095430-0ce1-4d67-bc0e-0f58a6373df5 ro  quiet
To:
> Under testing. I will post back when I determine a solution - if I can establish one.
CTRL-x 

See if it boots.

---

### Post by sikander3786 on 2010-12-03
> **nixie21 said:**
> WELL, I did everything, but the same issue is here...new log attached!

Thanks
There don't seem to be many changes from the initial Results.txt.

Which steps did you follow on that guide?

---

### Post by nixie21 on 2010-12-03
> **sikander3786 said:**
> There don't seem to be many changes from the initial Results.txt.

Which steps did you follow on that guide?

I did 2 - 5

---

### Post by nixie21 on 2010-12-03
> **drs305 said:**
> Boot to the grub menu. Highlight the first entry. Cursor to the linux line.
Change:

To:

CTRL-x 

See if it boots.

Sorry for the silly question, but how do i boot to the grub menu?

---

### Post by drs305 on 2010-12-03
> **nixie21 said:**
> Sorry for the silly question, but how do i boot to the grub menu?

Actually, I'm glad you didn't. But to answer your question, as Grub boots it would normally display the grub menu if it detects a second OS. If it doesn't, try holding down the SHIFT key during boot and see if it appears.

Once the menu is displayed, you can edit the highlighted menuentry by pressing "e" or get to the grub prompt by pressing "c". 

Your problem sounds very much like an addressing issue. The reason I'm glad you didn't do what I suggested is that I have not tested a separate /boot setup but am installing one now.

When I see exactly how G2 treats the separate /boot partition I will post back if you haven't solved your problem.

---

### Post by moon_raker on 2010-12-04
Not to disturb the thread as I am pretty clueless (not a drs305 for sure) :)
So there is a seperate grub2 /boot partition sda1 ??
[quote=sikander3786]Sda1 doesn't seem to be a /boot partition. If it was, then the script seems ok to me (except an instance of Grub2 is also present in the boot sector of sda1).[/quote]

Will one not have to mount both root sda3 and boot partitions ?
sudo mount /dev/sda3 /mnt 
sudo mount /dev/sda1 /mnt/boot 
sudo mount --bind /dev /mnt/dev 
sudo chroot /mnt 
dpkg-reconfigure grub-pc 
Ctrl+D
sudo umount /mnt/dev
sudo umount /mnt 
???
Obviously I am as confused as nixie21 is, that's why I suggested to pay a visit to this forum. Anyway, interesting to see how it all turns out.

---

### Post by sikander3786 on 2010-12-04
Yep. You need to mount /boot separately.

But I'd recommend to wait for **drs305**. They will be back soon with some good news, I know :-)

---

### Post by drs305 on 2010-12-04
Edit: Once again, another post as I was typing. *sikander3786* has already responded.

moon_raker,

In general, if you are working from a LiveCD or chrooting into another OS and it has a separate /boot partition, yes you have to mount the /boot partition as well.

In simplest terms, if you have to mount the main OS partition to perform work on it you must also mount any separate /boot partition if the commands you run are going to affect any of the files within the /boot folder.

Of course, if you are already operating in that OS there is no need since the /boot partition would already be mounted.

In the specific example you gave, depending on where you are chrooting from, you will probably have to mount more than just /dev (/proc, /sys, etc). One chroot example can be seen in the page linked to in my signature line (G2-Chroot).

---

### Post by nixie21 on 2010-12-04
Wow, I need to learn this stuff!!!  Thanks for looking into my problem!

---

### Post by moon_raker on 2010-12-04
Thanks to drs305 (et al) I* may *just reach rank amateur status as regards Grub2.   :D

---

### Post by nixie21 on 2010-12-08
So does anyone have an idea for me to try?  

Thanks!!!

---

### Post by drs305 on 2010-12-08
> **nixie21 said:**
> So does anyone have an idea for me to try?  


Can you describe what you want specifically and what it's doing? For instance, do you want to boot Ubuntu or Mint? 

If it's booting to the Ubuntu/Mint OS you want but you can't get into Windows the issue may be that you have moved it around. What I would recommend in this case would be to disconnect the Ubuntu drive, use a Windows repair disk to reinstall the boot files and fix the MBR to boot straight to Windows (point the BIOS at your Windows drive). 

Once you can boot to Windows, it will be easy to change the BIOS to point to the Ubuntu drive and set Grub to boot both.

---

### Post by nixie21 on 2010-12-08
Sorry...

I have 2 hard drives in the computer, not duel boot...

The Master drive has Mint Debian installed
The Slave has Windows XP

When I turn the computer on, it will boot right to the slave drive...If I hit boot menu (F12) and choose boot to primary master drive, then it boots to Mint, which is what I want.

I double checked the bios settings, it says boot to Primary c: Drive.

I do not know where to look for this problem?  Nothing in Bios settings helped, and I am at a loss.

Thanks so much.

---

### Post by drs305 on 2010-12-08
I think the general terminology is 'dual boot' whether or not the OS's are on the same drive or not. But that doesn't really matter.

I am not sure what is going on, but to continue investigating I can think of two things to try:

1. Switch the boot order in BIOS, even though it says it is booting to the drive you want. You can also check the SATA cables (or PATA). Perhaps they are reversed and that is why it appears to be booting the incorrect drive first.

2. If you have done that, next try holding down the SHIFT key during the boot process. If it is Grub2 that is controlling the boot (but selecting Windows) the menu will appear. We will then know that we have to work on the G2 files.

3. Finally, you can check to see if you have a /boot/grub/device.map file. It's just a text file so you can check it to make sure the drives aren't reversed. Most installs don't have a device.map file, so if it doesn't find one that is ok.

```
cat /boot/grub/device.map
```

---

### Post by nixie21 on 2010-12-08
Drives are set up right.  Holding shift does not do anything, it goes right to windows.

The cat of the file =


(hd0)	/dev/disk/by-id/ata-Maxtor_6L200P0_L40CSASG
(hd1)	/dev/disk/by-id/ata-ST3120026A_3JT3AE1L


As a test I went into bios and turned the slave drive to off and then it booted fine (I figured it would)

Thanks for the help!

---

### Post by moon_raker on 2010-12-09
> **nixie21 said:**
> 
As a test I went into bios and turned the slave drive to off and then it booted fine (I figured it would)

Thanks for the help!

So, you are getting the grub2 menu and can choose which OS to boot ?
Good news if that is the case. O:)

---

### Post by nixie21 on 2010-12-11
Well, it does go to grub right away when I have the slave drive set to off.  I can access the drive inside linux...thing is that I can not boot to this drive at all now.  Even though it shows up in grub, it is OFF in the bios so will not boot to it.  This stinks!!!

I dont need windows too often so this is good enough I guess

---

