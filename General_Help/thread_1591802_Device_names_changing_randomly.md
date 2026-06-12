---
title: "Device names changing randomly"
date: 2010-10-09
forum: General Help
---

### Post by ibates on 2010-10-09
I have noticed that from time to time, apparently completely randomly, Ubuntu seems to change dev names.  For example, the last time I booted up, my Windows HDD was shown in the GRUB as /dev/sdc1.  But the time before, it was /dev/sda1.

This is also the case in $ cat /proc/partitions.  Two examples are shown for two different occasions, where no other parameter (that I am aware of) has changed.

Example 1:

ian@ian-desktop:~$ cat /proc/partitions
major minor  #blocks  name

   8        0  390711384 sda
   8        1  381833216 sda1
   8        2          1 sda2
   8        5    8876032 sda5
   8       16  976762584 sdb
   8       17  976583286 sdb1
   8       32  976762584 sdc
   8       33  976762550 sdc1
   8       48  312571224 sdd
   8       49  272888091 sdd1
   8       50          1 sdd2
   8       53   39680518 sdd5
   8       64  312571224 sde
   8       65  312568641 sde1
ian@ian-desktop:~$ 


Example 2:

ian@ian-desktop:~$ cat /proc/partitions
major minor #blocks name

8 0 312571224 sda
8 1 272888091 sda1
8 2 1 sda2
8 5 39680518 sda5
8 16 312571224 sdb
8 17 312568641 sdb1
8 32 390711384 sdc
8 33 381833216 sdc1
8 34 1 sdc2
8 37 8876032 sdc5
8 48 976762584 sdd
8 49 976583286 sdd1
8 64 976762584 sde
8 65 976762550 sde1
ian@ian-desktop:~$


It could be that this is causing a profound and potentially hazardous situation when attempting to run a VMDK file in VirtualBox which was created at a time when the Windows (Guest) raw disk bore than name /dev/sda1.  As was the case in example 2 above.

But it seems that attempting to access that same drive at a time when Ubuntu has renamed it /dev/sdc1 is creating that hazardous situation.

Further; although I cannot generally read the dialogues because they move on too quickly, each time I boot Ubuntu, I get quite a bit of information about no-IRQ or something like that, and in the middle of it all is something about *cannot find /dev/sdb*, or */dev/sdd*, and sometimes, other device names as well.

How can I stop this renaming and be sure that each device always bears the same name?  And what is going on with the boot up dialogue saying that it cannot find some /dev or another?

---

### Post by sisco311 on 2010-10-09
[uhelp]community/UsingUUID[/uhelp]

---

### Post by ibates on 2010-10-09
An adjunct issue which may well be related to the issue above.

I have programmed fstab to mount a third HDD at bootup.  It is the HDD I use for backups and is thus necessary to have mounted at bootup.

Randomly, the boot process sometimes cannot locate this device.  I am presented with a dialogue which states essentially Unable to mount. I Ignore, S Skip, or M Mount manually.

Nothing changes from one boot session to the next as far as I am aware.

Sometimes this message can be overcome by a soft reboot, but sometimes a complete shutdown and power off the PC altogether is required.

Is this also part of the above problem?

---

### Post by blueridgedog on 2010-10-09
> **ibates said:**
> 

Randomly, the boot process sometimes cannot locate this device.  I am presented with a dialogue which states essentially Unable to mount. I Ignore, S Skip, or M Mount manually.

Is this also part of the above problem?

If the hardware can't see a device, then all subsequent devices will be changed accordingly, hence the suggestion to use UUID.

If you have a device that is typically sdb with partitions 1,2 and 3, but sda can't be located, then it will become sda.

---

### Post by ibates on 2010-10-09
Sisco311

Thanks for the link.  That seems to be pretty good stuff.  but for what I believe would be the case for an average user, it is really, really, technical stuff.

So now I know all about UUID.  (I think).  But how, when, where, and why, to use them in the snakes and ladders pit known as "the system" - well you've got me.  It might as well have been written in Chinese.

How on earth does this help me with my problem?

It sounds to me a bit like I am being told, "Linux is really for the big boys, and if you are not up to the technical standards necessary to use it, then just go away and go back to Windows".

