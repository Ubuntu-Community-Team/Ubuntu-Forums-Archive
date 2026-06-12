---
title: "Automount partitions Ubuntu 10.x"
date: 2011-03-23
forum: General Help
---

### Post by rgb1701 on 2011-03-23
I usually partition my hard drives with at least 3 partitions- /, swap and a data storage partition I usually disklabel "Data", usually formatted to ext3/4

When you install and boot Ubuntu 10.x, the Data partition shows up in Places>removable Media, and also in standard Gnome File selector dialogs, but Data is not mounted until you click on it in one of these two places.

I do not want to manually edit fstab nor enter the user account password everytime to mount it, as would be required using the 'mount' command in a terminal (I.e. sudo mount).

All I want is the equivalent of using the mouse pick Places> Removable Media> Data, which mounts the Data partition without asking for the user account password, automatically mounting to /media/Data, WITHOUT requiring the directory /media/Data to be created or existing prior to picking the partition in Places> Removable Media> Data.

What is the equivalent terminal command to do the same thing as the mouse pick?  Again- NO sudo/password needed, and automatically creating a mountpoint in /media using the disklabel of the partition?

I want the Data partition to be automounted using its disklabel everytime I boot, WITHOUT a password or manual fstab editing, simply behaving as if I clicked Places>Removable Media>Data.

Some quick googling turned up

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

but the gnome-mount command appears obsoleted in Ubuntu 10.x, and I tried variations of the mount command

