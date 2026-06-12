---
title: "Partitioning Help with gparted"
date: 2012-07-04
forum: General Help
---

### Post by hank22077 on 2012-07-04
I'm not quite sure how to partition my dual-boot Windows Vista and Ubuntu 10.04 LTS.

I've gotten the part of the hard drive I want allocated to Ubuntu, but don't know how to partition my Ubuntu install.
I can't find any threads to help.
So I've attached a screenshot of my gparted screen.

Thanks

---

### Post by Vaphell on 2012-07-04
your sda4 looks messy
you have 4 swaps, 2 ext4 partitions and 2 small ntfs partitions. Basic install requires single swap and single extX partition.
What do you want to have there?

---

### Post by msammels on 2012-07-04
Hey,

Could you tell me how you want to do this? What sda do you want Ubuntu on? I mean like /dev/sda1, /dev/sda2 or what? :)

---

### Post by hank22077 on 2012-07-05
> **Vaphell said:**
> your sda4 looks messy
you have 4 swaps, 2 ext4 partitions and 2 small ntfs partitions. Basic install requires single swap and single extX partition.
What do you want to have there?

Yes, this is all I want

---

### Post by hank22077 on 2012-07-05
> **msammels said:**
> Hey,

Could you tell me how you want to do this? What sda do you want Ubuntu on? I mean like /dev/sda1, /dev/sda2 or what? :)

I'd say /dev/sda4 , since it seems to be my primary Ubuntu install spot

---

### Post by oldfred on 2012-07-05
sda4 is the extended partition which holds many logical partitions. Are you going to totally reinstall or want to move things around?

If totally reinstalling what is in the two smal NTFS partitions sda5 & sda6? Is this data you want to save?

You will have to use gparted from a liveCD and right click on any swap with the little key showing it is mounted and right click swap-off. You cannot work with mounted partitions as shown with the key icon.

If you have no data to save in any of the partitions delete all of them and leave the space unallocated. Then from the Ubuntu installer, choose to install to the unallocated space or side by side. Do Not choose anything that says it will erase the entire drive.

Why is gparted have the waring next to your NTFS boot partition? click on the icon and it will tell you more. You many need chkdsk or something, as Linux will not open a NTFS partition that needs chkdsk to prevent further damage that then chkdsk may not be able to fix.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Vaphell on 2012-07-05
do you need those ntfs partitions (sda5, sda6)? ntfs = windows origin.

Have you installed ubuntu earlier, because sda11 looks pretty full?
Either way, run gparted from liveCD/USB, kill ext4 and swap partitions (but backup any data you want to preserve first) and create them from scratch in the freed space. 1G for swap (swap can be reused and you don't need more than 1 even with multiple linux installations), the rest of disk space goes to ext4 with / mountpoint.
You could create separate /home partition (allowing user configuration/customization to survive system reinstallation which can be useful) but sadly there is not enough space for it to make much sense. Just for your information - another extX partition, explicitly marked as /home in the 'mount point' column.

---

### Post by msammels on 2012-07-05
In that case, do you think it would be a good idea to remove /dev/sda5+ and do a fresh install on /dev/sda4, or am I missing something? :)

---

### Post by hank22077 on 2012-07-05
OK, thanks for all the advice and help guys; just lemme take it all in and I'll post responses.

Thanks again

---

