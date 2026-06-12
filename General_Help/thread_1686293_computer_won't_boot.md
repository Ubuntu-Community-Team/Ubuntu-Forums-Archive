---
title: "computer won't boot"
date: 2011-02-12
forum: General Help
---

### Post by roxat on 2011-02-12
I have two partitions installedon my computer, Ubuntu 10.04 (part. sda2) and Windows XP (part. sda1). When I restart my computer I get this message:

 [B]error: file not found
grub rescue>

[/B]I thought this must be a grub error, so I booteda Super Grub disk (v 0.9799). Then I tried to fix grub with the Super Grub disk, but I got this message:

[B]Error 15: File not found
   Booting 'not lucky'
pause SGD has NOT succeeded
[/B][B]SGD has NOT succeeded

[/B]I then booted the system using an Ubuntu live CD, version 10.04.I  tried to repair the sda2 Ubuntu partition. At a terminal prompt I ran ```
 **sudo e2fsck -f -y -v /dev/sda2**. This did not work. It ended with "e2fsck aborted". I could not repair the Ubuntu partition,
I tried to open the sda2 partition by running the terminal command [code] **sudo mount /dev/sda2 /mnt**. I received the following message:

[B]mount:  wrong fs type, bad option, bad superblock on /dev/sda2
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so[/B]

Using the ntfs-config program, I can easily mount the Windows XP partition (sda1). It mounts and I can read or write the files on the Windows XP partition. So at least Windows XP is not damaged.

I downloaded and ran the boot info script, and here are the results:

[CODE]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 246906777 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   399,102,794   399,102,732   7 HPFS/NTFS
/dev/sda2         399,102,795   797,562,989   398,460,195  83 Linux
/dev/sda3         797,562,990   805,948,919     8,385,930  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8E1442281442141D                       ntfs       JDiskCntfs                    
/dev/sda2        148baf56-f6a2-4a93-82bc-44a3aa04a7fb   ext3       JDiskFext3                    
/dev/sda3                                               swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc 
=============================== StdErr Messages: ===============================

ERROR: asr: seeking device "/dev/sdb" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdb" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdb" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sdb" to 4608
ERROR: hpt45x: seeking device "/dev/sdb" to 18446744073709545984
ERROR: isw: seeking device "/dev/sdb" to 18446744073709550592
ERROR: isw: seeking device "/dev/sdb" to 18446744073709551104
ERROR: isw: seeking device "/dev/sdb" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sdb" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sdb" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sdb" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sdb" to 137438913024
ERROR: pdc: seeking device "/dev/sdb" to 137438920192
ERROR: pdc: seeking device "/dev/sdb" to 137438927360
ERROR: pdc: seeking device "/dev/sdb" to 137438934528
ERROR: sil: seeking device "/dev/sdb" to 18446744073709551104
ERROR: via: seeking device "/dev/sdb" to 18446744073709551104
ERROR: asr: seeking device "/dev/sdb" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdb" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdb" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sdb" to 4608
ERROR: hpt45x: seeking device "/dev/sdb" to 18446744073709545984
ERROR: isw: seeking device "/dev/sdb" to 18446744073709550592
ERROR: isw: seeking device "/dev/sdb" to 18446744073709551104
ERROR: isw: seeking device "/dev/sdb" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sdb" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sdb" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sdb" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sdb" to 137438913024
ERROR: pdc: seeking device "/dev/sdb" to 137438920192
ERROR: pdc: seeking device "/dev/sdb" to 137438927360
ERROR: pdc: seeking device "/dev/sdb" to 137438934528
ERROR: sil: seeking device "/dev/sdb" to 18446744073709551104
ERROR: via: seeking device "/dev/sdb" to 18446744073709551104
```
 

Can anyone help? I need to get  my system running again.

Thanks.

roxat

---

### Post by runeh76 on 2011-02-12
Hi

Have a look at this

