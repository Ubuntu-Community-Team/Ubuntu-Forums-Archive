---
title: "Mounting a drive in Ubuntu"
date: 2006-03-09
forum: General Help
---

### Post by cabber on 2006-03-09
I have a FAT32 Partitioned drive that I would like to mount be not sure how to do this.  Can someone post a link or walk me through this please.  

I would like to use it with WIndows and Ubuntu to share files between the two os's.  I heard from a few to format and partition to EXT3.  Any upside with that?  

Thanks.

---

### Post by super on 2006-03-09
just cut and paste this into your /etc/fstab file
```
/dev/hd*xy*  /windows   vfat	  iocharset=utf8,umask=000   0       0
```
and if you are going to be dual-booting, then it will be easier for you to keep the fat32 partition to share files

x is your drive assignment (eg: hda, hdb)
y is your partition assignment (eg: hda1, hdb1)

if you encounter any problems, let me know

---

### Post by Sutekh on 2006-03-09
FAT32 is probably the best way to share between Windows / Ubuntu, but I'm prepared to be swayed to ext3.

Before that happens though here is how to setup the FAT32

You need to open a **Terminal** window.  

To start you need to determine the location of your partitions using
```
sudo fdisk -l
```
You can post the output of this command here if you want to make sure that you are choosing the right device.