### Post by hank22077 on 2012-07-06
OK:
I just done a fresh install.
I was going to try the upgrade to the new 12.04 LTS; per these instructions: [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS")

However, while doing the recommended package upgrades, underlined in bold below:

"To upgrade from 10.04 LTS on a desktop system before then, upgrade over the network with the following procedure.

    1.Start System/Administration/Software Sources
    2.On the Updates tab, set Show new distribution releases: to Long term support releases only, then press Close.
    3.Press Alt-F2 and type update-manager -d
        1.Click the Check button to check for new updates. _**If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.**_
        2.A message will appear informing you of the availability of the new release. Click Upgrade. 
    Follow the on-screen instructions."

My 'town' had a power-serge, interrupting my upgrades.
When my computer rebooted I ha nothing.
Fortunately I did have backups of Ubuntu and Windows; but, had to use a live cd to reinstall Ubuntu and get to my files.

This, I believe is why I have so many partitions.
No, I do not wish to remove Windows (@ this time), however I do want to re-partition Ubuntu to use ALL the space allocated to it, w/o the seperate partition...So?

Do this from gparted cd?

---

### Post by Vaphell on 2012-07-06
- get 12.04 cd/usb (you were going to upgrade anyway, clean install is much better)
- start installation procedure ([http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/))
- in partitioning phase pick manual config ([http://howtoubuntu.org/wp-content/uploads/2012/04/3-Choose.png](http://howtoubuntu.org/wp-content/uploads/2012/04/3-Choose.png) 'something else') which means gparted.
- delete ext4 and swap partitions (destroys all data on them)
- use free space to create fresh swap and ext4 partition, ext4 should be marked as /
- continue with installation

you may have wanted to preserve existing ubuntu data on ext4 partitions, but i think it's not feasible. You could remove 1 ext4 (and redundant swaps) and make the other ext4 to expand to eat the freed space (data on deleted one will be lost either way), but resizing partitions is an annoyingly lengthy process (at least it was when i tried it last time). Removing and creating from scratch is almost instant and even with backing up to some external hdd and restoring from it, the process should be much faster than playing with resizing - but know that you have the possibility.
In case of resizing you would have to go the upgrade route.

---

### Post by hank22077 on 2012-07-07
Well gparted wasn't much help, even on live cd.
So, since I have backups, I'm just doing a fresh install of Ubuntu, after removing my messed up partitions.

Wanted to try 12.04, but don't think my computer is compatible. Trying 11.10 a while back didnt workout. 
So, I needa go over the docs to figure out how it'll work on my system.

Thanks again, for every1s help. I'll repost later

---

### Post by hank22077 on 2012-07-07
> **hank22077 said:**
> Well gparted wasn't much help, even on live cd.
So, since I have backups, I'm just doing a fresh install of Ubuntu, after removing my messed up partitions.

Wanted to try 12.04, but don't think my computer is compatible. Trying 11.10 a while back didnt workout. 
So, I needa go over the docs to figure out how it'll work on my system.

Thanks again, for every1s help. I'll repost later

BTW, I have burned 12.04 on cd , and checked out [https://help.ubuntu.com/12.04/installation-guide/amd64/index.html](https://help.ubuntu.com/12.04/installation-guide/amd64/index.html) ; but would like to run it as dual boot with Windows Vista, and my Ubuntu 10.04.

Is this possible?

---

### Post by Vaphell on 2012-07-07
> but would like to run it as dual boot with Windows Vista, and my Ubuntu 10.04.

dual boot or triple boot then?
if dual boot (Vista+12.04) then you need 1 ext4
if triple boot(Vista+10.04+12.04) then obviously you need another ext4 to host new installation.

---

### Post by hank22077 on 2012-07-07
> **Vaphell said:**
> dual boot or triple boot then?
if dual boot (Vista+12.04) then you need 1 ext4
if triple boot(Vista+10.04+12.04) then obviously you need another ext4 to host new installation.

Thanks guys, my bad.
Actually, I did mean triple boot.
Sorry, I am still fairly new to Ubuntu.
I've learned alot; just still get stuck

---

### Post by Vaphell on 2012-07-07
...crap ;-)

do we still have the disk structure like on the screenshot attached?
sda11 is 10.04 and you want to preserve it?

is sda7 free to use? if so you can install 12.04 into it (select / mount point during install).
Remove 3 of 4 swaps and expand neighboring ext4 to consume the freed space (takes time).
```

before: [     ext4     ][ ext4 (10.04) ][ swap ][ swap ][ swap ][ swap ]
after:  [ ext4 (12.04) ][               ext4 (10.04)           ][ swap ]
```

---

### Post by hank22077 on 2012-07-07
Thanks, LinuxMaster007, I'm gonna try it n post back.

Yes, Vaphell, I've made the free space; now gonna try the install.

Thanks, again evry1

---

### Post by hank22077 on 2012-07-08
Well, forget about the triple boot.
Didnt even try it.
After, gettin my Ubuntu 10.04 re-installed; I ended up with booting issues neway.
My computer is 'locked' to boot from cd.
I'm usin my Ubuntu cd now.
The gparted utility under Administration, shows the partitions for Windows Vista and Ubuntu 10.04, but show blank space.
The gparted live cd is the same.
I was backing up Windows for my wife's laptop, so I could use more of the desktop for Ubuntu. But, I dont have all the data backed up and no recovery disk.
So, any suggestions? Windows partitions are there, but, like I said, all partitions seem blank.
BTW, do I needa post this issue elsewhere?

---

### Post by oldfred on 2012-07-08
Is gparted have any icons showing errors or warnings next to the partitions?

It will not show data in the partitions if it cannot mount the partition. And it will not mount partitions that need chkdsk from a Windows repairCD or e2fsck from Linux.

You should have a repairCD or liveCD or USB for the current version of every system you have installed. But I have used a Windows 7 repairUSB to run chkdsk on my XP install.

If you have another computer or a friend with Windows preferably the same 32 or 64 bit and Vista or 7 version.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Vaphell on 2012-07-09
could you post the screenshot with gparted window or the output of **fdisk -l** in terminal?

---

### Post by hank22077 on 2012-07-09
fdisk -l output:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000588f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         141     1126400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             141        8555    67584000    7  HPFS/NTFS
/dev/sda3            8555       11390    22776271+   7  HPFS/NTFS
/dev/sda4           11390       19458    64801793    5  Extended
/dev/sda5           13782       13922     1126400   82  Linux swap / Solaris
/dev/sda6           13922       19225    42599424   83  Linux
/dev/sda7           19225       19458     1865728    7  HPFS/NTFS
/dev/sda8           11390       13782    19208192   83  Linux

Partition table entries are not in disk order

---

### Post by oldfred on 2012-07-09
Did you change NTFS partitions around somehow?

Your original screenshot showed data in sda1 & sda3, but now it shows no data? and no errors on mounting.

---

### Post by hank22077 on 2012-07-09
> **oldfred said:**
> Did you change NTFS partitions around somehow?

Your original screenshot showed data in sda1 & sda3, but now it shows no data? and no errors on mounting.

Honestly, I dont know what happened. Windows was messed up.
I was gonna back up all my wifes files to put on her new laptop, and get rid of it all. Her windows pw kept gettin screwed up n we'd have to reset it through the admin account. We couldnt do any backups through the system; I was manually copying her files and saving them elsewhere. The BIOS and Setup (F2 & F10) have a password neither of us set or know. 
My Ubuntu is all that seems to work on this thing...
The Vista disk doesnt even load from the drive, even though 'boot from disk' is default. Yet, I can boot other disks.

---

### Post by Vaphell on 2012-07-09
damn, did you expand linux partition at the expense of windows partitions? in general that's not a good idea to play with windows partitions in gparted. Afaik Vista and W7 are especially vulnerable to screwups

[http://www.thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html](http://www.thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html)
> Unfortunately, some users will find that Windows 7 or Vista fails to boot after using GParted to resize a partition. This is especially true if the 'Round to Cylinders' option is left ticked - enabled is the default setting and should be changed to disabled before Resizing with GParted with Windows 7 or Vista.
It's best to use windows tools to free space and then use gparted to partition that space for linux.

10GB PQSERVICE which most likely held recovery tools allowing to restore the machine to out-of-factory state is completely broken.

---

### Post by hank22077 on 2012-07-09
> **Vaphell said:**
> damn, did you expand linux partition at the expense of windows partitions? in general that's not a good idea to play with windows partitions in gparted. Afaik Vista and W7 are especially vulnerable to screwups

[http://www.thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html](http://www.thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html)

It's best to use windows tools to free space and then use gparted to partition that space for linux.

10GB PQSERVICE which most likely held recovery tools allowing to restore the machine to out-of-factory state is completely broken.

No, I steered clear of the windows partitions...:confused:

---

### Post by oldfred on 2012-07-09
With all the partition changes it may make it more difficult but testdisk can recover old partition tables. You may lose new entries as whatever you recover cannot overlap existing partitions. If testdisk does not work and you have data you really want to recover stop using drive. Part of testdisk is photorec. But it is a long complicated process as it just scans drive for anything that looks like a file. It cannot recover file names, but can recover based on type of file and then its extension.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)
Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

Photorec can  take a very long time to scan a drive and you have to have room on anther drive to copy found data to. Then you have the task of trying to see if the recovered files are really what you want. 

I had saved a text file many times. It found all the old saved copies or parts there of. I was never sure I had last saved copy but between backup that was too old and bits from files I recovered most of those text files.

---

### Post by hank22077 on 2012-07-09
Thanks, oldfred

---

### Post by hank22077 on 2012-07-18
I marked this as solved, cuz the initial issue was.
However, even though most of us dislike windows, 
I could still use advice on the Vista "screw up(?)"

I have backup files and a restore disk.
Nothing really seems to work.

I dont really care to have or use Windows, but it would be nice to make certain I have everything restored for my wifes files to be put on her new laptop.

Like I said, I have '_***most***_' files backed up.
Just needa be sure.

Any additional advice...other than payin Microsoft? ( :D )

Thanks

---

### Post by oldfred on 2012-07-18
As Vaphell mentioned before, it is best to use Window to resize itself if Vista or 7. Only use gparted to create or resize Linux partitions. The Vendor recovery often wants the entire drive as it was when purchased and may not work with the Linux partitions still there. It just recreates Vista system. 

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by hank22077 on 2012-07-18
Ok.
Thanks again, oldfred

---

