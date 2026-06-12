---
title: "Another convert?"
date: 2011-11-15
forum: General Help
---

### Post by Rich J on 2011-11-15
Hi Everyone!  I am a Linux newbie looking to change over from Vista and would appreciate some basic advice!

I am running Ubuntu 11.10 as 2nd o/s to Vista as a precursor to swapping o/s's in the near future.  I **believe** that I'm dual-booting  :confused: - but there is some confusion over this as I used WUBI to help me install Ubuntu.  (Ubuntu is on it's own partition (B, and appears as 2nd choice in the boot menu).  I switched to Gnome desktop as I found Unity a bit too difficult to get my head around and so far so good, I'm slowly learning the ways of Linux- and I like every much what I see!  My problem at this stage is:

My pc came with Vista Home Premium pre-installed as an OEM version so I don't have any installation disks.  I've been advised that some proprietary pc's with this sort of configuration on the HDD can not be re-formatted and a different o/s to Windows installed in it's place - due to certain chips on the motherboard being 'flashed' therefore only recognizing Windows systems.  Is this true?  And if so, is there anything I can do to change this?

I would have preferred to have had a separate pc on which to evaluate Ubuntu but these are hard times in the UK!  I don't want to attempt a new install of Ubuntu only to find the o/s won't run and have no way of reinstalling Vista due to the lack of disks!

Any help on this (and I'm sure many other points in the future!) would be appreciated!

Thanks in advance

Rich J

PS - I know Windows can be mighty finicky if 'interfered with'!  I've had a few BSOD's already but at the moment Vista is stable!  Ubuntu has run fine from the off!

---

### Post by westie457 on 2011-11-15
Hello, welcome to the Forum.

Before you go any further with this here are some suggestions\recommendations for you.

1, Make a backup copy to dvd of the recovery partition. For the worst case scenario of a complete reinstall or if you wish to pass on the computer in the future.

2, Use Windows to make a Repair Disc to fix some Windows issues.

3, Make a complete backup of your Windows partition. This is a quicker way to reinstall than using the 'Recovery Partition.
Two recommended programs for this are 'Cloneilla' and 'Macrium Reflect'

These suggestions are in no order of importance. They are all vital. It is never to early to have backups however without one it is too late when the system gets hosed accidentally.

---

### Post by BillyBoa on 2011-11-15
> **Rich J said:**
> 
I am running Ubuntu 11.10 as 2nd o/s to Vista as a precursor to swapping o/s's in the near future.  I **believe** that I'm dual-booting  :confused: - but there is some confusion over this as I used WUBI to help me install Ubuntu.  (Ubuntu is on it's own partition (B, and appears as 2nd choice in the boot menu).  

Wubi does not make partitions. "It can install and uninstall Ubuntu in the same way as any other Windows application". You install Ubuntu through Wubi, like installing a regular program. Then you can uninstall it without any safety issues.

Doing partitions is a very different thing and in your case is almost impossible, because Vista uses 3 or 4 partitions of it's own, so you have to delete one to create space.....heading to the disaster. So I advise you to stay with Wubi, it's perfect.

---

### Post by jjex22 on 2011-11-15
100% agree with westie if you have issues getting a recovery cd (an essential if you've installed grub (incase you want to remove it) or for rescuing a botched vista look here

[http://www.vistax64.com/tutorials/141820-create-recovery-disc.html?ltr=C](http://www.vistax64.com/tutorials/141820-create-recovery-disc.html?ltr=C)

tbh, If you don't have hdd space issues, I'd say keep vista - windows can always come in handy - bios updates, games, mp3 player compatibility /etc, and you've paid for it!

As to the motherboard being flashed, I haven't encountered this but theoretically it'd just be a bios version designed to only work with the vista bootloader, in which case i'm sure you could just flash the bios from windows, or install easy bcd to the bootloader - tell it to pass on to grub with a time out of 0 and remove windows... simples!

I'd personally keep a dual boot... maybe further reduce the vista partition with gparted if you're not really using it, but as advised BACK UP NOW .. you have been warned.

---

### Post by coffeecat on 2011-11-15
Hi and welcome to the forum!

> **Rich J said:**
> I **believe** that I'm dual-booting  :confused: - but there is some confusion over this as I used WUBI to help me install Ubuntu.  (Ubuntu is on it's own partition (B, and appears as 2nd choice in the boot menu).

A wubi Ubuntu is not in its own partition, but in a virtual drive in the file C:\ubuntu\disks\root.disk. Or it can be in your Windows D: or E: or whatever drive. More here:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

> **Rich J said:**
> I switched to Gnome desktop as I found Unity a bit too difficult to get my head around and so far so good,

If you prefer classic gnome that's just fine, but give Unity a few days and you might find you prefer it. Many do.

> **Rich J said:**
> My pc came with Vista Home Premium pre-installed as an OEM version so I don't have any installation disks.  I've been advised that some proprietary pc's with this sort of configuration on the HDD can not be re-formatted and a different o/s to Windows installed in it's place - due to certain chips on the motherboard being 'flashed' therefore only recognizing Windows systems.  Is this true?  And if so, is there anything I can do to change this?

Two points: most OEM manufacturers provide a utility to create a set of restore DVDs for restoring the machine to factory condition and/or a recovery partition. What make/model is your machine?

I think you may be referring to "secure-boot" which may come in with uEFI machine and Windows 8. This is a watch-this-space and developing situation.

> **Rich J said:**
> I would have preferred to have had a separate pc on which to evaluate Ubuntu but these are hard times in the UK!  I don't want to attempt a new install of Ubuntu only to find the o/s won't run and have no way of reinstalling Vista due to the lack of disks!

Wubi is a good way of trying out Ubuntu and if Ubuntu runs OK on your machine it will run OK if installed natively to its own partition.

> **Rich J said:**
> I know Windows can be mighty finicky if 'interfered with'!  I've had a few BSOD's already but at the moment Vista is stable!  Ubuntu has run fine from the off!

The one disadvantage of wubi is that if the Windows filesystem becomes corrupted, it won't run.

> **BillyBoa said:**
> Wubi does not make partitions. "It can install and uninstall Ubuntu in tDoing partitions is a very different thing and in your case is almost impossible, because Vista uses 3 or 4 partitions of it's own, so you have to delete one to create space.....heading to the disaster. So I advise you to stay with Wubi, it's perfect.

Sorry - I have to correct this. Vista doesn't use 3 or 4 partitions. It can run happily with one partition. The problem is that many manufacturers create several primary partitions in their default setup making it sometimes difficult to create partitions for Linux. This is more of a problem with Windows 7 which often, but not always, has a separate boot partition.

---

### Post by BillyBoa on 2011-11-15
> **Rich J said:**
> 
Sorry - I have to correct this. Vista doesn't use 3 or 4 partitions. It can run happily with one partition. The problem is that many manufacturers create several primary partitions in their default setup making it sometimes difficult to create partitions for Linux. This is more of a problem with Windows 7 which often, but not always, has a separate boot partition.

As far as I now by default Vista creates 2 partitions, one primary and one system boot. Never installed one, so I'm not sure.

[IMG]http://ubuntuforums.org/picture.php?albumid=2449&pictureid=8292[/IMG] 

Windows7 which is a Vista upgrade and uses exactly the same partition system, creates 2 partitions by default, at least the disks I use.

---

### Post by coldraven on 2011-11-15
> **westie457 said:**
> Hello, welcome to the Forum.

Before you go any further with this here are some suggestions\recommendations for you.

1, Make a backup copy to dvd of the recovery partition. For the worst case scenario of a complete reinstall or if you wish to pass on the computer in the future.

2, Use Windows to make a Repair Disc to fix some Windows issues.

3, Make a complete backup of your Windows partition. This is a quicker way to reinstall than using the 'Recovery Partition.
Two recommended programs for this are 'Cloneilla' and 'Macrium Reflect'

These suggestions are in no order of importance. They are all vital. It is never to early to have backups however without one it is too late when the system gets hosed accidentally.
I agree with westie457, Google "making a Windows recovery disk"
He meant to type Clonezilla instead of Cloneilla
Having an USB external makes backing up your data or partitions easy. I recommend that you buy one while they are cheap.

---

### Post by JayKay3OOO on 2011-11-15
> **BillyBoa said:**
> As far as I now by default Vista creates 2 partitions, one primary and one system boot. Never installed one, so I'm not sure.

[IMG]http://ubuntuforums.org/picture.php?albumid=2449&pictureid=8292[/IMG] 

Windows7 which is a Vista upgrade and uses exactly the same partition system, creates 2 partitions by default, at least the disks I use.

Correct & lots of OEM computers have a backup partition to enable users to restore the computer to factory settings by hitting a key on boot.

---

### Post by Rich J on 2011-11-15
Hi Guys!  Wow! Are you part of the Rapid Response Team, or what?  A little more info.......

I'd looked around the net to see which Linux distro would be best suited to a newbie and decided on the latest release of Ubuntu........... on reflection, perhaps an older version of Mint might have been more user-friendly to a Windows user, but no matter......  

I understand that Vista ceases to be supported early next year and I've no real desire to upgrade to another Windows o/s.  I reckon uncle Bill has had enough of my hard-earned cash already!  I find it very wearing to have to constantly update security fixes, bug fixes and all - just to keep my pc from harm and the fact that I can't re-install my o/s thru lack of a disk!  I mean, I paid for the o/s as part of the purchase, it is licensed to me, so why should I be restricted?   Also, this pc still has plenty of life left in it so why spend even more money?  There has to be another way.

I have a 160Gb HDD with Vista on it but with around 80Gb unused space.  (I am only your bog-standard user!) so did a bit of prep, backed up my info etc to an external HDD, then partitioned the drive using Easeus Partition Manager.   My d/l'd Ubuntu disk for some reason wouldn't install to the B partition so I used WUBI to get it on.  It works just fine and can be selected at the first screen after boot.  (This is why I'm not sure if I am really dual-booting or if Ubuntu is installed under Windows)  I'm slowly getting to grips with it and can see me going for it permanently.  My wife, however still wants Vista as she's used to it and 'all my settings are there'.....  (I'm wearing her down slowly!)  I would prefer a clean break with Windows and when the day comes want just the one o/s installed.

Hope that makes things a little clearer!

Thanks again guys!

Thanks for the extras!  I'll reply asap

---

### Post by nothingspecial on 2011-11-15
Sounds to me like you have a wubi install rather than a dual boot.

There should be no reason why the installer on the cd would not allow you to use the 80gig partition.

Would you prefer a dual boot. I've never tried wubi but I beleve you do not get the full performance with it.

---

### Post by coffeecat on 2011-11-15
> **Rich J said:**
> My d/l'd Ubuntu disk for some reason wouldn't install to the B partition so I used WUBI to get it on.  It works just fine and can be selected at the first screen after boot.  (This is why I'm not sure if I am really dual-booting or if Ubuntu is installed under Windows) 

If you used wubi, I agree with nothingspecial - it's the latter.

Whatever - let's see exactly what you've got, how many partitions and then we can advise. Open a terminal (sorry!) and post the output of these two commands:

```
mount
sudo fdisk -lu
```

You'll be prompted for your password with the second but you won't get any feedback when you type it in. Don't worry - it is going in. Please post the output between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by MG&amp;TL on 2011-11-15
> **nothingspecial said:**
> Sounds to me like you have a wubi install rather than a dual boot.

There should be no reason why the installer on the cd would not allow you to use the 80gig partition.

Would you prefer a dual boot. I've never tried wubi but I beleve you do not get the full performance with it.

Depends on the hardware. But it's often buggy, and if you have a laptop mouse or anything unusual, forget it.

---

### Post by jjex22 on 2011-11-15
I think vista must use a form of extended partition - whilst it does create a boot partition it does only use one primary 'slot' on your drive. 

Also If you used Wubi to install you have ubuntu installed on the windows partition - if your boot screen is black with white writing and looks like the 'you did not shut down windows properly' screen - it's wubi, if it's purple and contains words like /dev/sda it's on a seperate partition.

---

### Post by Rich J on 2011-11-15
> **coffeecat said:**
> If you used wubi, I agree with nothingspecial - it's the latter.

Whatever - let's see exactly what you've got, how many partitions and then we can advise. Open a terminal (sorry!) and post the output of these two commands:

```
[code]mount
sudo fdisk -lu
```You'll be prompted for your password with the second but you won't get any feedback when you type it in. Don't worry - it is going in. Please post the output between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button in the message toolbar.[/CODE]```


Hi and thanks for the reply - is this what you need?

richard@ubuntu:~$ mount
/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/richard/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=richard)
richard@ubuntu:~$ sudo fdisk -lu
[sudo] password for richard: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x42d47009

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    11266047     5632000   27  Hidden NTFS WinRE
/dev/sda2   *    11279520   175286159    82003320    7  HPFS/NTFS/exFAT
/dev/sda3       175286160   278253359    51483600    7  HPFS/NTFS/exFAT
richard@ubuntu:~$ 
```

---

### Post by Rich J on 2011-11-15
> **jjex22 said:**
> I think vista must use a form of extended partition - whilst it does create a boot partition it does only use one primary 'slot' on your drive. 

Also If you used Wubi to install you have ubuntu installed on the windows partition -[COLOR=Red] if your boot screen is black with white writing and looks like the 'you did not shut down windows properly' screen - it's wubi,[/COLOR] if it's purple and contains words like /dev/sda it's on a seperate partition.


Hi and thanks for the clarification!  It's the first [COLOR=Red]one[/COLOR]! 

What does happen occasionally - when I've finished with Ubuntu and shut down normally, next boot into Vista (1st in list) **may** generate a BSOD.  Restart gives the usual options about repair/start normally etc.  Choosing repair will **sometimes** generate a 'Windows cannot repair disk at this time' or words to that effect.  However, restart again and vista will load as if nothing has happened!  This, I stress, is random and more often than not Vista will load ok.  Choosing Ubuntu has never been a problem and runs very well.

I put this down to Windows being Windows and acting like a teenage girl - you know, 'why are you looking at her and not at me' sort of thing!!   :rolleyes:

Rich

---

### Post by coffeecat on 2011-11-15
> **Rich J said:**
> is this what you need?

Perfect! First thing, you do have a wubi install, installed in sda3, which is probably your D:/E: drive rather than C:. Your 160GB is partitioned as follows:

sda1 - 5.8GB - probably a hidden manufacturer's restore partition.
sda2 - 84GB - boot flag set. Probably your C: partition.
sda3 - 52.7GB - contains your wubi virtual drive. As above - probably your Windows D: partition.

After that you have 17.5 GB unallocated* which could be used to install Ubuntu to its own partitions.

See what others say, but I would advise this. Don't be in a hurry to install Ubuntu to its own partitions. Continue to use wubi until you are ready. The only real disadvantages of wubi are that it runs a little slower and is vulnerable to host partition filesystem corruption. Its compatibility to hardware is no different than with a native installation.

When you are ready to install Ubuntu "properly" start a new thread with this information and someone will be able to help you. In the meantime, I forgot one command for you to run. Post the output of:

```
sudo blkid
```

That will give us the partition labels, if they have labels, which will tell us whether my assumptions about those partitions are correct.

* **EDIT**: you said 80GB spare, but the fdisk figures are equivalent to 17.5GB.

---

### Post by Rich J on 2011-11-15
> **coffeecat said:**
> Perfect! First thing, you do have a wubi install, installed in sda3, which is probably your D:/E: drive rather than C:. Your 160GB is partitioned as follows:

sda1 - 5.8GB - probably a hidden manufacturer's restore partition.
sda2 - 84GB - boot flag set. Probably your C: partition.
sda3 - 52.7GB - contains your wubi virtual drive. As above - probably your Windows D: partition.

After that you have 17.5 GB unallocated* which could be used to install Ubuntu to its own partitions.

See what others say, but I would advise this. Don't be in a hurry to install Ubuntu to its own partitions. Continue to use wubi until you are ready. The only real disadvantages of wubi are that it runs a little slower and is vulnerable to host partition filesystem corruption. Its compatibility to hardware is no different than with a native installation.

When you are ready to install Ubuntu "properly" start a new thread with this information and someone will be able to help you. In the meantime, I forgot one command for you to run. Post the output of:

```
sudo blkid
```That will give us the partition labels, if they have labels, which will tell us whether my assumptions about those partitions are correct.



```
richard@ubuntu:~$ sudo blkid
[sudo] password for richard: 
/dev/loop0: UUID="b4cfa1f9-56e9-431b-bc9c-74b9d73a7d9f" TYPE="ext4" 
/dev/sda1: UUID="268667D98667A7CF" TYPE="ntfs" 
/dev/sda2: LABEL="Vista" UUID="62847025846FFA45" TYPE="ntfs" 
/dev/sda3: LABEL="Linux" UUID="D2BE648ABE646945" TYPE="ntfs" 
```
[COLOR=Red]* **EDIT**: you said 80GB spare, but the fdisk figures are equivalent to 17.5GB.[/COLOR]

Sorry!  I meant that there was about 80Gb of UNUSED space on the (Vista) C drive.  I shrank the C partition using Easeus PM then tried to install Ubuntu into the remaining space.  The ISO wouldn't install directly to the new partition - I named it B - but I seemed to get it on via WUBI.  Hope this helps?

Incidentally, the Vista partition was mounted and was visible and readable until I ran Terminal!  Now it has disappeared from my /home folder - how do I get it back?

Thanks again for you help

---

### Post by coffeecat on 2011-11-15
Understood. But since you've got approx 17.5 GB at the end of the drive, that's perfect for creating an extended partition in for logical partitions for Ubuntu. Then you will have sda3 (presumably Windows D: ) which you can use as a shared data partition for both Windows and Ubuntu, **if** it's D:.

You don't install the ISO directly onto a partition - you burn it to a CD and boot from the CD to run either the live desktop or the installer.

More here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And something on partitioning which I heartily recommend:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

> **Rich J said:**
> Incidentally, the Vista partition was mounted and was visible and readable until I ran Terminal!  Now it has disappeared from my /home folder - how do I get it back?

The Vista partition won't be visible in /home. With your setup, the C: partition will be listed in the left pane of a file browser window with the partition label if it has one, or something like "84GB filesystem" if not. Simply click on it. Your wubi install is hosted in a separate partition so if you want to open this (the sda3 partition), click on "File System" in the left pane and then open the /host folder.

---