[http://ubuntuforums.org/showthread.php?t=1563883]("http://ubuntuforums.org/showthread.php?t=1563883")

---

### Post by Saskie on 2011-02-12
:frown::confused: I have ubuntu and vista on computer when turn it on command is error:no such partition
Grub rescue I cant access anything but setup blue screen and don't know what to do here help

---

### Post by Rubi1200 on 2011-02-13
> **Saskie said:**
> :frown::confused: I have ubuntu and vista on computer when turn it on command is error:no such partition
Grub rescue I cant access anything but setup blue screen and don't know what to do here help
Please don't hijack threads; the staff do not like it.

You can use the Report Abuse function next to your post and ask a moderator to start this in a new thread.

In any event, here is what you need to do please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Rubi1200 on 2011-02-13
> **roxat said:**
> I have two partitions installedon my computer, Ubuntu 10.04 (part. sda2) and Windows XP (part. sda1). When I restart my computer I get this message:

 [B]error: file not found
grub rescue>

[/B]I thought this must be a grub error, so I booteda Super Grub disk (v 0.9799). Then I tried to fix grub with the Super Grub disk, but I got this message:

[B]Error 15: File not found
   Booting 'not lucky'
pause SGD has NOT succeeded
[/B][B]SGD has NOT succeeded

[/B]I then booted the system using an Ubuntu live CD, version 10.04.I  tried to repair the sda2 Ubuntu partition. At a terminal prompt I ran ```
 **sudo e2fsck -f -y -v /dev/sda2**. This did not work. It ended with "e2fsck aborted". I could not repair the Ubuntu partition,
I tried to open the sda2 partition by running the terminal command [code] **sudo mount /dev/sda2 /mnt**. I received the following message:

[B]mount:  wrong fs type, bad option, bad superblock on /dev/sda2
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so[/B]

Using the ntfs-config program, I can easily mount the Windows XP partition (sda1). It mounts and I can read or write the files on the Windows XP partition. So at least Windows XP is not damaged.

Hi and welcome to the forums :-)

From the LiveCD, run the following command and post the output here (wrap with code tags as with the script):
[CODE]sudo dumpe2fs /dev/sda2 | grep -i superblock
```

---

### Post by roxat on 2011-02-13
To Rubi1200:

As you suggested, in a terminal I ran
```
sudo dumpe2fs /dev/sda2 | grep -i superblock
```

Terminal responded with the following message:

dumpe2fs 1.41.11 (14-Mar-2010)
Journal superblock magic number invalid!

What now?

roxat

---

### Post by Rubi1200 on 2011-02-13
Hi roxat,
then try this command instead:
```
sudo mke2fs -n /dev/sda2
```

---

### Post by roxat on 2011-02-13
[FONT=monospace]To: Rubi1200

OK, in a terminal I ran

[/FONT]```
sudo mke2fs -n /dev/sda2
```

Here is what I got back:

```
 mke2fs 1,41.11 (14-Mar-2010)
              warning: 164 blocks unused.

              Filesystem label=
              OS type: Linux
        .     Block size=4096 (log=2)
              Fragment size=4096 (log=2)
              Stride=0 blocks, Stripe width=0 blocks
              12476160 inodes, 49807360 blocks
              2490376 blocks (5.00%) reserved for the super user
              First data block=0
              Maximum filesystem blocks=0
              1520 block groups
              32768 blocks per group, 32768 fragments per group
              8208 inodes per group
              Superblock backups stored on blocks:
                             32768, 98304, 163840, 229376, 284912, 819200, 884736, 1605632, 2654208, 
                             4096000, 7962624, 11239424, 20480000, 23887872
              
```

What next?

roxat

---

### Post by Rubi1200 on 2011-02-13
Caveat: what I am about to suggest might fix things, but then again...

If you understand the risks, then we can try it, but if not then you should run this command first to make a backup of everything:

```
dd if=/dev/sda2 of=/disk2/backup-sda2.img
```In the command, substitute disk2 with the actual designation for an external HDD or USB (whatever will be large enough to hold the whole partition that you are about to copy).

Once you have done that, try this command on the damaged file-system:

```
e2fsck -f -b 32768 /dev/sda2
```If this superblock does not work, use the next one in the list (from the command you ran before)

Oh, and if this does work, i.e. no errors reported, you should be able to reboot taking out the LiveCD and be back in Ubuntu (I hope).

If things go wrong, you can always restore the image you just backed up or use something like Testdisk to try and recover files etc.

I want to point out again that this is risky and if you are not comfortable with doing this then don't.

You may also want to wait for input from other users for possible solutions.

---

### Post by roxat on 2011-02-13
To: Rubi1200

While I was waiting for your answer, I booted from an Ubuntu live CD, and I opened gparted.  Then I thought I would run another e2fsck check of my sda2 partition using gparted. When gparted runs a check it does 
```
e2fsck -f -y -v /dev/sda2
```

Here are the results of the check by gparted.

```
GParted 0.5.1

Libparted 2.2
Check and repair file system (ext3) on /dev/sda2  00:02:30    ( ERROR )
         
calibrate /dev/sda2  00:00:00    ( SUCCESS )
         
path: /dev/sda2
start: 399102795
end: 797562989
size: 398460195 (190.00 GiB)
check file system on /dev/sda2 for errors and (if possible) fix them  00:02:30    ( ERROR )
         
e2fsck -f -y -v /dev/sda2
         
e2fsck: Group descriptors look bad... trying backup blocks...
Resize inode not valid. Recreate? yes

Pass 1: Checking inodes, blocks, and sizes
Group 0's inode table at 15 conflicts with some other fs block.
Relocate? yes

Group 0's block bitmap at 13 conflicts with some other fs block.
Relocate? yes

Group 0's inode bitmap at 14 conflicts with some other fs block.
Relocate? yes

Group 1's inode table at 32783 conflicts with some other fs block.
Relocate? yes

Group 1's block bitmap at 32781 conflicts with some other fs block.
Relocate? yes

Group 1's inode bitmap at 32782 conflicts with some other fs block.
Relocate? yes

Group 3's inode table at 98319 conflicts with some other fs block.
Relocate? yes

Group 3's block bitmap at 98317 conflicts with some other fs block.
Relocate? yes

Group 3's inode bitmap at 98318 conflicts with some other fs block.
Relocate? yes

Group 5's inode table at 163855 conflicts with some other fs block.
Relocate? yes

Group 5's block bitmap at 163853 conflicts with some other fs block.
Relocate? yes

Group 5's inode bitmap at 163854 conflicts with some other fs block.
Relocate? yes

Group 7's inode table at 229391 conflicts with some other fs block.
Relocate? yes

Group 7's block bitmap at 229389 conflicts with some other fs block.
Relocate? yes

Group 7's inode bitmap at 229390 conflicts with some other fs block.
Relocate? yes

Group 9's inode table at 294927 conflicts with some other fs block.
Relocate? yes

Group 9's block bitmap at 294925 conflicts with some other fs block.
Relocate? yes

Group 9's inode bitmap at 294926 conflicts with some other fs block.
Relocate? yes

Group 25's inode table at 819215 conflicts with some other fs block.
Relocate? yes

Group 25's block bitmap at 819213 conflicts with some other fs block.
Relocate? yes

Group 25's inode bitmap at 819214 conflicts with some other fs block.
Relocate? yes

Group 27's inode table at 884751 conflicts with some other fs block.
Relocate? yes

Group 27's block bitmap at 884749 conflicts with some other fs block.
Relocate? yes

Group 27's inode bitmap at 884750 conflicts with some other fs block.
Relocate? yes

Group 49's inode table at 1605647 conflicts with some other fs block.
Relocate? yes

Group 49's block bitmap at 1605645 conflicts with some other fs block.
Relocate? yes

Group 49's inode bitmap at 1605646 conflicts with some other fs block.
Relocate? yes

Group 81's inode table at 2654223 conflicts with some other fs block.
Relocate? yes

Group 81's block bitmap at 2654221 conflicts with some other fs block.
Relocate? yes

Group 81's inode bitmap at 2654222 conflicts with some other fs block.
Relocate? yes

Group 125's inode table at 4096015 conflicts with some other fs block.
Relocate? yes

Group 125's block bitmap at 4096013 conflicts with some other fs block.
Relocate? yes

Group 125's inode bitmap at 4096014 conflicts with some other fs block.
Relocate? yes

Group 243's inode table at 7962639 conflicts with some other fs block.
Relocate? yes

Group 243's block bitmap at 7962637 conflicts with some other fs block.
Relocate? yes

Group 243's inode bitmap at 7962638 conflicts with some other fs block.
Relocate? yes

Group 343's inode table at 11239439 conflicts with some other fs block.
Relocate? yes

Group 343's block bitmap at 11239437 conflicts with some other fs block.
Relocate? yes

Group 343's inode bitmap at 11239438 conflicts with some other fs block.
Relocate? yes

Group 625's inode table at 20480015 conflicts with some other fs block.
Relocate? yes

Group 625's block bitmap at 20480013 conflicts with some other fs block.
Relocate? yes

Group 625's inode bitmap at 20480014 conflicts with some other fs block.
Relocate? yes

Group 729's inode table at 23887887 conflicts with some other fs block.
Relocate? yes

Group 729's block bitmap at 23887885 conflicts with some other fs block.
Relocate? yes

Group 729's inode bitmap at 23887886 conflicts with some other fs block.
Relocate? yes

Inode 1 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Root inode is not a directory. Clear? yes

Inode 8, i_blocks is 0, should be 262408. Fix? yes

Inode 17 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 33 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 49 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 65 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 81 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 97 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 113 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 129 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 145 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 161 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 177 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 193 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 209 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 225 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 241 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 257 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 273 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 289 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 305 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 321 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 337 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 353 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 369 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 385 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 401 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 417 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 433 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 449 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 465 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 481 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 497 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 513 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 529 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 545 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 561 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 577 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 593 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 609 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 625 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 641 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 657 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 673 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 689 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 705 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 721 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 737 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 753 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 769 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 785 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 801 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 817 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 833 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 849 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 865 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 881 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 897 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 913 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 929 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 945 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 961 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 977 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 993 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1009 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1025 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1041 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1057 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1073 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1089 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1105 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1121 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1137 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1153 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1169 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1185 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1201 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1217 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1233 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1249 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1265 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1281 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1297 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1313 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1329 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1345 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1361 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1377 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1393 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1409 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1425 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1441 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1457 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1473 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1489 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1505 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1521 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1537 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1553 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1569 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1585 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1601 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1617 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1633 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1649 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1665 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1681 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1697 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1713 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1729 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1745 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1761 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1777 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1793 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1809 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1825 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1841 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1857 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1873 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1889 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1905 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1921 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1937 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1953 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1969 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1985 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2001 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2017 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2033 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2049 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2065 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2081 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2097 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2113 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2129 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2145 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2161 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2177 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2193 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2209 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2225 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2241 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2257 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2273 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2289 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2305 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2321 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2337 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2353 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2369 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2385 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2401 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2417 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2433 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2449 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2465 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2481 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2497 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2513 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2529 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2545 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2561 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2577 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2593 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2609 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2625 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2641 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2657 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2673 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2689 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2705 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2721 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2737 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2753 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2769 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2785 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2801 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2817 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2833 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2849 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2865 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2881 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2897 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2913 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2929 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2945 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2961 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2977 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2993 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3009 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3025 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3041 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3057 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3073 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3089 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3105 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3121 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3137 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3153 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3169 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3185 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3201 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3217 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3233 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3249 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3265 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3281 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3297 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3313 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3329 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3345 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3361 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3377 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3393 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3409 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3425 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3441 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3457 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3473 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3489 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3505 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3521 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3537 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3553 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3569 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3585 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3601 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3617 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3633 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3649 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3665 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3681 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3697 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3713 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3729 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3745 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3761 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3777 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3793 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3809 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3825 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3841 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3857 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3873 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3889 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3905 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3921 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3937 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3953 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3969 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3985 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4001 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4017 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4033 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4049 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4065 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4081 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4097 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4113 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4129 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4145 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4161 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4177 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4193 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4209 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4225 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4241 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4257 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4273 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4289 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4305 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4321 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4337 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4353 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4369 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4385 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4401 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4417 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4433 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4449 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4465 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4481 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4497 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4513 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4529 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4545 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4561 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4577 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4593 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4609 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4625 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4641 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4657 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4673 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4689 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4705 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4721 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4737 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4753 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4769 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4785 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4801 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4817 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4833 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4849 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4865 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4881 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4897 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4913 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4929 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4945 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4961 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4977 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4993 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5009 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5025 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5041 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5057 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5073 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5089 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5105 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5121 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5137 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5153 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5169 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5185 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5201 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5217 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5233 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5249 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5265 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5281 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5297 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5313 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5329 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5345 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5361 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5377 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5393 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5409 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5425 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5441 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5457 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5473 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5489 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5505 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5521 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5537 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5553 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5569 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5585 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5601 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5617 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5633 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5649 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5665 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5681 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5697 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5713 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5729 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5745 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5761 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5777 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5793 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5809 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5825 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5841 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5857 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5873 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5889 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5905 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5921 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5937 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5953 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5969 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5985 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6001 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6017 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6033 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6049 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6065 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6081 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6097 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6113 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6129 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6145 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6161 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6177 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6193 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6209 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6225 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6241 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6257 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6273 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6289 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6305 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6321 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6337 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6353 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6369 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6385 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6401 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6417 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6433 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6449 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6465 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6481 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6497 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6513 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6529 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6545 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6561 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6577 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6593 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6609 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6625 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6641 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6657 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6673 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6689 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6705 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6721 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6737 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6753 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6769 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6785 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6801 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6817 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6833 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6849 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6865 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6881 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6897 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6913 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6929 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6945 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6961 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6977 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6993 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7009 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7025 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7041 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7057 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7073 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7089 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7105 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7121 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7137 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7153 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7169 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7185 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7201 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7217 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7233 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7249 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7265 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7281 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7297 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7313 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7329 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7345 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7361 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7377 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7393 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7409 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7425 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7441 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7457 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7473 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7489 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7505 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7521 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7537 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7553 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7569 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7585 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7601 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7617 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7633 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7649 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7665 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7681 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7697 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7713 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7729 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7745 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7761 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7777 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7793 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7809 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7825 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7841 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7857 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7873 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7889 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7905 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7921 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7937 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7953 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7969 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7985 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8001 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8017 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8033 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8049 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8065 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8081 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8097 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8113 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8129 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8145 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8161 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8177 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 405966 has illegal block(s). Clear? yes

Illegal block #17 (1297578584) in inode 405966. CLEARED.
Inode 407104 has illegal block(s). Clear? yes

Illegal block #17 (1297578584) in inode 407104. CLEARED.
Inode 407190 has illegal block(s). Clear? yes

Illegal block #17 (1297578584) in inode 407190. CLEARED.
Relocating group 0's block bitmap from 13 to 1032...
Relocating group 0's inode bitmap from 14 to 1033...
Relocating group 0's inode table from 15 to 1820...
Relocating group 1's block bitmap from 32781 to 33810...
Relocating group 1's inode bitmap from 32782 to 33811...
Relocating group 1's inode table from 32783 to 33812...
Relocating group 3's block bitmap from 98317 to 99336...
Relocating group 3's inode bitmap from 98318 to 99337...
Error allocating 512 contiguous block(s) in block group 3 for inode table: Could not allocate block in ext2 filesystem
Relocating group 5's block bitmap from 163853 to 164872...
Relocating group 5's inode bitmap from 163854 to 164873...
Error allocating 512 contiguous block(s) in block group 5 for inode table: Could not allocate block in ext2 filesystem
Relocating group 7's block bitmap from 229389 to 230408...
Relocating group 7's inode bitmap from 229390 to 230409...
Error allocating 512 contiguous block(s) in block group 7 for inode table: Could not allocate block in ext2 filesystem
Relocating group 9's block bitmap from 294925 to 295944...
Relocating group 9's inode bitmap from 294926 to 295945...
Error allocating 512 contiguous block(s) in block group 9 for inode table: Could not allocate block in ext2 filesystem
Relocating group 25's block bitmap from 819213 to 820232...
Relocating group 25's inode bitmap from 819214 to 820233...
Error allocating 512 contiguous block(s) in block group 25 for inode table: Could not allocate block in ext2 filesystem
Relocating group 27's block bitmap from 884749 to 885768...
Relocating group 27's inode bitmap from 884750 to 885769...
Error allocating 512 contiguous block(s) in block group 27 for inode table: Could not allocate block in ext2 filesystem
Relocating group 49's block bitmap from 1605645 to 1606664...
Relocating group 49's inode bitmap from 1605646 to 1606665...
Error allocating 512 contiguous block(s) in block group 49 for inode table: Could not allocate block in ext2 filesystem
Relocating group 81's block bitmap from 2654221 to 2655240...
Relocating group 81's inode bitmap from 2654222 to 2655241...
Error allocating 512 contiguous block(s) in block group 81 for inode table: Could not allocate block in ext2 filesystem
Relocating group 125's block bitmap from 4096013 to 4097032...
Relocating group 125's inode bitmap from 4096014 to 4097033...
Error allocating 512 contiguous block(s) in block group 125 for inode table: Could not allocate block in ext2 filesystem
Relocating group 243's block bitmap from 7962637 to 7963656...
Relocating group 243's inode bitmap from 7962638 to 7963657...
Relocating group 243's inode table from 7962639 to 7963658...
Relocating group 343's block bitmap from 11239437 to 11240456...
Relocating group 343's inode bitmap from 11239438 to 11240457...
Error allocating 512 contiguous block(s) in block group 343 for inode table: Could not allocate block in ext2 filesystem
Relocating group 625's block bitmap from 20480013 to 20481032...
Relocating group 625's inode bitmap from 20480014 to 20481033...
Relocating group 625's inode table from 20480015 to 20481034...
Relocating group 729's block bitmap from 23887885 to 23888904...
Relocating group 729's inode bitmap from 23887886 to 23888905...
Relocating group 729's inode table from 23887887 to 23888906...
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: aborted
```

Take a look at the above, and tell me if there ate any obvious errors.

Thank you!


roxat

---

### Post by roxat on 2011-02-13
I will try ```
e2fsck -f -b 32768 /dev/sda2
```

and post the results here. I will also try all the other superblock backups.

roxat

---

### Post by Rubi1200 on 2011-02-13
I have also asked someone else to offer advice here, so if you can wait that would be also a good idea.

In any event, good luck!

---

### Post by roxat on 2011-02-13
To: Rubi1200

Well, in a terminal I ran
```

e2fsck -f -b 32768 /dev/sda2 
```.

I ran this 14 times with every superblock backup that was listed by mke2fs -n /dev/sda2. Every time the e2fsck aborted. The last one that I ran is listed below.

```

sudo e2fsck  -f -b 23887872 /dev/sda2

 Resize inode not valid.  Recreate? yes

Pass 1: Checking inodes, blocks, and sizes
Group 0's inode table at 15 conflicts with some other fs block.
Relocate? yes

Group 0's block bitmap at 13 conflicts with some other fs block.
Relocate? yes

Group 0's inode bitmap at 14 conflicts with some other fs block.
Relocate? yes

Group 1's inode table at 32783 conflicts with some other fs block.
Relocate? yes

Group 1's block bitmap at 32781 conflicts with some other fs block.
Relocate? yes

Group 1's inode bitmap at 32782 conflicts with some other fs block.
Relocate? yes

Group 3's inode table at 98319 conflicts with some other fs block.
Relocate? yes

Group 3's block bitmap at 98317 conflicts with some other fs block.
Relocate? yes

Group 3's inode bitmap at 98318 conflicts with some other fs block.
Relocate? yes

Group 5's inode table at 163855 conflicts with some other fs block.
Relocate? yes

Group 5's block bitmap at 163853 conflicts with some other fs block.
Relocate? yes

Group 5's inode bitmap at 163854 conflicts with some other fs block.
Relocate? yes

Group 7's inode table at 229391 conflicts with some other fs block.
Relocate? yes

Group 7's block bitmap at 229389 conflicts with some other fs block.
Relocate? yes

Group 7's inode bitmap at 229390 conflicts with some other fs block.
Relocate? yes

Group 9's inode table at 294927 conflicts with some other fs block.
Relocate? yes

Group 9's block bitmap at 294925 conflicts with some other fs block.
Relocate? yes

Group 9's inode bitmap at 294926 conflicts with some other fs block.
Relocate? yes

Group 25's inode table at 819215 conflicts with some other fs block.
Relocate? yes

Group 25's block bitmap at 819213 conflicts with some other fs block.
Relocate? yes

Group 25's inode bitmap at 819214 conflicts with some other fs block.
Relocate? yes

Group 27's inode table at 884751 conflicts with some other fs block.
Relocate? yes

Group 27's block bitmap at 884749 conflicts with some other fs block.
Relocate? yes

Group 27's inode bitmap at 884750 conflicts with some other fs block.
Relocate? yes

Group 49's inode table at 1605647 conflicts with some other fs block.
Relocate? yes

Group 49's block bitmap at 1605645 conflicts with some other fs block.
Relocate? yes

Group 49's inode bitmap at 1605646 conflicts with some other fs block.
Relocate? yes

Group 81's inode table at 2654223 conflicts with some other fs block.
Relocate? yes

Group 81's block bitmap at 2654221 conflicts with some other fs block.
Relocate? yes

Group 81's inode bitmap at 2654222 conflicts with some other fs block.
Relocate? yes

Group 125's inode table at 4096015 conflicts with some other fs block.
Relocate? yes

Group 125's block bitmap at 4096013 conflicts with some other fs block.
Relocate? yes

Group 125's inode bitmap at 4096014 conflicts with some other fs block.
Relocate? yes

Group 243's inode table at 7962639 conflicts with some other fs block.
Relocate? yes

Group 243's block bitmap at 7962637 conflicts with some other fs block.
Relocate? yes

Group 243's inode bitmap at 7962638 conflicts with some other fs block.
Relocate? yes

Group 343's inode table at 11239439 conflicts with some other fs block.
Relocate? yes

Group 343's block bitmap at 11239437 conflicts with some other fs block.
Relocate? yes

Group 343's inode bitmap at 11239438 conflicts with some other fs block.
Relocate? yes

Group 625's inode table at 20480015 conflicts with some other fs block.
Relocate? yes

Group 625's block bitmap at 20480013 conflicts with some other fs block.
Relocate? yes

Group 625's inode bitmap at 20480014 conflicts with some other fs block.
Relocate? yes

Group 729's inode table at 23887887 conflicts with some other fs block.
Relocate? yes

Group 729's block bitmap at 23887885 conflicts with some other fs block.
Relocate? yes

Group 729's inode bitmap at 23887886 conflicts with some other fs block.
Relocate? yes

Inode 1 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Root inode is not a directory.  Clear? yes

Inode 8, i_blocks is 0, should be 262408.  Fix? yes

Inode 17 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 33 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 49 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 65 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 81 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 97 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 113 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 129 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 145 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 161 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 177 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 193 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 209 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 225 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 241 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 257 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 273 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 289 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 305 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 321 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 337 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 353 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 369 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 385 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 401 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 417 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 433 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 449 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 465 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 481 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 497 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 513 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 529 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 545 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 561 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 577 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 593 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 609 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 625 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 641 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 657 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 673 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 689 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 705 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 721 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 737 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 753 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 769 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 785 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 801 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 817 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 833 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 849 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 865 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 881 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 897 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 913 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 929 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 945 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 961 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 977 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 993 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1009 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1025 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1041 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1057 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1073 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1089 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1105 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1121 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1137 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1153 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1169 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1185 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1201 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1217 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1233 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1249 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1265 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1281 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1297 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1313 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1329 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1345 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1361 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1377 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1393 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1409 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1425 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1441 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1457 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1473 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1489 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1505 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1521 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1537 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1553 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1569 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1585 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1601 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1617 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1633 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1649 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1665 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1681 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1697 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1713 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1729 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1745 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1761 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1777 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1793 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1809 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1825 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1841 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1857 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1873 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1889 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1905 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1921 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1937 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1953 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1969 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 1985 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2001 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2017 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2033 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2049 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2065 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2081 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2097 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2113 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2129 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2145 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2161 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2177 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2193 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2209 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2225 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2241 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2257 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2273 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2289 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2305 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2321 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2337 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2353 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2369 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2385 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2401 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2417 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2433 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2449 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2465 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2481 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2497 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2513 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2529 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2545 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2561 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2577 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2593 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2609 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2625 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2641 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2657 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2673 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2689 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2705 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2721 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2737 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2753 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2769 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2785 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2801 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2817 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2833 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2849 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2865 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2881 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2897 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2913 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2929 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2945 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2961 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2977 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2993 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3009 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3025 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3041 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3057 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3073 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3089 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3105 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3121 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3137 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3153 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3169 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3185 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3201 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3217 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3233 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3249 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3265 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3281 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3297 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3313 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3329 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3345 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3361 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3377 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3393 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3409 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3425 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3441 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3457 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3473 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3489 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3505 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3521 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3537 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3553 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3569 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3585 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3601 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3617 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3633 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3649 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3665 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3681 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3697 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3713 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3729 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3745 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3761 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3777 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3793 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3809 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3825 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3841 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3857 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3873 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3889 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3905 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3921 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3937 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3953 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3969 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3985 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4001 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4017 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4033 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4049 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4065 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4081 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4097 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4113 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4129 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4145 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4161 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4177 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4193 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4209 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4225 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4241 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4257 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4273 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4289 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4305 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4321 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4337 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4353 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4369 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4385 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4401 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4417 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4433 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4449 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4465 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4481 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4497 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4513 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4529 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4545 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4561 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4577 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4593 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4609 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4625 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4641 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4657 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4673 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4689 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4705 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4721 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4737 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4753 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4769 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4785 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4801 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4817 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4833 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4849 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4865 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4881 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4897 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4913 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4929 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4945 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4961 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4977 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 4993 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5009 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5025 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5041 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5057 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5073 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5089 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5105 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5121 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5137 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5153 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5169 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5185 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5201 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5217 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5233 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5249 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5265 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5281 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5297 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5313 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5329 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5345 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5361 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5377 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5393 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5409 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5425 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5441 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5457 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5473 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5489 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5505 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5521 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5537 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5553 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5569 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5585 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5601 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5617 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5633 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5649 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5665 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5681 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5697 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5713 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5729 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5745 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5761 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5777 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5793 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5809 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5825 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5841 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5857 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5873 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5889 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5905 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5921 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5937 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5953 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5969 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 5985 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6001 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6017 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6033 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6049 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6065 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6081 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6097 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6113 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6129 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6145 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6161 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6177 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6193 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6209 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6225 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6241 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6257 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6273 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6289 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6305 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6321 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6337 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6353 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6369 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6385 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6401 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6417 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6433 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6449 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6465 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6481 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6497 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6513 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6529 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6545 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6561 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6577 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6593 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6609 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6625 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6641 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6657 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6673 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6689 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6705 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6721 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6737 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6753 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6769 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6785 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6801 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6817 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6833 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6849 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6865 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6881 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6897 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6913 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6929 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6945 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6961 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6977 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 6993 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7009 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7025 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7041 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7057 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7073 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7089 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7105 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7121 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7137 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7153 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7169 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7185 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7201 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7217 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7233 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7249 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7265 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7281 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7297 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7313 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7329 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7345 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7361 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7377 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7393 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7409 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7425 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7441 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7457 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7473 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7489 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7505 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7521 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7537 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7553 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7569 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7585 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7601 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7617 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7633 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7649 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7665 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7681 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7697 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7713 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7729 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7745 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7761 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7777 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7793 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7809 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7825 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7841 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7857 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7873 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7889 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7905 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7921 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7937 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7953 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7969 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 7985 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8001 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8017 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8033 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8049 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8065 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8081 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8097 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8113 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8129 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8145 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8161 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8177 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 405966 has illegal block(s).  Clear? yes

Illegal block #17 (1297628569) in inode 405966.  CLEARED.
Inode 407104 has illegal block(s).  Clear? yes

Illegal block #17 (1297628569) in inode 407104.  CLEARED.
Inode 407190 has illegal block(s).  Clear? yes

Illegal block #17 (1297628569) in inode 407190.  CLEARED.
Relocating group 0's block bitmap from 13 to 1032...
Relocating group 0's inode bitmap from 14 to 1033...
Relocating group 0's inode table from 15 to 1820...
Relocating group 1's block bitmap from 32781 to 33810...
Relocating group 1's inode bitmap from 32782 to 33811...
Relocating group 1's inode table from 32783 to 33812...
Relocating group 3's block bitmap from 98317 to 99336...
Relocating group 3's inode bitmap from 98318 to 99337...
Error allocating 512 contiguous block(s) in block group 3 for inode table: Could not allocate block in ext2 filesystem
Relocating group 5's block bitmap from 163853 to 164872...
Relocating group 5's inode bitmap from 163854 to 164873...
Error allocating 512 contiguous block(s) in block group 5 for inode table: Could not allocate block in ext2 filesystem
Relocating group 7's block bitmap from 229389 to 230408...
Relocating group 7's inode bitmap from 229390 to 230409...
Error allocating 512 contiguous block(s) in block group 7 for inode table: Could not allocate block in ext2 filesystem
Relocating group 9's block bitmap from 294925 to 295944...
Relocating group 9's inode bitmap from 294926 to 295945...
Error allocating 512 contiguous block(s) in block group 9 for inode table: Could not allocate block in ext2 filesystem
Relocating group 25's block bitmap from 819213 to 820232...
Relocating group 25's inode bitmap from 819214 to 820233...
Error allocating 512 contiguous block(s) in block group 25 for inode table: Could not allocate block in ext2 filesystem
Relocating group 27's block bitmap from 884749 to 885768...
Relocating group 27's inode bitmap from 884750 to 885769...
Error allocating 512 contiguous block(s) in block group 27 for inode table: Could not allocate block in ext2 filesystem
Relocating group 49's block bitmap from 1605645 to 1606664...
Relocating group 49's inode bitmap from 1605646 to 1606665...
Error allocating 512 contiguous block(s) in block group 49 for inode table: Could not allocate block in ext2 filesystem
Relocating group 81's block bitmap from 2654221 to 2655240...
Relocating group 81's inode bitmap from 2654222 to 2655241...
Error allocating 512 contiguous block(s) in block group 81 for inode table: Could not allocate block in ext2 filesystem
Relocating group 125's block bitmap from 4096013 to 4097032...
Relocating group 125's inode bitmap from 4096014 to 4097033...
Error allocating 512 contiguous block(s) in block group 125 for inode table: Could not allocate block in ext2 filesystem
Relocating group 243's block bitmap from 7962637 to 7963656...
Relocating group 243's inode bitmap from 7962638 to 7963657...
Relocating group 243's inode table from 7962639 to 7963658...
Relocating group 343's block bitmap from 11239437 to 11240456...
Relocating group 343's inode bitmap from 11239438 to 11240457...
Error allocating 512 contiguous block(s) in block group 343 for inode table: Could not allocate block in ext2 filesystem
Relocating group 625's block bitmap from 20480013 to 20481032...
Relocating group 625's inode bitmap from 20480014 to 20481033...
Relocating group 625's inode table from 20480015 to 20481034...
Relocating group 729's block bitmap from 23887885 to 23888904...
Relocating group 729's inode bitmap from 23887886 to 23888905...
Relocating group 729's inode table from 23887887 to 23888906...
e2fsck: aborted

```

Any more advice?

Thanks!

roxat

---

### Post by Rubi1200 on 2011-02-13
Was the file-system always ext3? 

The default for 10.04 is ext4. I know it is sort of irrelevant now, but it might explain what went wrong.

I am out of ideas except that you might want to try Testdisk as a last option to either recover the partition and/or any data:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I hope this helps.

---

### Post by JBA2337 on 2011-02-13
deleted

---

### Post by roxat on 2011-02-13
> **Rubi1200 said:**
> Was the file-system always ext3? 

The default for 10.04 is ext4. I know it is sort of irrelevant now, but it might explain what went wrong.

I am out of ideas except that you might want to try Testdisk as a last option to either recover the partition and/or any data:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I hope this helps.
_________________________________________________________________________________________

To: Rubi1200

Yes, my file system has always been ext3. I use ext3 instead of ext4, so that I can access the Linux partition when I am running Windows XP. The program I am using in Windows to access Linux (Ext2fsd) does not work with ext4. By the way, do you know of a Windows-compatible program that can read and write to an ext4 partition?

I already ran Testdisk earlier this week, and using it I rewrote both the ntfs and the ext3 partitions, but that did not help solve my problem.

I have a backup on another hard disk of most of the files and data that I created while using Ubuntu, except for the last 2 weeks. I was hoping to avoid re-formatting the ext3 partition, but I guess now that is my only choice. 

**Thank you very much** for all of your help with this problem. I guess I will go ahead and re-install Ubuntu, and allow formatting of the partition.

roxat

---

### Post by Rubi1200 on 2011-02-14
Sorry for the delayed response; forum upgrade

Unless you can recover some files with Testdisk, you may have little choice but to reformat and reinstall.

in any event, good luck :-)

---

### Post by roxat on 2011-02-14
> **Rubi1200 said:**
> Sorry for the delayed response; forum upgrade

Unless you can recover some files with Testdisk, you may have little choice but to reformat and reinstall.

in any event, good luck :-)
__________________________________________________________________________

To Rubi1200:

After screwing around with my computer, I can now use Windows XP. I  guess TestDisk must have fixed that, but Ubuntu still won't work. Its not mountable, and I can't even read any of the files in the partition. For the past year I have enjoyed using Ubuntu a lot more than Windows (I only use Windows when I have to). So I guess I will go ahead and format the ext3 partition with the latest version of Ubuntu.

Thanks a lot for all of your help. Bye.

roxat

---

