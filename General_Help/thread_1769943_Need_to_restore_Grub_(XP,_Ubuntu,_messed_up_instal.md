---
title: "Need to restore Grub (XP, Ubuntu, messed up installation)"
date: 2011-05-28
forum: General Help
---

### Post by jwxie on 2011-05-28
Hi guys.

Previously I had Windows XP and Ubuntu 10.10 installed. Today I decided to reinstall Ubuntu 10.10, so I went ahead and did the installation (simply install via CD and deleted the old Ubuntu partitions).

I also deleted one of my NTFS drive called "Programming" which I used to store some of my programming stuff. I deleted it because I want to allocate more space for Ubuntu. 

Long story short. After the installation, I used GParted to format the unallocated space (28.1 GB) into NTFS. But it was not recgonized by Windows. I run the cheap RAID under Windows, so there are two 500GB disks.

I deleted that free partiation afterward (from both devices, sda, sdb). When I reboot I received grub rescue. I restored my MBR and I was able to go to XP.

Here is the result.txt generated ussing the Boot Info script:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Lilo is installed in the MBR of /dev/mapper/isw_bhjiaijgjj_Volume0.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bhjiaijgjj_Volume01: _______________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

isw_bhjiaijgjj_Volume02: _______________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_bhjiaijgjj_Volume05: _______________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, 
                       isw_bhjiaijgjj_Volume05 starts at sector 63.
    Operating System:  
    Boot files:        

isw_bhjiaijgjj_Volume06: _______________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

isw_bhjiaijgjj_Volume07: _______________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   167,766,794   167,766,732   7 NTFS / exFAT / HPFS
/dev/sda2         167,766,856   974,813,183   807,046,328   f W95 Extended (LBA)
/dev/sda5         167,766,858   587,191,814   419,424,957   7 NTFS / exFAT / HPFS
/dev/sda6         647,194,624   651,192,319     3,997,696  82 Linux swap / Solaris
/dev/sda7         651,194,368   974,813,183   323,618,816  83 Linux


Drive: isw_bhjiaijgjj_Volume0 _____________________________________________________________________

Disk /dev/mapper/isw_bhjiaijgjj_Volume0: 500.1 GB, 500104826880 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976767240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_bhjiaijgjj_Volume01   *             63   167,766,794   167,766,732   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bhjiaijgjj_Volume02        167,766,856   974,813,183   807,046,328   f W95 Extended (LBA)
/dev/mapper/isw_bhjiaijgjj_Volume05        167,766,858   587,191,814   419,424,957   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bhjiaijgjj_Volume06        647,194,624   651,192,319     3,997,696  82 Linux swap / Solaris
/dev/mapper/isw_bhjiaijgjj_Volume07        651,194,368   974,813,183   323,618,816  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_bhjiaijgjj_Volume01 C08835D58835CAA4                       ntfs       
/dev/mapper/isw_bhjiaijgjj_Volume05 8680DC0280DBF721                       ntfs       Personal
/dev/mapper/isw_bhjiaijgjj_Volume06 214636e7-0858-4f46-804b-9682f80198c9   swap       
/dev/mapper/isw_bhjiaijgjj_Volume07 703654c3-fe59-4cc3-8fef-135eb78d00e8   ext4       
/dev/sda                                                isw_raid_member 
/dev/sdc                                                isw_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_bhjiaijgjj_Volume0
isw_bhjiaijgjj_Volume01
isw_bhjiaijgjj_Volume05
isw_bhjiaijgjj_Volume06
isw_bhjiaijgjj_Volume07

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/isw_bhjiaijgjj_Volume01 /media/C08835D58835CAA4  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/mapper/isw_bhjiaijgjj_Volume07 /media/703654c3-fe59-4cc3-8fef-135eb78d00e8 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


====================== isw_bhjiaijgjj_Volume01/boot.ini: =======================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

--------------------------------------------------------------------------------

================= isw_bhjiaijgjj_Volume07/boot/grub/grub.cfg: ==================

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
}

