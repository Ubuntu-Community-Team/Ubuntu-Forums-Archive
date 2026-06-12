---
title: "Ubuntu won't load anymore."
date: 2010-10-09
forum: General Help
---

### Post by Teclas5 on 2010-10-09
Hello my friends. My laptop is running 9.04 and until a few days ago, I had no problems. But now it will not load Ubuntu at all. It says on the screen:

mount: mounting /dev/disk/by-uuid/4b311e55-3c79-44e5-a500-bb29671e6ec2 on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init. 
No init found. Try passing init= bootarg.


Sorry guys, I am a novice, and any help would be most welcome and appreciated.

---

### Post by Rubi1200 on 2010-10-09
Is this a regular install or via Wubi?

Have you recently updated/upgraded anything?

Post the results of the boot-script linked at the bottom of my post. This needs to be done from a LiveCD.

Thanks.

---

### Post by Teclas5 on 2010-10-09
This is the results of the boot-script Rubi1200. And on the contrary, thank *you* for the help. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   189,374,219   189,374,157  83 Linux
/dev/sda2         189,374,220   195,366,464     5,992,245   5 Extended
/dev/sda5         189,374,283   195,366,464     5,992,182  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4b311e55-3c79-44e5-a500-bb29671e6ec2   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6e8369b9-f0b7-48ee-997d-b2e3d362a586   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by Rubi1200 on 2010-10-09
Hi,
It appears your file system has been damaged:
> wrong fs type, bad option, bad superblock on /dev/sda1You need to run this from the LiveCD:

```
sudo e2fsck -C0 -p -f -v /dev/sda1
```If this does not help and there are errors, then try this:

```
sudo e2fsck -f -y -v /dev/sda1
```Let us know what happens please.

---

### Post by Teclas5 on 2010-10-09
Success! Thank you so much Rubi1200! Your script worked like a charm. The first one gave me an error, but the second one did the job. Again, I appreciate your help my friend, lots of karma! :guitar:

---

### Post by Rubi1200 on 2010-10-10
You are more than welcome Teclas5 :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

### Post by BBWin3 on 2010-10-10
*Hello, *
*I am another nubie to **Ubuntu 9.10.** I had exactly the same problem as Teclas5.*
*I performed all of the same inputs suggested by **Rubi1200.** Including error fixes which got me back to the boot menu.THANK YOU for that!.*
 
*Now after starting machine then selecting the first (at the top, Unbuntu 9.10 kernel 2.6.31-22) to boot from,*
*  my machine boots to blank screen. after a bit of time it then it echos back the following:*
 
upsplash: using mode 1024 x 768
Mount: mounting /dev/disk/by-uuid/e760a<long i.d. number.....> a48beaf /on /root
Failed: invalid argument
Mount: Mounting /sys on /root/sys Failed No Such file or Directory.
Mount: Mounting /dev on /root dev Failed No Such file or Directory.
Mount: Mounting /sys on /root/sys Failed No Such file or Directory.
Mount: Mounting /proc on /root/sys Failed No Such file or Directory. 
 
Target file system doesnt have /sbin/init
No init found Try passing init = bootarg
 
BusyBox v. 1.13.3 (Ubuntu 1:1,13,3-1 ubuntu7) built-in shell (ash)
Enter 'help' for list of built-in commands
 
initramfs>
 
***So I tried the following:***
 
initramfs> init = bootarg
 
/bin/sh: init: not found
 
*Any possible help would be most appreciated.*
 
*-Terri,*
*<BBWin3>*

---

### Post by Rubi1200 on 2010-10-16
Please post the results of the boot-script (the way Teclas5 did it) so we can take a closer look at what is happening.

Thanks.

---

### Post by BBWin3 on 2010-10-16
[B]Good Day Rubi1200,

Here are the results from boot info script. I know how it is to be busy.
I can wait however long it takes - no hurry. Your help is truely appreciated.
Thank You, Terri (BBWin3)[/B]

```

```                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 61390911 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e8ab7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   154,031,219   154,031,157  83 Linux
/dev/sda2         154,031,220   160,071,659     6,040,440   5 Extended
/dev/sda5         154,031,283   160,071,659     6,040,377  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4105 MB, 4105175040 bytes
37 heads, 37 sectors/track, 5856 cylinders, total 8017920 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,760     8,017,919     8,015,160   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e760a314-7e3d-4dd6-b724-54e4a48fbeaf   ext3                                     
/dev/sda5        48f21179-5389-4dca-bef9-9498f04247a7   swap                                     
/dev/sdb1        8461-5E71                              vfat       UDISK                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/UDISK             vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

---

### Post by Rubi1200 on 2010-10-16
Run this command from the LiveCD first and post the output please:

```
sudo mke2fs -n /dev/sda1
```

---

### Post by BBWin3 on 2010-10-16
[B]Good Day,

Here are the results of:
sudo mke2fs -n /dev/sda1[/B]
-BBWin3

```

```   	 	 	 	 	 	  ubuntu@ubuntu:~$ sudo mke2fs -n /dev/sda1
 mke2fs 1.41.9 (22-Aug-2009)
 Filesystem label=
 OS type: Linux
 Block size=4096 (log=2)
 Fragment size=4096 (log=2)
 4816896 inodes, 19253894 blocks
 962694 blocks (5.00%) reserved for the super user
 First data block=0
 Maximum filesystem blocks=0
 588 block groups
 32768 blocks per group, 32768 fragments per group
 8192 inodes per group
 Superblock backups stored on blocks:  
 	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,  
 	4096000, 7962624, 11239424

