---
title: "Expanding an Ubuntu System Partition"
date: 2009-07-21
forum: General Help
---

### Post by drs305 on 2009-07-21
**[SIZE=3][COLOR=Navy]Introduction[/COLOR][/SIZE]**
This post originally concerned a bug in Jaunty which created a partition which was too small to support a normal Ubuntu installation. Since Jaunty reached it's End of Life in October 2010, I am removing the section which details how to identify the bug and correct it. The information on how to expand the Ubuntu / partition remains valid an is left here to help those wishing to enlarge it.

[COLOR="DarkRed"]Note for Wubi Users:[/COLOR] This guide cannot be used to resize a Wubi installation within Windows. For guidance on how to transfer a Wubi installation to it's own partition, please refer to [this link]("http://lubi.sourceforge.net/lvpm.html") or the [WubiGuide]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?").


**[SIZE=3][COLOR=Navy]Do I Need More Space for My Ubuntu Installation?[/COLOR][/SIZE]**

Check your free space and system partition size by running the following command from a terminal. To open a terminal: Applications > Accessories > Terminal.

```

df -h | grep "/dev/sd"

```Look for the " **[COLOR=DarkRed]/[/COLOR]** " Ubuntu system partition and check the percentage in use. The original figures were for the Jaunty bug, which now is irrelevant. However, even on recent installations, look at the percentage in **bold**. If it is near 100%, you are running out of room.
> 
Filesystem            Size  Used Avail Use% Mounted on
**[COLOR=DarkRed]/dev/sda5 2.3G 2.3G 0 [B]100%** /[/COLOR][/B]It is telling you that the Linux system ( / ) is only 2.3GB in size and is 100% full. That partition is too small to run Ubuntu effectively. Although this guide is written to help users with an initial installation that created a system partition that is too small, it can also be used to expand *any* system partition which has become too small. 

If you have a system partition which has performed reasonably well in the past but suddenly appears full, you may want to investigate why your system partition is now full: [_RecoverLostDiskSpace_]("https://help.ubuntu.com/community/RecoverLostDiskSpace").