insmod part_msdos
insmod ext2
set root='(/dev/mapper/isw_bhjiaijgjj_Volume0,msdos8)'
search --no-floppy --fs-uuid --set 703654c3-fe59-4cc3-8fef-135eb78d00e8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/mapper/isw_bhjiaijgjj_Volume0,msdos8)'
search --no-floppy --fs-uuid --set 703654c3-fe59-4cc3-8fef-135eb78d00e8
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_bhjiaijgjj_Volume0,msdos8)'
    search --no-floppy --fs-uuid --set 703654c3-fe59-4cc3-8fef-135eb78d00e8
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=703654c3-fe59-4cc3-8fef-135eb78d00e8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_bhjiaijgjj_Volume0,msdos8)'
    search --no-floppy --fs-uuid --set 703654c3-fe59-4cc3-8fef-135eb78d00e8
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=703654c3-fe59-4cc3-8fef-135eb78d00e8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_bhjiaijgjj_Volume0,msdos8)'
    search --no-floppy --fs-uuid --set 703654c3-fe59-4cc3-8fef-135eb78d00e8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=703654c3-fe59-4cc3-8fef-135eb78d00e8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_bhjiaijgjj_Volume0,msdos8)'
    search --no-floppy --fs-uuid --set 703654c3-fe59-4cc3-8fef-135eb78d00e8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=703654c3-fe59-4cc3-8fef-135eb78d00e8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_bhjiaijgjj_Volume0,msdos8)'
    search --no-floppy --fs-uuid --set 703654c3-fe59-4cc3-8fef-135eb78d00e8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_bhjiaijgjj_Volume0,msdos8)'
    search --no-floppy --fs-uuid --set 703654c3-fe59-4cc3-8fef-135eb78d00e8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/mapper/isw_bhjiaijgjj_Volume01)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/mapper/isw_bhjiaijgjj_Volume0,msdos1)'
    search --no-floppy --fs-uuid --set c08835d58835caa4
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
--------------------------------------------------------------------------------

====================== isw_bhjiaijgjj_Volume07/etc/fstab: ======================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_bhjiaijgjj_Volume08 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_bhjiaijgjj_Volume07 none            swap    sw              0       0
--------------------------------------------------------------------------------

========== isw_bhjiaijgjj_Volume07: Location of files loaded by Grub: ==========

           GiB - GB             File                                 Fragment(s)

 338.647003174 = 363.619450880  boot/grub/core.img                             1
 368.701122284 = 395.889815552  boot/grub/grub.cfg                             1
 360.792587280 = 387.398090752  boot/initrd.img-2.6.35-22-generic              2
 311.185546875 = 334.132936704  boot/initrd.img-2.6.35-28-generic              2
 338.651000977 = 363.623743488  boot/vmlinuz-2.6.35-22-generic                 1
 338.645549774 = 363.617890304  boot/vmlinuz-2.6.35-28-generic                 1
 311.185546875 = 334.132936704  initrd.img                                     2
 360.792587280 = 387.398090752  initrd.img.old                                 2
 338.645549774 = 363.617890304  vmlinuz                                        1
 338.651000977 = 363.623743488  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda5


Unknown BootLoader on sda6


Unknown BootLoader on sda7


Unknown BootLoader on isw_bhjiaijgjj_Volume02



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/mapper/isw_bhjiaijgjj_Volume02: No such file or directory
hexdump: /dev/mapper/isw_bhjiaijgjj_Volume02: No such file or directory