Please do not take that comment lightly.   I, like I can imagine, many others, have invested countless hours and lost hair in seriously attempting to move over to Linux.  In my case, for over two years.  But every time something like this pops up, I am as far from finding a user-friendly replacement for Windows as I was the first day I started up Linux.  And that is a long, long, way away.

After reading throuogh the reference you gave, I am molre confused than I was before I started.

What do I need to change?

Where must it be changed?

What about apps which access data by reference to device names?

What happens if I change the device name in one place but overlook the change in another place?

I could go on with the questions for a long time.

And if, as the Community website states, *Linux now prefers to use UUID (Universally Unique Identifier), LABEL, or symlinks to identify media storage devices on a system* why did the developers of the current Ubuntu releases apparently decide to not use UUID?

That those developers decided not to use UUID cannot be argued because even Ubuntu's Disk Utility (in System->Administration) only refers to devices by /dev names.

Have we, the users, been setup.  It sure looks like it.

Is there a more understandable method?

---

### Post by srs5694 on 2010-10-10
First, UUIDs are applied to *filesystems,* which are data structures that exist inside partitions, which in turn are data structures on hard disks. Thus, you can't use UUIDs to refer to entire hard disks (which is what you'd need to tell GParted which disk to use). Of course, if you're using GParted, there's a human brain at work, which has this thing called "common sense." In other words, you're supposed to be able to recognize that you're working on one disk rather than another. (This might not be possible if you've got a bunch of identically-partitioned disks of the same model, of course, but in general it's a reasonable assumption.) One side comment: The new GUID Partition Table (GPT) partitioning scheme applies GUIDs (a UUID variant) to entire disks, so in theory, if you used GPT exclusively, disk partitioning tools could identify them by GUID much the way filesystem mounting tools can identify filesystems by UUID. This isn't yet possible, since GPT is still uncommon and AFAIK the system functions don't exist for this sort of thing yet; but it could happen in a few years.

Second, Windows has equally confusing internals. Disks can shift around and get confused in Windows, so going back to Windows won't really help make things any less confusing, except by accident. (The Windows drivers for *your* particular mix of hardware might result in less instability; but there might be less stability in Windows for your neighbor's hardware.)