---

### Post by Rubi1200 on 2010-10-16
Thanks for the output. Before we continue, are you able to see and access any of your files from the LiveCD?

If yes, I would suggest you try and save them to an external media such as a USB drive or the like.

There is always a chance that the command I will give you now may not work or even mean that you could lose data.

If you are willing to continue, then run this command from the LiveCD:
```
sudo e2fsck -f -b 32768 /dev/sda1
```
Basically, what we are trying to do is replace the bad superblock that was originally detected in the script.

If this command works, in other words it does not report any errors, then you should be able to boot into the system again.

If there are errors, do not continue, post back here and we will try another option.

---

### Post by HLSolbjorg on 2010-10-16
This worked like a charm for me! Thanks a lot! :D

---

### Post by BBWin3 on 2010-10-16
Hello Again,

I  ran the e2fsck, then I said yes to abort, then I ran it again with no abort
here are the results. I also tried 2 other superblock locations with same results:

```

```   	 	 	 	 	 	  1st run............
 

 ubuntu@ubuntu:~$ sudo e2fsck -f -b 32768 /dev/sda1
 

 e2fsck 1.41.9 (22-Aug-2009)
 Journal version not supported by this e2fsck.
 Abort<y>? yes
 

 ubuntu@ubuntu:~$
 

 

 2nd run............
 

 ubuntu@ubuntu:~$ sudo e2fsck -f -b 32768 /dev/sda1
 

 e2fsck 1.41.9 (22-Aug-2009)
 Journal version not supported by this e2fsck.
 Abort<y>? no
 Journal superblock is corrupt.
 Fix<y>? no
 e2fsck: The ext2 superblock is corrupt while checking ext3 journal for /dev/sda1
 

 ubuntu@ubuntu:~$

---

### Post by Rubi1200 on 2010-10-16
What does the output of this command tell you?

```
dumpe2fs /dev/sda1 | grep -i superblock
```

Just to rewind a little bit, how did you end up in this situation in the first place?

These kinds of errors are usually caused by:
user error
buggy device drivers or utilities
power outages
kernel bugs

Also, which version of Ubuntu was installed on the computer?

Thanks.

---

### Post by BBWin3 on 2010-10-17
Good Day again,
 
Firstly some history: I had skipped over file checking twice... my bad. 
              I believe the hard drive was going bad. 
              And I turned off the computer during one of those-dumb blond- OKAY
              I then ran the suggested file fixes from herman@...  *sudo e2fsck -C0 -p -f -v /dev/sda2.*
Due to error founds on the disk, I ran: * sudo e2fsck -y -f -v /dev/sda2*
              NOTE: I am not sure if I ran the above two commands using /SDA2 or SDA1.
 
So today, I then tried your suggestion. *sudo dumpe2fs /dev/sda1 |grep -i superblock*
 
Output shown below.
 
After that I tried *sudo e2fsck -f -b 162340 /dev/sda1*  again.
 
THIS HAD directoriy and inode count errors.
.... I allowed the program to perform the fixes.
 
AFTER MANY MANY OF THE ABOVE FIXES....>>> SUCCESS!! <<< REBOOTING now NORMAL.:):):)
 
A greatfull thank you for all of your help.
 
Now it is time to backup everything and replace the hard drive.
 
Output of above follows:
```
 
buntu@ubuntu:~$ sudo dumpe2fs /dev/sda1 | grep -i superblock


dumpe2fs 1.41.9 (22-Aug-2009)
Primary superblock at 0, Group descriptors at 1-5
Backup superblock at 32768, Group descriptors at 32769-32773
Backup superblock at 98304, Group descriptors at 98305-98309
Backup superblock at 163840, Group descriptors at 163841-163845
Backup superblock at 229376, Group descriptors at 229377-229381
Backup superblock at 294912, Group descriptors at 294913-294917
Backup superblock at 819200, Group descriptors at 819201-819205
Backup superblock at 884736, Group descriptors at 884737-884741
Backup superblock at 1605632, Group descriptors at 1605633-1605637
Backup superblock at 2654208, Group descriptors at 2654209-2654213
Backup superblock at 4096000, Group descriptors at 4096001-4096005
Backup superblock at 7962624, Group descriptors at 7962625-7962629
Backup superblock at 11239424, Group descriptors at 11239425-11239429
[COLOR=#000080]_[EMAIL="ubuntu@ubuntu"]ubuntu@ubuntu[/EMAIL]_[/COLOR]:~$


Then I tried sudo e2fsck -f -b 163840 /dev/sda1 on the 3rd superblock as follows:


Directories count wrong for group #316 (0, counted=44).
Fix<y>? yes
Free inodes count wrong for group #317 (8192, counted=8161).
Fix<y>? yes
Directories count wrong for group #317 (0, counted=1).
Fix<y>? yes
Free inodes count wrong for group #322 (8192, counted=8093).
Fix<y>? yes
Directories count wrong for group #322 (0, counted=8).
Fix<y>? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 366842/4816896 files (1.6% non-contiguous), 5617412/19253894 blocks
ubuntu@ubuntu:~$ 



```

---

### Post by Rubi1200 on 2010-10-18
Excellent! I am really glad you sorted it out! :) :)

I was actually going to suggest you run the e2fsck again with the -y switch (which would have recursively answered yes to the questions you answered manually).

In any event, take your own advice and save whatever data you can before investing in a new drive.

If you need any additional help, feel free to ask.

And don't forget to drop by the forums now and again, even if you don't have a specific question/problem.

You can learn an enormous amount just by reading posts in the various forum sections.

---