```

[IMG]http://img155.imageshack.us/img155/4303/screenshotog.png[/IMG]


From what I see, the archive configuration leaves a mess there. 

I want to achieve two things:
(1) restore Grub and clean up the mess bootloader
(2) format the free space (28.1 GB) NTFS, and make it available (read/write/accessible) to both XP and Linux. 

May someone please help me on this?

Thank you very much.

---

### Post by Quackers on 2011-05-28
It appears that you are using Intel raid (set in bios).
If that is the case your gparted screenshot is not normal, I think.
In my experience when a "fakeraid" array is used /dev/sda and, in your case /dev/sdc should show as unpartitioned. 
In gparted the only device that should show partitions is (in your case) /dev/mapper/isw_bhjiaijgjj_Volume0, which should be accessible by clicking on the little arrow next to the box with /dev/sda in it.
Does that appear?

If not it may be that having made adjustments to your partitions on /dev/sda, you have broken the raid array. Check that in your bios, maybe.

---

### Post by jwxie on 2011-05-28
> **Quackers said:**
> .....

If not it may be that having made adjustments to your partitions on /dev/sda, you have broken the raid array. Check that in your bios, maybe.

You are very correct, Quackers. I forgot to set RAID back to 1st boot. However, that being said, I cannot use live cd to boot into Ubuntu now, because I am setting RAID-0 as 1st boot option.

I don't know any other ways to verify your claim. 
However, I do think you are correct.

Now if you are correct, how do I go about solving #1? 
I tried sudo grub but when I am on the live cd it gives me error said "command grub doesn't exist" (I think...)

Thanks!

--- EDITED
I have asked a similar question before, but that was when I didn't have RAID0.

---

### Post by Quackers on 2011-05-28
Try entering your bios and then go into your RAID screen (probably by pressing ctrl+I when asked. Then look to see if your raid array reports "normal" or "failed"

---

### Post by jwxie on 2011-05-28
Hi Quackers, 
Indeed for me Ctrl + I does the trick!
It said Normal  and bootable.

---

### Post by Quackers on 2011-05-28
So, in the live cd desktop open up gparted.
Near the top right is the box which shows /dev/sda.
If you click on the little arrow next to that is one of the options
/dev/mapper/isw_bhjiaijgjj_Volume0

---

### Post by jwxie on 2011-05-28
Hi. Sorry it takes a while to boot into Ubuntu using live cd

No, there is none, only SDA and SDC are shown. I think that's because I set BOOT BY CD as first option. I cannot boot into live cd without changing the boot order...
 
sudo grub
grub: command not found

---

### Post by Quackers on 2011-05-28
Please try something for me. I don't think it should be necessary with 10.10 but it won't do any harm.
Please close gparted then go to synaptic package manager and install kpartx. Once installed close synaptic then re-open gparted and try that little arrow again and see if the /dev/mapper option appears.

---

### Post by jwxie on 2011-05-28
HI!

Yes. It shows up!

:)

All 3.

Volume0,   dev/sad,   dev/sdb,  all 465.76GiB

---

### Post by Quackers on 2011-05-28
Ok, when /dev/sda and /dev/sdb are selected do they appear as empty?

---

### Post by jwxie on 2011-05-28
> **Quackers said:**
> Ok, when /dev/sda and /dev/sdb are selected do they appear as empty?

I assume select means clicking on the menu. No. After clicking, the content remains the same. None of them shows empty partition list

Thanks.
-- John

---

### Post by Quackers on 2011-05-28
Hmm, that is not what I expected.
We can try to install grub the long-handed way, but I'm not sure if it will accept the commands.
Please open up a terminal and copy/paste these commands one line at a time pressing enter after each line.
It should report no errors. If it reports any errors please show them.
```
sudo mount /dev/mapper/isw_bhjiaijgjj_Volume07 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_bhjiaijgjj_Volume0
```
If no errors are reported please reboot and see if grub appears.

---

### Post by jwxie on 2011-05-28
Woo. Quackers! Thanks for the help The grub appears!

Do you mind to help me on solving #2?

Last time I tried, I formatted the free space NTFS, but it didn't show up under Windows.

Once agian, thank you very much!
I can access both XP and Personal partitions under Ubuntu

---

### Post by Quackers on 2011-05-28
Glad it worked :-)
Don't forget kpartx, you may need to install it to the live desktop every time you need to use it.
What do you want to do exactly for this other query?

---

### Post by jwxie on 2011-05-28
1. What does kpart do to Gparted??? 

2. I have the 28GB free, and my plan was to create it NTFS. Simply put, I want to turn the free space into NTFS drive, and make it available to both Windows and Ubuntu to use. (Personal, for example, is created along with the Windows installation). This afternoon I tried to format the free space NTFS (via GParted), but it didn't show up in My Computer when I logged on XP, and I couldn't even access to that newly created drive after formatting it. It gave me a long error...

---

### Post by Quackers on 2011-05-28
With 11.04 kpartx was necessary for gparted to "see" the raid array. From memory, I believe it was not necessary on 10.10 on my Intel raid system.
So, either my memory is fading or our systems are different.

With regard to your second question I would urge caution, for the moment.
On my system I would change partitions in gparted using the /dev/mapper option in the drop-down box.
However, on my system /dev/sda and /dev/sdb show as unallocated space. The only partitions on mine are shown in /dev/mapper only.

Yours appears to be different. Yours show partitions in /dev/sda etc.
What shows in gparted on /dev/mapper on yours?

The problem is that if you change partitions on /dev/sda rather than /dev/mapper you may break your raid array - and lose everything!

---

### Post by jwxie on 2011-05-28
Hi.

I think screenshots are better :)



Moreover, under Places, I have
Computer   (normal)
Personal   (also normal..)
166GB Filessytem  (from the size I think this is our Ubuntu, which is accessible by Computer;  also no message / no directory shown)
86 GB Filesystem     (no message / no directory shown)
86 GB Filesystem    (accessible)

The last two refer to the XP.

---

### Post by Quackers on 2011-05-28
Is there a /dev/mapper option in gparted now you are in 10.10?

---

### Post by jwxie on 2011-05-28
Hi. I am sorry. I was away for a while.

I didnt notice I uplaoded one of the pictures twice!

The correct one with mapper is attached

Thanks!

---

### Post by Quackers on 2011-05-28
Ok thanks.
On none of the screenshots does it show a NTFS partition in that 28.61GiB space, I see. Did you say earlier that you had created one there with gparted?

I also don't like the red circles with the ! in them. These can mean that the file systems are not in the correct state. If you right-click on each partition (in /dev/mapper) that has a red circle to its left, and choose "information" what does it say in the window that opens up, please?

---

### Post by jwxie on 2011-05-28
Hi,

> On none of the screenshots does it show a NTFS partition in that 28.61GiB space, I see. Did you say earlier that you had created one there with gparted?

Yes. As soon as I realised the newly formated partition was not revealed under XP, I went back to Ubuntu and deleted them (at that time only sda and sbc were shown).

At this point this partition does not exist. It's actually unallocated 28.1GB  (I have two unallocated, one is 28.1GB, the other one is about 1GB large).

I also attached two screenshots. 
For the mapper, the error is different from those shown in sda and sdc (these two give the same flag error).


I hope you don't mind about screenshots (some helpers like written and not screenshots..). But Ithink screenshots can provide more information...

Once again, thank you very much :)

---

### Post by Quackers on 2011-05-28
I occasionally had these red circles but could never solve it. It didn't seem to affect anything though.
You have a choice.
You can either create a new NTFS partition with gparted BUT ONLY in the /dev/mapper screen!!!
or
you can create a new partition from within Windows using the Disk Management window.
Either method should result in the new partition being recognised by both systems.
The new partition, though, will change the partition numbers of your Ubuntu system and your swap partition, though I don't think that will cause any problems with grub.

I still don't like the fact that partitions show in /dev/sda and /dev/sdc though. Consequently I feel I should warn you that partitioning your system may possibly be a risk, though I suspect (and hope) that if you use either of the methods outlined above you should be ok. No guarantees though, the risk is your own!

Alternatively you could wait for further advice from other members. There are several here with much more raid experience than me :-)
Good luck to you, it's nearly bedtime here!

---

### Post by jwxie on 2011-05-30
> **Quackers said:**
> I occasionally had these red circles but could never solve it. It didn't seem to affect anything though.
You have a choice.
You can either create a new NTFS partition with gparted BUT ONLY in the /dev/mapper screen!!!
or
you can create a new partition from within Windows using the Disk Management window.
Either method should result in the new partition being recognised by both systems.
The new partition, though, will change the partition numbers of your Ubuntu system and your swap partition, though I don't think that will cause any problems with grub.

I still don't like the fact that partitions show in /dev/sda and /dev/sdc though. Consequently I feel I should warn you that partitioning your system may possibly be a risk, though I suspect (and hope) that if you use either of the methods outlined above you should be ok. No guarantees though, the risk is your own!

Alternatively you could wait for further advice from other members. There are several here with much more raid experience than me :-)
Good luck to you, it's nearly bedtime here!

Hi Quakcers. Thanks for the tremendous help!
I got everything working. I have been testing :)

Thanks!

---

### Post by Quackers on 2011-05-31
Aha! I'm very glad to hear that :-)
Well done!
Happy testing!

---