Third, you seem to be under the mistaken impression that Ubuntu is a monolithic whole created by one all-knowing mind. It isn't. It's a collection of thousands of little components created by different people acting independently. The same is true of any OS, really, but Windows has both the advantage and the disadvantage of being driven by a corporate entity that can assign specific goals. (See *[The Cathedral and the Bazaar](http://catb.org/esr/writings/cathedral-bazaar/)* by Eric S. Raymond for much more on the competing philosophies and driving forces behind commercial vs. open source software.)

Fourth, if it's important to you that you have consistent device names for your disks for those tools that can't yet use UUIDs, you can look into udev configuration. For your purposes, I'd recommend creating a symbolic link to any disk or partition that has special interest to you. [Here](http://www.reactivated.net/writing_udev_rules.html) is one of many Web pages a Web search turns up about udev. Note in particular the section on USB hard disks near the end. (Conventional PATA, SATA, or SCSI hard disks are just like USB hard disks, in principle.) If you want to access partition #1 on a particular disk for VirtualBox, you could create a symbolic link to that partition and call it, say, /dev/vbdisk.

Fifth, as a general rule, I wouldn't recommend giving virtualization software direct access to a disk partition. I acknowledge that this sort of access might be necessary sometimes, but in my experience, virtualization is best done using disk files as hard disk stand-ins. This enables easy copying of virtual disks, use of disk compression on virtual images, etc. That said, I've not used VirtualBox specifically, so I don't know if it might be built around an assumption of direct partition access. If it's like most other virtualization tools, though, I'd just ditch the direct partition access and use files. That will bypass the entire problem, and is likely to be the cleanest solution. If this isn't an option for you, please tell us why.

---

### Post by ibates on 2010-10-10
srs5694

Many thanks for that obviously well considered and thorough response.

I have absolutely no argument with anything you have written, and somewhat unusually for technical matters such as this, it is quite easy to understand.

Really, there is only one partition on one HDD which is causing me grief.  That is partition 1 on my Windows XP HDD.  Unfortunately, that is also the boot partition, but from my experiences with VirtualBox, I have not come across a situation where I think I could even try to boot from that disk when it is running as a VMDK file in a guest VM even if I wanted to - and I never would.

Generally, on the occasion when, coincidently it appears, the correct disk has been identified by the Ubuntu system as the one I am actually attempting to access, all does go very sweetly.  I am happy to load the program files onto the Windows XP VM so I only have to access the data for the few programs I want to run regularly on Windows.  The vast majority of what is on that disk is of no interest to me 99.9% of the time.

My query I suppose is, can I simply change the identity of the raw disk for a new VMDK file and also that of the HDD I mount at boot up for backups using UUID and leave the others do what they will?

If I can, what advice would you give for actually changing the name of the device (a) for re-creating the VMDK file and (b) editing fstab so as to change the identifier of the device for mounting at bootup by UUID?

The syntax in VirtualBox for creating a VMDK file according to the manual is:

VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk -rawdisk /dev/sda -partitions 1

Obviously /path/to/file.vmdk must be absolute and /dev/sda is typical not literal.

Also, the line in fstab for the HDD to mount at bootup (nothing to do with VirtualBox or VM, but a simple action in the Ubuntu system) is:

/dev/sde1 /media/UBackups ext4 auto,rw,user 0 2

I assume I can edit that line to replace /dev/sde1 with the UUID for that disk.

What do you think about all of that?

---

### Post by ibates on 2010-10-10
I have edited my fstab file and inserted a UUID name for the backup HDD which I wanted to mount at boot up.

It works perfectly; so that is one problem down and out of the way.

I then tried to create a new VMDK file, but have come across the old 

*Error opening the raw disk 'UUID=C29052C49052BE9B': VERR_FILE_NOT_FOUND*

message.  I have had it before while attempting to create a VMDK file, but I cannot for the life of me remember what I did to get rid of it.

VirtualBox does recognise and use UUID.

Is the format I have used correct?  Here is the command I have used.  It is verbatim from the User Manual with the exception of the device identifier (now UUID instead of /dev/sd??).

*VBoxManage internalcommands createrawvmdk -filename /home/ian/vmdkfiles/PhysicalC.vmdk -rawdisk UUID=C29052C49052BE9B*

I have checked and re-checked the identifier.  It is what is shown in blkid and also when mounting the drive in "Places".

I am a member of the user Group "Disk" and "vboxusers"

I would appreciate assistance in bowling this remaining problem over.

---

### Post by dcstar on 2010-10-10
> **ibates said:**
> I have edited my fstab file and inserted a UUID name for the backup HDD which I wanted to mount at boot up.

It works perfectly; so that is one problem down and out of the way.

I then tried to create a new VMDK file, but have come across the old 
......

If you have VM issues then post in the Virtualization forum.

---

### Post by sisco311 on 2010-10-10
> **ibates said:**
> 
VirtualBox does recognise and use UUID.

Is the format I have used correct?  Here is the command I have used.  It is verbatim from the User Manual with the exception of the device identifier (now UUID instead of /dev/sd??).

*VBoxManage internalcommands createrawvmdk -filename /home/ian/vmdkfiles/PhysicalC.vmdk -rawdisk UUID=C29052C49052BE9B*

I have checked and re-checked the identifier.  It is what is shown in blkid and also when mounting the drive in "Places".

I am a member of the user Group "Disk" and "vboxusers"

I would appreciate assistance in bowling this remaining problem over.

Instead of /dev/sdXY or UUID=XXXXXXXXXXXXXXXX use the symbolic link from /dev/disk/by-uuid/:

*VBoxManage internalcommands createrawvmdk -filename /home/ian/vmdkfiles/PhysicalC.vmdk -rawdisk /dev/disk/by-uuid/C29052C49052BE9B*

---

### Post by ibates on 2010-10-11
sisco311

Many thanks for your reply to my question about syntax with respect to UUID.  It is doubtless as relevant when used by an app such as VirtualBox as for any other use within the Linux environment.

This has solved the problem.  The VMDK is created and everything is on track.

If I knew how to mark this thread as SOLVED I would.

---