*Gparted* provides an excellent graphical depiction of your system's partitioning. You can also inspect the drive's partitions via terminal commands. After entering the following command you will be asked for a password. Type your password. You won't see it as you type. Press ENTER when you have typed it.
> ```

sudo fdisk -l # Lowercase L, not a number. 

```On a Windows installation, you will normally see the Windows partition or two, an extended partition, the Linux partition, and a swap partition. This is a typical layout:
[quote]
Device Boot Start End Blocks Id System
/dev/**sda1** 1 1321 10606592 27 Unknown
/dev/**sda2** * 1321 30076 230971576 7 HPFS/NTFS
/dev/**sda3** 30077 30401 2610562+ 5 Extended
/dev/**sda5** 30077 30379 2433816 83 Linux
/dev/**sda6** 30380 30401 176683+ 82 Linux swap / Solaris
In this case, **sda1** is a Windows rescue partition, **sda2** is the Windows partition (HPFS/NTFS), **sda3** is the Extended partition, **sda5** is the Ubuntu installation, and **sda6** is the Ubuntu swap partition.[/quote]

[SIZE=3]**[COLOR=Navy]I Need More Space. What Are My Options?[/COLOR]**[/SIZE]
[LIST]
[*]Expand the existing / partition (instructions below).
[*]Reinstall the system and use a larger partition.
[*]Move $HOME to a another partition. Here is one link on [moving your $HOME partition]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html")
[*]Move your data/music/other files to a non-system partition. On a normal Ubuntu installation the system files should occupy less than 10 GB of disk space.
[/LIST]

**[COLOR=Navy][SIZE=3]Some Basic Rules for Expanding the [B]/** System Partition:[/SIZE][/COLOR][/B]
[LIST=1]
[*]Backup your important data (from all partitions).
[*]If you are going to change the Windows partition, defrag it at least once.
[*][COLOR="DarkRed"]I recommend using the Windows partition with a Windows partition manager. *gparted* is an excellent tool but if you are already comfortable with a Windows partitioner, use it to change the Windows partition. Use the Windows Disk Management tool for windows partitions if at all possible for the Windows partitoons.[/COLOR]
[*]Run* gparted* from the LiveCD/Installation CD or a SystemRescue CD. You must do this because the Ubuntu system partitions must be unmounted to change them.  
[*]To access gparted from the LiveCD: System > Administration > Partition Editor.
[*]If you are shrinking Windows, leave it some extra space. Don't resize it all the way to the minimum - leave some free space within the Windows partition.
[*]Unmount any swap partitions (linux-swap). *A swap partition is mounted by default on the LiveCD and must be unmounted.* Select the swap partition, then from the main *gparted* menu: Partition > "Swapoff". If you see "Swapon", the swap partition is already unmounted.
[*]No partitions you are trying to change should be mounted. Mounted partitions have a "keys" symbol in the lower section of gparted.
[*]When expanding partitions, the unallocated space must be touching the partition you want to grow. There cannot be any other partitions between the two.
[*]Both the unallocated space and the partition to be expanded must be in the same area - both inside the extended partition, or both outside the extended partition. The extended partition has a light blue border. In the simplest terms, there can be no light blue line between the two partitions or unallocated space you are working with.
_[ATTACH]122547[/ATTACH]_
[*]When resizing a partition, do not make it smaller than the data currently contained on it. Data is shown in yellow. If you move the borders into the yellow area you will lose data.
[*]If deleting a partition in the extended partition, all partitions with a higher designation must be umounted first. If the system partition has a higher number than the one you are trying to delete you will need to use the LiveCD or another utility CD so you can umount the system partition.
[*]Resizing a large partition can take a long time - more than an hour or longer. The bigger the partition, the longer the time. Don't stop the operation until it completes.
[/LIST]
*[COLOR=DarkRed]**[SIZE=3]When asking for help, a [I]gparted* screenshot is very valuable. To take and post a screenshot:[/SIZE]**[/COLOR][/I]
From the Ubuntu Main Menu: Applications, Accessories, Take Screenshot. The screenshot by default is saved on the user's Desktop. To add it to a post, at the bottom of the post page is a section called "Additional Options". Click on "Manage Attachments", browse to the snapshot location and add the screenshot.

[SIZE=3]**[COLOR=Navy]How Large Should My Ubuntu Partition Be?[/COLOR]**[/SIZE]
This is highly subjective and depends in part on how much free and unallocated space you have available. The current *absolute minimum recommended* system partition size is 4GB. The *recommended minimum is 8GB*.

Providing the Ubuntu partition with more space will give the user more options for growth or future partitioning changes. These options include creating a separate /home partition, making one or more data partitions, etc. Remember that it is much easier to split a large partition than it is to grow one!

Purely subjective, and without knowing the details of your system, I'd use a 10-15GB / and a 2GB swap partition. The 10-15GB should be expanded by the amount of *data/music/etc* you intend to store in your $HOME folder, unless of course you have a separate /home partition. So if you intend on keeping 30GB of music files in your $HOME folder, the size of your Ubuntu partition should be 40-45GB minimum.

**[SIZE=3][COLOR=Navy]Expanding the [B]/** Partition: Step by Step[/COLOR][/SIZE][/B]
A few stipulations about these steps:
[LIST]
[*]The screenshots are not of an actual system. Do not use the partition sizes or designations in the graphics when resizing your partitions. They are only abstract examples and are not proportional.
[*]The following steps assume you have read and followed steps 1-10 above, including backing up your data, running gparted from a LiveCD, unmounting the partitions, and turning off swap.
[*]For this example, we will assume the original partitioning is:
[LIST]
[*]sda1 - Windows recovery partition.
[*]sda2 - Windows.
[*]sda3 - Extended partition.
[*]sda5 - Ubuntu system / partition.
[*]sda6 - Ubuntu swap partition.
[/LIST]
 
[*]Here is a screenshot of a typical drive following an Ubuntu installation on a Windows computer. Note this is not a Wubi installation.
_[ATTACH]122546[/ATTACH]_
Note the Windows recovery partition is full, the Windows partition has lots of free space, the Ubuntu partition is contained *within* the extended partition and is full or nearly so.
[/LIST]

[LIST=1]
[*]Shrink the Windows partition (sda2):
[*]Note: Reducing the size of the Windows partition is best done using Windows software. If this is not possible or desired, use the following steps.
[*]This [YouTube video]("http://www.youtube.com/user/CoverlessTech#p/a/E8F1691C3779BDC3/2/cXZKRyvSqwQ") shows how to do it, Start at the 4:55 mark. (Thanks to Robster2 for providing the link.)
[*]Select the partition and from *gparted's* main menu, select "Partition > Resize".
[LIST]
[*]Slide the right border of the Windows partition to the left. How much is up to you but remember the Ubuntu partition must be at least 5GB.
[/LIST]
[*]Select sda3, the Extended partition. It is easier to select this partition from the list in the lower pane.  _[ATTACH]121893[/ATTACH]_
[LIST]
[*]Drag the left border (light blue) of the Extended partition to the left, touching the Windows partition and leaving no *unallocated* space (gray). _[ATTACH]121890[/ATTACH]_
[/LIST]
[*]Select the Ubuntu / system partition.
[LIST]
[*]Drag the left border of the Ubuntu partition all the way to the left. The Windows partition and Ubuntu partition should now be next to each other, divided by the Extended partition's light blue border. _[ATTACH]122083[/ATTACH]_
[/LIST]
[*]Confirm the Ubuntu partition is now the desired size.
[*]Hit *Apply*.
[LIST]
[*]This operation could take more than an hour to complete, depending on the partition sizes.
[*]Do not interrupt this process. It could result in data loss.
[*]If using a laptop on battery, make sure it is sufficiently charged to complete the operation before the battery depletes.
[/LIST]
[/LIST]


**[SIZE=3][COLOR=Navy]Related Links:[/COLOR][/SIZE]**
[Resizing Linux partitions]("http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html") by *srs5694*
[_Installation/SystemRequirements_]("https://help.ubuntu.com/community/Installation/SystemRequirements")
[SOLVED: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")
[_HowtoPartition_]("https://help.ubuntu.com/community/HowtoPartition")
[_Partitioning Basics_]("http://ubuntuforums.org/showthread.php?t=282018")
Troubleshooting:
[_RecoverLostDiskSpace_]("https://help.ubuntu.com/community/RecoverLostDiskSpace")
[_Disk Full - Check Your Trash_]("http://ubuntuforums.org/showthread.php?t=898573")

[_Launchpad Bug Report_]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/404910")

---

### Post by michy99 on 2009-07-21
Excellent. Thanks for taking the time to write this up. I have bookmarked it to point people to when they have this problem.

---

### Post by merlinus on 2009-07-21
+110!

Thanks for writing this up.  It would seem there is some sort of bug with the 9.04 partitioner that causes this problem for a fair number of folks.

---

### Post by rafita on 2009-07-21
Thanks a lot for such detailed instructions!

I don't have the problem described here (not having enough size for Ubuntu),
however, I would like to give Windows less space *and Ubuntu more) than what 
it has now. I assume these instructions should work, right?

---

### Post by drs305 on 2009-07-21
> **rafita said:**
> Thanks a lot for such detailed instructions!

I don't have the problem described here (not having enough size for Ubuntu),
however, I would like to give Windows less space *and Ubuntu more) than what 
it has now. I assume these instructions should work, right?

Yes they should. The order of your partitions may not be exactly the same but the process would be the same as long as the Windows and Ubuntu partitions are next to each other. If they are not, additional movement of these and other partitions would be needed first.

---

### Post by grayn0de on 2009-07-21
I think this should eventually make it's way into the Tutorials section of the forum. Very nice writeup. :D

---

### Post by kg4cna on 2009-07-22
Excellent!  Thank you very much!  I will save for future reference.

Agree it should be moved to Tutorials.

Thanks!
Allen

+11111111111111111111111

---

### Post by lukjad on 2009-07-25
Well worth the read, and very useful. Thanks for the tutorial drs305.

---

### Post by RLBarto on 2009-07-28
I was able to use gparted to free up some space from the XP partition on my LENOVO S10 but not to unmount partitions.  It says they are in use. Used both a live dvd through a USB drive and the flash drive with the retro live version and I cant do it.  Any advice for this novice will be appreciated.

---

### Post by drs305 on 2009-07-28
> **RLBarto said:**
> I was able to use gparted to free up some space from the XP partition on my LENOVO S10 but not to unmount partitions.  It says they are in use. Used both a live dvd through a USB drive and the flash drive with the retro live version and I cant do it.  Any advice for this novice will be appreciated.

A swap partition may be mounted, even with the LiveCD. That is the default. Check by highlighting any red-bordered partition(s) (swap partitions) to see if they are mounted: Select Partition, Swapoff to unmount them. 

Once you turn off swap, the swap and extended partitions should be unmounted and you shouldn't have any other mounted partitions (no 'key' symbols).

---

### Post by RLBarto on 2009-07-29
Thank you for your help.  I was able to unmount my partitions and resize  them successfully.

---

### Post by madhavhmk on 2009-08-20
I have very less space available on / but when i run gparted from live cd, 
it is indicating the entire HDD as unused single partition...!!! even though I have many partitions already....

I am outputting the fdisk -l here:

255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              10        1315    10485760    7  HPFS/NTFS
/dev/sda2   *        1315        9147    62914560    7  HPFS/NTFS
/dev/sda3            9148       19458    82815716    f  W95 Ext'd (LBA)
/dev/sda4   *       19131       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda5            9148        9755     4883728+  83  Linux
/dev/sda6            9756       19130    75302912    7  HPFS/NTFS
/dev/sda7           19131       19458     2620416   dd  Unknown


thanks in advance..!!!!

---

### Post by drs305 on 2009-08-20
> **madhavhmk said:**
> I have very less space available on / but when i run gparted from live cd, 
it is indicating the entire HDD as unused single partition...!!! even though I have many partitions already....

I am outputting the fdisk -l here:

255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              10        **[COLOR="Red"]1315[/COLOR]**    10485760    7  HPFS/NTFS
/dev/sda2   *        [COLOR="Red"]**1315**[/COLOR]        9147    62914560    7  HPFS/NTFS
/dev/sda3            9148       19458    82815716    f  W95 Ext'd (LBA)
/dev/sda4   *       19131       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda5            9148        9755     4883728+  83  Linux
/dev/sda6            9756       19130    75302912    7  HPFS/NTFS
/dev/sda7           19131       19458     2620416   dd  Unknown


thanks in advance..!!!!

madhavhmk,

Often when you can't see the partitions in gparted it is because the partition table has errors in it. Note that sda1 and sda2 both share a common cylinder. That may be the problem. 

I defer to others on partition table repair. It might be best to start a new thread more on topic with an appropriate title or do a search for partition table repair. It would probably be viewed by more viewers with experience with these types of issues.

You can search for doskfsck and testdisk among others. Be sure to back up important data before conducting any partition table modifications.

---

### Post by kajgot on 2009-08-21
Hi, I turned off the swap (Partition, Swapoff) and the only thing that happened is that the 'key' symbol next to "linux-swap" dissapered. However, I still have 'key' symbol next to two other entries in the GParted: one is next to ext3 and the other is next to extended. I tried clicking ext file system and doing "unmount" but it told me that it can't be done because ... Most likely other partitions are also mounted on these mount points and I was advised to unmount them manually.

Any idea what to do now? 

By the way, although I am a bit desperate for not being able to do what others seem to be able to with ease, I am pretty surprised that I actually managed to shrink NTFS filesystem! For a newbie like me, that's something :)

---

### Post by kajgot on 2009-08-21
> **kajgot said:**
> Hi, I turned off the swap (Partition, Swapoff) and the only thing that happened is that the 'key' symbol next to "linux-swap" dissapered. However, I still have 'key' symbol next to two other entries in the GParted: one is next to ext3 and the other is next to extended. I tried clicking ext file system and doing "unmount" but it told me that it can't be done because ... Most likely other partitions are also mounted on these mount points and I was advised to unmount them manually.

Any idea what to do now? 

By the way, although I am a bit desperate for not being able to do what others seem to be able to with ease, I am pretty surprised that I actually managed to shrink NTFS filesystem! For a newbie like me, that's something :)

I fixed it! I fixed it myself! 

Actually, I screwed up myself first place. I wasn't paying attention that you MUST run Ubuntu from the CD, NOT from the computer. It actually make sense (no wonder that Ubuntu didn't let me unmount itself). 

Well, I guess I should have read the post more carefully! Sorry if I caused any headaches. 

My first linux problem solved!

---

### Post by hovrashko on 2009-10-03
[SIZE=4]didn't go very good form me..

during extension of a ext3 pop up an error, and show all added free space turns out full, for instance i had 10 gb full before and 7 free, after extension i have 50 gb full and 7 free, and when restarted in Gparted shows 57 gb for ext3 but in disk analyzer shows 17? 
 what's happening? where hell 40 gb came from and why i cant accesses them?
:confused:
thanks[/SIZE]

---

### Post by drs305 on 2009-10-03
hovrashko, 

Please you post the results of the following commands:
```

df -Th
sudo fdisk -l  # Lowercase L

```

If you use Gparted, a screenshot of your current drive would be very helpful.

---

### Post by fallenashes on 2010-04-19
Thanks for the thorough post, this thread and forum in general is amazing. But I would like to talk about what stumped me forever.

1.  Right click the linux swap and click swapoff.  This grays out the needed options otherwise.
2. You have to think of terms of unallocated space, not partitions.
3. Gparted is not a "merger" type partition editior, it is an add-subtract to manipulate unallocated space.

If I am wrong/misguided please feel free to correct me.

---

### Post by Keskasidvar on 2010-08-14
Im Dual booting Ubuntu 10.04 with Win7 and am thinking about uninstalling Win7, will Ubuntu automatically take the open space for itself or will i need the change the partition manually, and is there a way i can do this from the terminal?

---

### Post by drs305 on 2010-08-15
> **Keskasidvar said:**
> Im Dual booting Ubuntu 10.04 with Win7 and am thinking about uninstalling Win7, will Ubuntu automatically take the open space for itself or will i need the change the partition manually, and is there a way i can do this from the terminal?

You would have to adjust the partitions manually. Assuming you want to keep your current Ubuntu installation, the most common way would be to use the LiveCD, open gparted, delete the Windows partition (if you are sure you want to do that) and then resize the Ubuntu / partition. 

Depending on the size of the adjustment, moving the Ubuntu partition could take a long time (1 hour+). 

How you incorporate the old space depends on your existing partition setup - primary vs extended partitions, etc. When you are ready to change things, open up a new thread and post a screenshot of your current setup as seen by gparted. We'll then be able to give you more specific advice if you need it.

---

### Post by coolman98 on 2010-10-06
thanks.

---

### Post by bluexrider on 2011-11-03
Great tutorial +1

---

### Post by koftis on 2011-12-09
I 've just completed the resizing (using partition manager for the windows drive and gparted for ubuntu swap and ext4)
I had problems booting..
so i reinstalled grub via live cd..

Now iam able to login in both windows and ubuntu 10.04 But i get errors before i sign in error : no argument specified(dchk in Xp and some warnings in 10.04)..

Can i fix this?

May i remove and reinstall grub?

Or should i use the rescatux live cd instead?

I couldn't fix it after reading this [thread]("http://ubuntuforums.org/showthread.php?t=1662142&page=2")

Thx in advance!:)

---

### Post by drs305 on 2011-12-09
> **koftis said:**
> I 've just completed the resizing (using partition manager for the windows drive and gparted for ubuntu swap and ext4)
I had problems booting..
so i reinstalled grub via live cd..

Now iam able to login in both windows and ubuntu 10.04 But i get errors before i sign in error : no argument specified(dchk in Xp and some warnings in 10.04)..

Can i fix this?

May i remove and reinstall grub?

Or should i use the rescatux live cd instead?

I couldn't fix it after reading this [thread]("http://ubuntuforums.org/showthread.php?t=1662142&page=2")

Thx in advance!:)

Referencing the link you provided, just confirm that if using Grub 1.99 you are using "--set=root" and in Grub 1.98 you are using "--set ". You can check the version of Grub you are using with "grub-install -v" and you should probably check the actual menu at boot by pressing 'e' and looking at the search line to see if you have the proper format.

Have you tried running an fsck check in Ubuntu and chkdsk in Windows?

For Ubuntu, if you are already logged on, you can schedule a check on the next boot by running the command "sudo touch /forcefsck". Or if booted to the LiveCD run "sudo e2fsck -f -y -v /dev/sdXY" (X the drive, Y the partition) with that partition NOT mounted.

In XP, I believe you open a terminal and run "chkdisk c: /F" but as I don't use Window please confirm the way to accomplish this.

---

### Post by koftis on 2011-12-10
I have grub 1.98 i've tried the edit option with no success..
But i've just took a photo from the error 
> "error:No arguments specified,
vga=795 is deprecated.Use gfxpayload=1280x1024;
linux command instead.
Press any key to continue.."

tried to clean install grub but i failed, then **live ubuntu cd reinstall grub** same error "no arguments specified" but i'm not trying to fix it, as far as i can boot normally..
After the repartitioning **i cannot see the sda9(windows partition)** in places, and i could not mount it manually using the **Disk Utility **- no problem under Xp
(My linux installation is in sda8)

---

### Post by drs305 on 2011-12-10
From the grub menu, try editing the entry (press 'e') and delete the entire 'search' line, then CTRL=x.

If it still doesn't work, install the Boot Repair tool (see link in my signature line). You can run it from the LiveCD or your normal system. The link to Boot Repair is in my signature line.

If that doesn't fix it, please start a new thread, and from Boot Repair you can run the boot info script. Post the link to RESULTS.txt and the error message you posted above.

---

### Post by Ben Gallagher on 2012-04-24
Hello!
I'm new to this forum and Ubuntu, so I'm not sure if this is the place to ask this question, but here goes. I recently upgraded to Ubuntu 10.04 LTS (Lucid Lynx) from an earlier version. I had set up partitions myself during the previous install, thanks to helpful tips on the internet, but during the upgrade I did the more automatic upgrade process. I think somewhere along the way I ended up with extra partitions, and the size of my /home partition is too small. I took a screenshot in Terminal of the size of the partitions I have at the moment, it looks like this:


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xff292a99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1529    12281661   27  Unknown
/dev/sda2   *        1530        5650    33095676    6  FAT16
/dev/sda3            5651        6041     3140707+   7  HPFS/NTFS
/dev/sda4            6042       14593    68693909+   5  Extended
/dev/sda5            6042        6888     6796424   83  Linux
/dev/sda6           14203       14593     3140676   82  Linux swap / Solaris
/dev/sda7            6888        7534     5191680   83  Linux
/dev/sda8            7534        7570      290816   82  Linux swap / Solaris

Partition table entries are not in disk order


I suspect I need to use Gparted to expand the size of one of these partitions, and perhaps to delete one as well? Any advice on what to do and the process I should use would be very much appreciated. And if this isn't the place to ask these questions, redirection to the appropriate forum is also welcome! Thanks in advance,
Ben

---