[http://manpages.ubuntu.com/manpages/hardy/man8/mount.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/mount.8.html)

but couldn't come up with the secret sauce to replicate the simple mouse pick Places>Removable Media>Data (or picking Data in a stock file selector).  

What method or command does Ubuntu use to mount the Data partition when it is mouse clicked via Places>Removable Media>Data?

---

### Post by blind2314 on 2011-03-23
You can dump this into a script and have it run on boot (or run this command from a terminal, I'll provide both "versions").
 
```

#!/bin/sh
 
if [ ! -d /media/Data ]; then
     mkdir /media/Data
fi
 
mount -t ext3 /dev/sdb1 /media/Data

```
 
Of course, change /dev/sdb1 to whatever partition and disk data actually resides on. If you want to run that all as one command from a terminal, type:
 
```
if [ ! -d /media/Data ]; then mkdir /media/Data; fi; mount -t ext3 /dev/sdb1 /media/Data
```

---

### Post by celldweller1591 on 2011-03-23
> sudo apt-get install mountmanager
and then, then use it to automount all types of partitions.

---

### Post by rgb1701 on 2011-03-23
> **blind2314 said:**
> You can dump this into a script and have it run on boot (or run this command from a terminal, I'll provide both "versions").
 
```

#!/bin/sh
 
if [ ! -d /media/Data ]; then
     mkdir /media/Data
fi
 
mount -t ext3 /dev/sdb1 /media/Data

```
 
Of course, change /dev/sdb1 to whatever partition and disk data actually resides on. If you want to run that all as one command from a terminal, type:
 
```
if [ ! -d /media/Data ]; then mkdir /media/Data; fi; mount -t ext3 /dev/sdb1 /media/Data
```

Thanks, but your method requires creating the directory /media/Data, which most likely requires a sudo command and password.

Isn't there a terminal command that replicates the functionality of simply mouse picking Places>Removable Media>Data?  This means automatically mounting the Data partition to /media WITHOUT the a priori creattion of a /media/Data directory, creating the mountpoint /media/Data automatically based on the disklabel (Data in this case).

/rant on
I never understood why this is so difficult and/or obfuscated, particularly in Ubuntu (whose raison de'etre is usability for normal non-CS/sysadmin users) in 2011.

I understand the CS/sysadmin security reasons for partition mount policies, but there is ZERO reason to NOT automount all recognized partitions at first startup, just like Windows does with all formatted partitions, assigning drive letters to all recognized partitions. The analogous Ubuntu/linux behavior ought to be simply mounting all recognized/formatted partitions physically attached to the computer to /media, the same as mouse picking them in the Places menu.

If inserted USB sticks and hard drives are automounted, then why aren't partitions INSIDE THE COMPUTER!?

At minimum, the behavior is consistent, and an annoyance to noobs and those who setup installs for others.
/rant off

---

### Post by rgb1701 on 2011-03-23
> **celldweller1591 said:**
> and then, then use it to automount all types of partitions.

Thanks- I'll try it later.  I assume I won't need to create the directory /media/Data prior to using it...

---

### Post by blind2314 on 2011-03-23
> **rgb1701 said:**
> Thanks, but your method requires creating the directory /media/Data, which most likely requires a sudo command and password.
 
Isn't there a terminal command that replicates the functionality of simply mouse picking Places>Removable Media>Data? This means automatically mounting the Data partition to /media WITHOUT the a priori creattion of a /media/Data directory, creating the mountpoint /media/Data automatically based on the disklabel (Data in this case).
 
/rant on
I never understood why this is so difficult and/or obfuscated, particularly in Ubuntu (whose raison de'etre is usubility for normal mom-CS/sysadmin users) in 2011.
 
I understand the CS/sysadmin security reasons for partition mount policies, but there is ZERO reason to NOT automount all recognized partitions at first startup, just like Windows does with all formatted partitions, assigning drive letters to all recognized partitions. The analogous Ubuntu/linux behavior ought to be simply mounting all recognized/formatted partitions physically attached to the computer to /media, the same as mouse picking them in the Places menu.
 
If inserted USB sticks and hard drives are automounted, then why aren't partitions INSIDE THE COMPUTER!?
 
At minimum, the behavior is consistent, and an annoyance to noobs and those who setup installs for others.
/rant off
 
 
There are actually good reasons to not automount every single recognized partition at boot (unless it's in your fstab). I'm sorry that you're having difficulties, but ranting about downfalls in an OS that are there for a purpose isn't really useful to anyone.
 
Also, for what it's worth, the reason Windows automounts everything is because it does make changes to its partition/filesystem table when new partitions are created..the user doesn't have a say in this.

---

### Post by Morbius1 on 2011-03-23
But mountmanger will create entries in fstab which violates one of your original requirements.

What is your objection to having entries in fstab or creating your own mount points. None of my business I suppose - just like to know.

---

### Post by rgb1701 on 2011-03-23
> **Morbius1 said:**
> But mountmanger will create entries in fstab which violates one of your original requirements.

What is your objection to having entries in fstab or creating your own mount points. None of my business I suppose - just like to know.

No big objection to changing fstab- I just wanted a method that didn't require manual fstab editing or the need for the mountpoint directory to exist already.

[http://opendesktop.org/content/show.php/MountManager?content=78270](http://opendesktop.org/content/show.php/MountManager?content=78270)

[http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html](http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html)

Personally, I have no barrier to editing fstab manually, but I prefer point and click methods, and I need simple GUI methods in order to instruct non-techie types in how to automount partitions.

Automounting is important for DVR/PVR machines running MythTV, for example.  I always set Myth to record to a partition and/or drive separate from the OS / partition.  If there is a power failure and the machine restarts (for any reason), the recording partition needs to be there (mounted) at startup.  When I tell a non-techie user how to install Mythbuntu with a simple point and click procedure, I need a similarly simple point and click  GUI method to let them automount their recording partition/drive.

---

### Post by rgb1701 on 2011-03-23
> **blind2314 said:**
> There are actually good reasons to not automount every single recognized partition at boot (unless it's in your fstab). I'm sorry that you're having difficulties, but ranting about downfalls in an OS that are there for a purpose isn't really useful to anyone.
 
Also, for what it's worth, the reason Windows automounts everything is because it does make changes to its partition/filesystem table when new partitions are created..the user doesn't have a say in this.

Apologize for the rantish post, but this has been a pet peeve behavior for a LONG time.  Usability issues are typically emotional, and are basic functionality issues with a BIG impact on "normal" non-techie users.

Ubuntu needs to prompt the user the first time a partition is picked in Places>Removable Media with a simple checkbox that asks "Would you like to mount this partition automatically every time you start?", then ask for the account password if needed once to make the change, automounting that partition to /media/$DISKLABEL just like the manual mouseclick.

It would still be useful to know the terminal command equivalent to the Places>Removable Media mouse click, i.e. mounting a partiton to /media/$DISKLABEL *without* the directory /media/$DISKLABEL existing already.

re: Windows partition tables updating-

Again, if Ubuntu automounts inserted USB drives, which represent a FAR greater security/privacy risk vs partitions on hard disks located physically inside the computer itself, then why aren't the partitions on internal drives automounted (or at minimum, prompted for automounting if desired)?

---

### Post by Morbius1 on 2011-03-23
Then the best thing to do is instruct the installer to have all these non-system disks mount at boot when you do the initial install. The installer will basically ask you two questions:

Where do you want it to mount?
How is it currently formatted?

The installer will do the rest populating fstab with what it thinks is the appropriate setting.

---

### Post by rgb1701 on 2011-03-23
Apparently, I'm not alone in my sentiments-

[http://ubuntuforums.org/showthread.php?t=1498130](http://ubuntuforums.org/showthread.php?t=1498130)

[https://answers.launchpad.net/disk-manager/+question/7114](https://answers.launchpad.net/disk-manager/+question/7114)

Requiring unique disklabels (which are simpler than UUID's) on partitions needs to be mandatory, to simplify automounting by disklabel.

The problem with referencing drives by /dev/sdb1, sdc2, etc is that these designations can re-assign themselves between reboots at random *without* adding/removing internal IDE/SATA physical drives installed in a machine (I've had it happen on a couple of my boxes)!  Adding/removing internal IDE/SATA drives and/or USB drives further complicates the /dev/sXYZ designations for automounting purposes.

Also, a drive/partition that is referenced as /dev/sdc1 on one machine, will not likely be the same when connected to another machine, so the only two unique identifiers for a partition are UUID or disklabel.  The UUID is too long and technical, so that leaves the disklabel.

---

### Post by Morbius1 on 2011-03-23
> Requiring unique disklabels (which are simpler than UUID's) on  partitions needs to be mandatory, to simplify automounting by disklabel.How do you propose to make a unique disk label or any disk label mandatory? This is usually set at the time the partition is initially formatted.

[COLOR=Blue]**EDIT:**[/COLOR] Just to make this clear. By default, these non system partitions that are not defined in fstab will mount when selected to /media/disk-label. It's hard wired to do that. The reason you are getting /media/UUID-number is because the partition has no label.

---

### Post by vanadium on 2011-03-23
To the OP: I think pmount is the tool you are after. You could include the command in the user's autostart.

---

### Post by rgb1701 on 2011-03-23
> **Morbius1 said:**
> How do you propose to make a unique disk label or any disk label mandatory? This is usually set at the time the partition is initially formatted.

[COLOR=Blue]**EDIT:**[/COLOR] Just to make this clear. By default, these non system partitions that are not defined in fstab will mount when selected to /media/disk-label. It's hard wired to do that. The reason you are getting /media/UUID-number is because the partition has no label.

It is trivial to change the disklabel of a partition after OS install with gparted, or the System>Administration>Disk Utility that is available by default in Ubuntu 10.x, 

[http://petermoulding.com/smart_disk](http://petermoulding.com/smart_disk)
[http://blog.rogersoles.com/2010/06/27/technology/ubuntu-disk-utility/](http://blog.rogersoles.com/2010/06/27/technology/ubuntu-disk-utility/)

or the terminal with mlabel or e2label-

[http://ubuntuforums.org/showpost.php?p=1915514&postcount=6](http://ubuntuforums.org/showpost.php?p=1915514&postcount=6)

requiring the sudo password, of course.

If a newly inserted/installed partition or USB drive had the same label as an existing mounted parttion, the OS could prompt the user to update the disklabel of a conflicting device (asking for the sudo password, of course), or simply apply a -1, -2, etc to the disklabel to identify a unique mountpoint at /media.

Ubuntu 10.x already does the -1,-2,... numbering for inserted USB drives without disklabels, calling them disk-1, disk-2, etc

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Another good disklabel HOWTo-

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Mountpoint HOWTO-
[https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)

---

### Post by Morbius1 on 2011-03-23
Yes but:
> How do you propose to make a unique disk label or any disk label [COLOR=Blue]mandatory[/COLOR]?
EDIT: So now we're talking about external devices ?

---

### Post by rgb1701 on 2011-03-23
> **vanadium said:**
> To the OP: I think pmount is the tool you are after. You could include the command in the user's autostart.

EDIT- That was NOT the droid I was looking for :D

That is NOT the command being executed when you mouseclick unmounted partitions in Places>Removable Drives

[http://manpages.ubuntu.com/manpages/maverick/man1/pmount.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/pmount.1.html)

[http://packages.ubuntu.com/maverick/pmount](http://packages.ubuntu.com/maverick/pmount)

[https://launchpad.net/ubuntu/+source/pmount](https://launchpad.net/ubuntu/+source/pmount)

[http://ubuntuforums.org/showthread.php?t=375768](http://ubuntuforums.org/showthread.php?t=375768)

I found this- the gvfs-mount command
[http://sukiprattle.blogspot.com/2010/07/automounting-partition-using-gvfs-mount.html](http://sukiprattle.blogspot.com/2010/07/automounting-partition-using-gvfs-mount.html)

---

### Post by rgb1701 on 2011-03-23
> **Morbius1 said:**
> Yes but:

EDIT: So now we're talking about external devices ?

My OP was referring to internal IDE/SATA partitions, but my rant covered the inconsistent mount behavior of USB connected partitions vs. internal IDE/SATA partitions ;)

---

### Post by texas.chef94 on 2011-03-24
> **rgb1701 said:**
> No big objection to changing fstab- I just wanted a method that didn't require manual fstab editing or the need for the mountpoint directory to exist already.

[http://opendesktop.org/content/show.php/MountManager?content=78270](http://opendesktop.org/content/show.php/MountManager?content=78270)

[http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html](http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html)

Personally, I have no barrier to editing fstab manually, but I prefer point and click methods, and I need simple GUI methods in order to instruct non-techie types in how to automount partitions.

Automounting is important for DVR/PVR machines running MythTV, for example.  I always set Myth to record to a partition and/or drive separate from the OS / partition.  If there is a power failure and the machine restarts (for any reason), the recording partition needs to be there (mounted) at startup.  When I tell a non-techie user how to install Mythbuntu with a simple point and click procedure, I need a similarly simple point and click  GUI method to let them automount their recording partition/drive.

I would appreciate your carrying this thought/process a bit further.
I suddenly find myself in need of a data partition and I have set one up in hopes to go from there.
Could you point me to a resource or give me the terminal commands to get full permission, as well as how exactly do I access to write to after this is done. Thanks

---

### Post by rgb1701 on 2011-03-24
I think I found what I need-

gvfs-mount

[http://sukiprattle.blogspot.com/2010/07/automounting-partition-using-gvfs-mount.html](http://sukiprattle.blogspot.com/2010/07/automounting-partition-using-gvfs-mount.html)

which appears to be what is executed when mouse clicking an unmounted partition to mount it in Places>Removable Media, based on my observations of the relevant processes shown in htop when I clicked partitions there.

The link above addresses exactly the issues highlighted in my OP.

Mountmanager requires the account password, plus it appears to need the mount path specified- I wanted the mount path defined automatically by disklabel.

Pmount did not work with non-removable drives, i.e. internal IDE/SATA partitions.

In any event, I wanted the terminal command that replicated the Places>Removable Media mouse click functionality, which gvfs-mount appears to do, and is articulated well at the link above:

> Why automounting on startup? (These are just few reasons.Might be lot of other possibilities)

    * the collection of wallpaper you using are placed in that partition
    * Icons for launcher which is placed in that partition
    * You want it to be available each time you boot


Why use gvfs-mount
Usually when talking about automounting on startup people would suggest user to add entries in /etc/fstab. The problem is that if we mount a partition from fstab, we need to have admin right to unmount/remount the partition. And another uncool thing is that if we automount using mount command & entries in fstab, anything that we delete from the partition will not go into trash instead it will be deleted from your harddisk as soon as you click delete. You wont find it in trash, believe me.

Automount using gvfs-mount is a totally opposite story. Any partition you mount using gvfs-mount command can be unmount/remount without administrative privilege. Besides that anything we delete will go to trash first. So if we accidently deleted something we can find it back & restore from trash.

---

### Post by rgb1701 on 2011-03-24
> **texas.chef94 said:**
> I would appreciate your carrying this thought/process a bit further.
I suddenly find myself in need of a data partition and I have set one up in hopes to go from there.
Could you point me to a resource or give me the terminal commands to get full permission, as well as how exactly do I access to write to after this is done. Thanks

I assume your DATA partition (/dev/sda5) appears in Places>Removable Media?

If you click on it there, does it mount (show up on the desktop) and can you read/write to it?

Assuming it appears in your Places>Removable Media menu, just add the command

gvfs-mount -d /dev/sda5

to your 

System > Preferences > Startup Applications

per 

[http://sukiprattle.blogspot.com/2010/07/automounting-partition-using-gvfs-mount.html](http://sukiprattle.blogspot.com/2010/07/automounting-partition-using-gvfs-mount.html)

---

### Post by rgb1701 on 2011-03-24
I added the partitions I wanted automounted to 

System > Preferences > Startup Applications

using gvfs-mount-d for each partition, and rebooted.

It works!

Now all we need is a simple one panel GUI to check box the partitions we want automounted this way with gvfs-mount, and we'll be set :D

A simple check box added to System>Administration>Disk Utility or elsewhere would be a great help (hint hint) ;)

---

### Post by Morbius1 on 2011-03-25
[http://sukiprattle.blogspot.com/2010/07/automounting-partition-using-gvfs-mount.html](http://sukiprattle.blogspot.com/2010/07/automounting-partition-using-gvfs-mount.html)


While I do admire the authors investigative skill and it does seem to be the answer for your particular requirement he does show a total lack of understanding on how fstab works:
> Why use gvfs-mount
Usually when talking about automounting on startup people would suggest user to add entries in /etc/fstab. The problem is that if we mount a partition from fstab, we need to have admin right to unmount/remount the partition. The whole point of adding an entry into fstab is to have the partition mount at boot so it's always available to the user. Why is he trying to unmount it? If he wants to mount and unmount it then leave the system set up as it is and mount and unmount it from Places. If he doesn't want to be asked for a password to mount from Places then install 10.10.
> And another uncool thing is that if we automount using mount command & entries in fstab, anything that we delete from the partition will not go into trash instead it will be deleted from your harddisk as soon as you click delete. You wont find it in trash, believe me.I don't know how he set up his fstab entry but he has total control over that.

If he set it up this way:
> /dev/sda5  /media/Data  vfat  utf8,umask=007,gid=46 0       1[COLOR=Blue]*BTW, this is the entry that Ubuntu would create for that partition had you asked it to do so during the initial install ( except it uses UUID instead of /dev/sdxy ).*[/COLOR]

Then he is correct - sort of. It will not show up in **[COLOR=Blue]his[/COLOR]** trash because [COLOR=Black]he[/COLOR] is not the owner of the partition - root it.
If he set it up this way:
>  /dev/sda5  /media/Data  vfat  utf8,umask=007,[COLOR=Blue]uid=1000[/COLOR],gid=46 0       1Then he is the owner of the partition and it will show up in his trash.

---

### Post by rgb1701 on 2011-03-25
**pysdm** appears to be a GUi tool that enables automount setup, though I haven't tried it-

[http://askubuntu.com/questions/18229/automounting-hard-disk-partions](http://askubuntu.com/questions/18229/automounting-hard-disk-partions)

[http://packages.ubuntu.com/search?keywords=pysdm](http://packages.ubuntu.com/search?keywords=pysdm)

---

### Post by vanadium on 2011-03-25
This utility is not anymore maintained and somewhat outdated. It does not support mounting by UUID, which you need in today´s computers.

---

### Post by blind2314 on 2011-03-25
> **vanadium said:**
> This utility is not anymore maintained and somewhat outdated. It does not support mounting by UUID, which you need in today´s computers.
 
 
Just curious as to the reasoning of why you "need" UUID mounting. You can just as easily mount by raw name, and the OS won't care.

---

### Post by vanadium on 2011-03-25
Device name, what you call "raw name", may change between boots. UUID's not.

---

### Post by rgb1701 on 2011-03-25
> **vanadium said:**
> Device name, what you call "raw name", may change between boots. UUID's not.

Correct.

Assuming "raw name" means /dev/sdXY, this is a POOR method to reference partitions for mounting, because that designation can change between reboots.  This means it's a RELATIVE partition referencing method.

An ABSOLUTE partition referencing/identification method is needed.

The two best ABSOLUTE referencing methods for partitions are by UUID or disklabel.

I prefer disklabel, because it is trivial to update by the user, you can call it whatever you want, from the old familiar Windows style C, D, E, etc, to plain english labels like Data, Videos, Photos, DVR, MythTV, etc.  These won't change between reboots, or removing the drive and plugging it into another computer, etc.  The disklabel acts as a simpler user friendly proxy for the UUID for that partition

The UUID can still be used by the OS for it's internal technical housekeeping and to resolve conflicts with identical disklabels, but there is little reason for normal user's to ever know about it.

It amazes me how these simple usability issues with disc mounting treament are still cropping up in 2011 in Linuxland.

It wasn't too long ago (pre 2004?) when we had to manually mount optical discs, rather than the automounting behavior we expect today.

Don't know why we still go around in circles with mount/automount issues and policies for hard disks, whose behavior changes depending on the filesystem type (fat32/ntfs/etx2/3, etc), hard disk connection method (internal IDE/SATA vs USB/Firewire) and other variables.

We need uniform disk/partition mounting behaviors.

To be fair, I experienced similar issues in my Windows (win98SE/XP) days years ago.  As I added hard disks and USB disks and changed partitions, drive letter assignments (D:, E:, etc, analogous to /dev/sdb, /dev/sdc, etc) would change, and the same physical drive would get a different letter (or letters, dependig on number of partitions).  Plus, I never used anything but fat32 and NTFS then, while Linux supports FAR more by default, which complicates issues.

So, always refering to partitions using an absolute identifier like UUID first, then disklabel (convenience for the user, especially non-techie users), is probably the best way to finally resolve the floating partition references problem.

---