Once you know the name of the shared drive (/dev/hdb1, /dev/sda1, I can't say for sure), you can edit your **/etc/fstab**.  fstab is a configuration file that contains information regarding your partitions and where they should be mounted.

You should create a backup of the fstab before editing it
```
sudo cp /etc/fstab /etc/fstab_backup
```
Then you can edit it using 
```
sudo gedit /etc/fstab
```

Once you have opened the fstab then you need to add the line to mount the shared drive.  
For a FAT32 partition you should add a line similar to this one
```
[COLOR="Blue"]/dev/hdb1[/COLOR]    [COLOR="Red"]/media/windows[/COLOR]   [COLOR="Green"]vfat[/COLOR]   [COLOR="DarkOrchid"]iocharset=utf8,umask=0000[/COLOR]   0   0
```
 - [COLOR="Blue"]/dev/hdb1[/COLOR] - is the location of the shared drive, you will have to edit this as apropriate from the output of fdisk

 - [COLOR="Red"]/media/windows[/COLOR] - this is the folder where the drive will be mounted.  If this folder doesn't exist you will need to create it yourself ```
sudo mkdir [COLOR="Red"]/media/windows[/COLOR]
```
**Note** you don't have to use [COLOR="Red"]/media/windows[/COLOR], in my system I use [COLOR="Red"]/mnt/os-shared[/COLOR], its up to you

 - [COLOR="Green"]vfat[/COLOR] - this specifies the filesystem as fat

 - [COLOR="DarkOrchid"]iocharset=utf8,umask=0222[/COLOR] - these options set the character encoding to utf8 (for special chars) and sets the **umask**.  [COLOR="DarkOrchid"]umask=0000[/COLOR] allows read, write and execute access to the partition.

Once you've modified the /etc/fstab, you can save it and issue the command```
sudo mount -a
```This re-mounts the partitions, without you having to restart your computer.

---

### Post by harley on 2006-03-09
what if you fstab file is read only?

---

### Post by Sutekh on 2006-03-09
[QUOTE=harley]what if you fstab file is read only?[/QUOTE]
Thats why you need to use ```
**sudo** gedit /etc/fstab
``` To allow you to edit it.

Edit: harley I posted to your thread about mount NTFS partitions

---

### Post by cabber on 2006-03-09
fdisk 1

```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10395    83497806    7  HPFS/NTFS

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4500    36146218+  83  Linux

Disk /dev/sdc: 37.0 GB, 37018484224 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4314    34652173+  83  Linux
/dev/sdc2            4315        4500     1494045    5  Extended
/dev/sdc5            4315        4500     1494013+  82  Linux swap / Solaris

```

I have a 400G with Windows installed 100G Partition so that leaves 300g free to use for files/music/photos, and what not.

I have Linspire installed on a seperate drive (36 gig)

And Ubuntu installed on a third drive (36G)

So as you can see, the drive in focus is the Windows drive.

---

### Post by cabber on 2006-03-09
I have Partition Magic installed on my Windows set up.  Would it be easier to use that instead?

---

### Post by Sutekh on 2006-03-09
Its not formatted FAT32 its formatted NTFS.

So just use this line instead

```
/dev/sda1    /media/windows   ntfs   mls=utf8,umask=0222   0   0
```
Sorry but NTFS can't be written to at this stage in Linux, you can only read and execute files on an NTFS partition.

---

### Post by cabber on 2006-03-09
The drive that Windows is on is a 400G HD.  Windows is partitioned on NTFS for 100G .  The remaining 300 has yet been allocated.  Can't I create a FAT32 partition from that remaining space?

---

### Post by Sutekh on 2006-03-09
[QUOTE=cabber]
I have a 400G with Windows installed 100G Partition so that leaves 300g free to use for files/music/photos, and what not.[/QUOTE]
[QUOTE=cabber]I have Partition Magic installed on my Windows set up. Would it be easier to use that instead?[/QUOTE]
So you want to create a FAT32 partition (I though you already had one)?   If you are in Windows now and like Partition Magic then go right ahead.  

If you are in Ubuntu you can install GPartED
```
sudo apt-get install gparted
```
And create the FAT32 partition on the free space.  Gparted works very similar to Partition Magic.  You must unmount the windows drive before creating this partition too.
```
sudo umount /dev/sda1
```
Will acheive this.


I'd consider backing up important data/work before trying any of this though

---

### Post by cabber on 2006-03-09
Can I create a FAT32 and EXT3 with the remaining space?

  I'll probably use Partion Magic as I am somewhat of a rookie with Ubuntu and gparted.

---

### Post by Sutekh on 2006-03-09
[QUOTE=cabber]Can I create a FAT32 and EXT3 with the remaining space?

  I'll probably use Partion Magic as I am somewhat of a rookie with Ubuntu and gparted.[/QUOTE]
Yep the more partitions the merrier I say!   I have several on my spare disc.  You might want something more simple though.  

I don't know if Partition Manager creates ext3 partitions.

---

### Post by cabber on 2006-03-09
```
You must unmount the windows drive before creating this partition too
```

Is this only if I'm using gparted?

---

### Post by cabber on 2006-03-09
[QUOTE=Sutekh]Yep the more partitions the merrier I say!   I have several on my spare disc.  You might want something more simple though.  

I don't know if Partition Manager creates ext3 partitions.[/QUOTE]

I'll check.  Is there a size limit with ext3?  Also, since these partitions will not be bootable, should I make them logical or primary?

---

### Post by Sutekh on 2006-03-09
[QUOTE=cabber]```
You must unmount the windows drive before creating this partition too
```

Is this only if I'm using gparted?[/QUOTE]
I think when you use Partition Magic it reboots the PC and before Windows loads it makes the changes.  I presume this is similar to unmounting them.  

I know of no way to unmount them; in any case if you are using Partition Magic you are using Windows and can't unmount it.

---

### Post by Sutekh on 2006-03-09
[QUOTE=cabber]I'll check.  Is there a size limit with ext3?  Also, since these partitions will not be bootable, should I make them logical or primary?[/QUOTE]
2TB - 2 tera bytes. 

Make them logical.  You can only have a maximum of 4 primary partitions on a drive.

In Gparted what I do is create an 'extended partition' on the remaining space.  All partitions in the extended partition are logical ones.

---

### Post by cabber on 2006-03-09
I'm back in WIndows now and will create an extended partition with the remaining space and fdisk and post results for you.  Thanks for your assistance.

---

### Post by Sutekh on 2006-03-09
[QUOTE=cabber]I'm back in WIndows now and will create an extended partition with the remaining space and fdisk and post results for you.  Thanks for your assistance.[/QUOTE]
Take your time :)  Don't want to mess this up.  Good Luck

---

### Post by cabber on 2006-03-09
New fdisk after partition:  ext3 is offered with Partition Magic.  I created 150 G FAT32 and 150G ext3.  

```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10395    83497806    7  HPFS/NTFS
/dev/sda2           10396       48641   307210995    f  W95 Ext'd (LBA)
/dev/sda5           10396       29517   153597433+   b  W95 FAT32
/dev/sda6           29518       48641   153613498+  83  Linux

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4500    36146218+  83  Linux

Disk /dev/sdc: 37.0 GB, 37018484224 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4314    34652173+  83  Linux
/dev/sdc2            4315        4500     1494045    f  W95 Ext'd (LBA)
/dev/sdc5            4315        4500     1494013+  82  Linux swap / Solaris

```

Now the fun begins...I think.   Please advise on step by step from here.  Thanks again.

---

### Post by Doytch on 2006-03-09
Umm, isn't Ext3 only writable natively in Linux, and you need a driver that's finnicky for write support to exist under Windows?  Wouldn't that kind of suck for a drive that's to be used for Windows and Ubuntu?

---

### Post by cabber on 2006-03-09
[QUOTE=Doytch]Umm, isn't Ext3 only writable natively in Linux, and you need a driver that's finnicky for write support to exist under Windows?  Wouldn't that kind of suck for a drive that's to be used for Windows and Ubuntu?[/QUOTE]


Should I change it to FAT32?  Just to be on the safe side?

---

### Post by Doytch on 2006-03-09
I'm by no means an expert on the subject, but that's what I've heard.  The downside of Fat32 is that you can't have files larger than 4gb, but I could live with that, so I just formatted with Fat32.

---

### Post by cabber on 2006-03-09
I'll play around with it and see if it flys.

So now that I have have the FAT32 drive.  How do I mount it?  Can this be done with a Systems tool or does it have to be done in the console?

---

### Post by aysiu on 2006-03-09
In Mepis and Knoppix--you just click on the partition, which automatically appears on your desktop.

In Ubuntu--the command-line.

Quick and dirty:
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

With details:
[http://www.psychocats.net/linux/mountwindows](http://www.psychocats.net/linux/mountwindows)

---

### Post by Sutekh on 2006-03-09
[QUOTE=cabber]I'll play around with it and see if it flys.

So now that I have have the FAT32 drive.  How do I mount it?  Can this be done with a Systems tool or does it have to be done in the console?[/QUOTE]
Cool it looks like it worked.  Just follow my first post to this thread.

Instead of using this line
```

/dev/hdb1    /media/windows   vfat   iocharset=utf8,umask=0000   0   0
```
Use this one
```
/dev/sda5    /media/windows   vfat   iocharset=utf8,umask=0000   0   0
```

---

### Post by qferret on 2006-03-09
if you modify /etc/fstab as super suggested in the 2nd post in this thread, it will mount at boot time. Just note that you have to create the directory to mount to first (mkdir from a terminal or right click and create folder in the GUI)

I would go with /media/windows or /mnt/windows instead of just /windows though  ;-)


If you have 300 GB to play with, I would create both an ext3 AND a FAT32 partition. The 4GB file limit has been a gotcha for me in the past (read: DVD & PS2 ISO's > 4GB). Also....FAT32 corrupts far easier than ext3 in my experience. Use those points for guidance as to partition size. If you are going to be ripping DVD's etc left & right, go with a larger ext3 partition. If you will need to share a majority of the files with a Windows partition, go with a larger FAT32 partition. :idea:

---

### Post by cabber on 2006-03-09
[QUOTE=Sutekh]Cool it looks like it worked.  Just follow my first post to this thread.

Instead of using this line
```

/dev/hdb1    /media/windows   vfat   iocharset=utf8,umask=0000   0   0
```
Use this one
```
/dev/sda5    /media/windows   vfat   iocharset=utf8,umask=0000   0   0
```[/QUOTE]

Okay, this worked.  One question.  For the ext3 drive, I want to name it something else.  Like media/ext.  When I changed the media/windows and ran mount -a from below instruction it didn't take.

```
 - /media/windows - this is the folder where the drive will be mounted. If this folder doesn't exist you will need to create it yourself
Code:

sudo mkdir /media/windows

Note you don't have to use /media/windows, in my system I use /mnt/os-shared, its up to you

- vfat - this specifies the filesystem as fat

- iocharset=utf8,umask=0222 - these options set the character encoding to utf8 (for special chars) and sets the umask. umask=0000 allows read, write and execute access to the partition.

Once you've modified the /etc/fstab, you can save it and issue the command
Code:

sudo mount -a

This re-mounts the partitions, without you having to restart your computer.
```

---

### Post by Sutekh on 2006-03-09
[QUOTE=cabber]Okay, this worked.  One question.  For the ext3 drive, I want to name it something else.  Like media/ext.  When I changed the media/windows and ran mount -a from below instruction it didn't take.
[/QUOTE]Okay the line in the /etc/fstab needs to be different for an ext3 partition.

Also you need to create the folder for the ext3 partition to be mounted in *aswell* as changing the line in the /etc/fstab

Say you wanted it to go in /media/ext, first create the folder
```
sudo mkdir /media/ext
```
Then use this line to mount it in the /etc/fstab
```
/dev/sda6    /media/ext   ext3   defaults   0   0
```
Then remount everything using
```
sudo mount -a
```

There are other options for mounting ext3 that you may want to look into later, but for now the defaults should be all you need.

---

### Post by cabber on 2006-03-09
Okay, that worked.  \\:D/  I really appreciate all of your knowledge and assistance.

So, where are these drives located (besides on the desktop)?  media/windows and media/ext..but under what?

Also.  If I am downloading something and want to save it:  Where do I save files within Ubuntu?  Besides the new ext3 drive?  Thanks again.  SO many questions.

As you probably guessed, I'm a long time Windows guy but loving linux.  

While I have your time:
How do I mount CD Drives?  I have two :confused: 

What about my  floppy?:confused: 

How do I get icons on the desktop?  Firefox, email, and others?

---

### Post by Sutekh on 2006-03-09
[QUOTE=cabber]Okay, that worked.  \\:D/  I really appreciate all of your knowledge and assistance.

So, where are these drives located (besides on the desktop)?  media/windows and media/ext..but under what?[/QUOTE]
Okay the 'devices' (the drive/partition) are located in /dev ie /devices

/dev/sda refers to the first ('a') SCSI drive.  /dev/sda1 refers to the first partition on the first SCSI drive.  Your Windows partition is /dev/sda1, your FAT32 share is /dev/sda5 and the ext3 is /dev/sda6.  

The folders /media/... refer to the point on your Linux filesystem where the devices are 'mounted'.  So /dev/sda5 is mounted to /media/windows.  

I hope that explains it a bit.

[QUOTE=cabber]
Also.  If I am downloading something and want to save it:  Where do I save files within Ubuntu?  Besides the new ext3 drive?  Thanks again.  SO many questions.
[/QUOTE]This is a good post on explaining the Linux filesystem

[Ubuntu Forums - That Crazy Directory Tree!](http://ubuntuforums.org/showthread.php?t=126107)

In a default situation you only have access to this folder: /home/<username>.  The rest of the system is off limits to a normal user, and with good reason, it is very easy to mess things up.  In the occasions where you do need to do things outside of your home folder, you use the command **sudo** which breifly gives a normal user full privileges to the system.

Now that you have mounted these extra partitions you should also be able to have access to them, so you can choose to download your files to a location under your home folder or in one of these shared partitions.

[QUOTE=cabber]
While I have your time:
How do I mount CD Drives?  I have two :confused: 

What about my  floppy?:confused: 
[/QUOTE]
CDROMs and floppies should already have entries in the /etc/fsatb similar to my ones
```
/dev/hdc    /media/cdrom0     udf,iso9660    ro,user,noauto     0      0
/dev/fd0    /media/floppy0    auto           rw,user,noauto     0      0
```
When you insert a CDROM or floppy they should appear automatically on your desktop.  This is an automount setting found in the Removable Drives and Media entry in the System -> Preferences Menu


[QUOTE=cabber]
How do I get icons on the desktop?  Firefox, email, and others?[/QUOTE]
Icons on the desktop?  Do you mean those partitions we mounted or do you mean anything in general?

To get those partitions on the desktop, open the Configuration Editor, its in the Applications -> System Tools Menu.  In the menu on the left open apps -> nautilus -> desktop and check the box 'volumes_visible'.  This should put partitions mounted under /media/ on the desktop.

Oh now I think you meant getting Firefox and Email on the desktop.  Well just open up the menu that contains them and click and drag it to the desktop.  That should create a shortcut for you.

---

### Post by Peacepunk on 2006-03-12
**Thanks Sutekh**

This has worked with my NTFS partition as well.

Here is a snap if my fstab:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>     <options>       <dump>  <pass>
proc                 /proc                          proc          defaults                    0       0
/dev/hda6        /                                 reiserfs      notail                        0       1
#/dev/hda1     /media/hda1     ntfs   defaults                                      0       0
/dev/hda5        none                          swap          sw                             0       0
/dev/hdc          /media/cdrom0          udf,iso9660 user,noauto             0       0
/dev/hda1        /media/windows         ntfs   iocharset=utf8,umask=0000   0    0


You'll notice I didn't delete the original mounting point, I just added an "**#**" in front. Spare me the fear of getting back the backuped file wrong.

I cannot write, though. But I've got all my Music & Pics back !

Thanks again.

---

### Post by Peacepunk on 2006-03-12
[CENTER]**_Warning: You better get rid of your iPod..._**[/CENTER]


*Working the Partitions, digging into forums, opening shells, trying to keep up..*. I found one partition FAT32 too much on my system, as it can consider the same as being formatted in two ways. Nope. It was my iPod that appeared in my fdisk listing.

[CENTER][COLOR="Red"]Yeah.[/COLOR]

[FONT="Comic Sans MS"][SIZE="4"]  :-D  A FREE newbie advice: unplug anything not needed  :-D [/SIZE][/FONT][/CENTER]

---

### Post by Sutekh on 2006-03-12
[QUOTE=Peacepunk]```

/dev/hda1 /media/windows ntfs iocharset=utf8,umask=0000 0 0
```
Hi Peacepunk, good to hear it's working.  I would change that line a little though
```
/dev/hda1 /media/windows ntfs **nls**=utf8,umask=0**222** 0 0
```
 - **nls** is the option that has replaced iocharset for NTFS partitions (I'm unsure whether or not using iocharset will have a negative effect, but nls is the new name)

 - umask=0**222** this prevents write access to the NTFS partition, as Linux support for writing to NTFS is not really stable.  I know umask=0000 doesn't allow write access in any case, I just like the extra precaution.

[QUOTE=Peacepunk]
You'll notice I didn't delete the original mounting point, I just added an "**#**" in front. Spare me the fear of getting back the backuped file wrong.
[/QUOTE]That's a good idea if you re unsure about replacing iles with backup files.

[QUOTE=Peacepunk]
I cannot write, though. But I've got all my Music & Pics back !

Thanks again.[/QUOTE]
Again writing to NTFS is still not a recommended practice, but I'm glad you have access to your data.

---

### Post by alexandermimix on 2006-08-18
if ubuntu automatically mounted partitions / drives when they are added ubuntu would be much more loved by people converting from windows. Its not that hard however it is infinatly harder then in lets say XP where new FAT32 and NTFS partitions are ready to use without any user interaction before your OS has even finished booting. :(

---

### Post by aysiu on 2006-08-18
> **alexandermimix said:**
> if ubuntu automatically mounted partitions / drives when they are added ubuntu would be much more loved by people converting from windows. Its not that hard however it is infinatly harder then in lets say XP where new FAT32 and NTFS partitions are ready to use without any user interaction before your OS has even finished booting. :(
Unfortunately, Ubuntu is in the dark ages when it comes to mounting.

Knoppix has had this down for quite some time.

---

### Post by alexandermimix on 2006-08-18
> **aysiu said:**
> Unfortunately, Ubuntu is in the dark ages when it comes to mounting.

Knoppix has had this down for quite some time.

which is unfortunate because I feel these sort of things are what really hold back linux from the desktop market where people want to turn on their computer and just do stuff without fiddling around under the hood. Seem to spend more time getting things to work then actuelly using them.

---

### Post by aysiu on 2006-08-18
Knoppix *is* Linux.

---

### Post by alexandermimix on 2006-08-18
I realise this however knoppix doesn't have some of the things that ubuntu has down pat.

If its possible to automount drives / partitions in one distro shouldn't it be pretty darn easy to port that functionallity to another distro eg. ubuntu?

---

### Post by aysiu on 2006-08-18
> **alexandermimix said:**
> I realise this however knoppix doesn't have some of the things that ubuntu has down pat.

If its possible to automount drives / partitions in one distro shouldn't it be pretty darn easy to port that functionallity to another distro eg. ubuntu?
So you would think.

By the way, Mepis is just about the best I've found. It's based on Ubuntu, but it has a lot more GUI frontends for things, including mounting drives/partitions and restoring Grub to the MBR.

---

### Post by alexandermimix on 2006-08-18
> **aysiu said:**
> So you would think.

By the way, Mepis is just about the best I've found. It's based on Ubuntu, but it has a lot more GUI frontends for things, including mounting drives/partitions and restoring Grub to the MBR.

Mepis, might have to have a look. Unfortunate that each distro seems to have its 'niche' strengths. Eg. ubuntu is so easy to update and install programs. Some distro's have java or flash working great.

so much choice when it comes to linux distro's! Such a shame that all the best (from a 'just want things to work' perspective) hasn't been extracted from all the individual distro's and placed into one truelly windows murdering distro. People seem to recommend a differant distro as being 'easiest' for each thing you want to do. One distro that does it all 'easiest' would rock as most people 'want it all' and generally want to use one operating system for everything, thus people generally stick with MS which does work generally well for everything.

---

### Post by aysiu on 2006-08-18
Actually, I'd say Mepis is the easiest hands-down, with PCLinuxOS as a close contender.

Both come as live/installer CDs in one with GUI installers. Both also come with popular proprietary codecs and software. There's a big emphasis on point-and-click.

Of course, Linspire is also a contender, except that most Linux users don't like Linspire for its cost and its "Windows-like" appearance/philosophy.

And don't forget there's the Linux Distribution Chooser:
[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

---

