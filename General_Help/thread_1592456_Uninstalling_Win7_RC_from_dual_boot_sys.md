---
title: "Uninstalling Win7 RC from dual boot sys"
date: 2010-10-10
forum: General Help
---

### Post by maja_z on 2010-10-10
Hi!

About a year ago I set up a dual boot system with Win 7 RC as the primary (I guess, anyway it was the first one I installed) and ubuntu kk. Since then I've basically only been using ubuntu and now I want to get rid of windows and free up the partition it occupies. 

So basically I was wondering how I should go about doing this? I haven't even tried booting in windows for a while, the RC version was only valid until June or something, so I bet it wouldn't even work. 

I don't want to do a fresh install, mainly because I've set up so many things in ubuntu, packages and drivers and the like that I haven't kept a record of and would really hate to have to do again. 

Is there a clean and neat way of doing this? Sorry if this is noobyish!

m.

---

### Post by sikander3786 on 2010-10-10
Just use your favorite partitioning software (mine is gparted), delete the Windows partition and create a new partition in the free space.

Afterwards running

```
sudo update-grub
```

will remove the Windows entry from Grub menu.

---

### Post by mörgæs on 2010-10-10
I would recommend a clean install of 10.04 or 10.10, which can erase the whole drive. If I can not convince you to do so, second best is to remove the Windoze partitions with Gparted.

---

### Post by sikander3786 on 2010-10-10
> I would recommend a clean install of 10.04 or 10.10, which can erase the whole drive.

I couldn't get to a specific reason behind that. Why bother a fresh install if you've got a system running with all the custom settings and configuration? Why bother backup blah blah blah?

Some real benefits.....?

---

### Post by konungursvia on 2010-10-10
He's right, just download gparted (the iso or disk image) burn it to a cd and boot, and in there, you will see you can delete your win partition, then resize the linux one to be larger (the whole drive).

---

### Post by oldfred on 2010-10-10
I agree with reformatting the partition. 

Depending on its size you could move /home into it so when you do want to reinstall you do not lose your user settings. 

Or you can just make it another /data partition and store some of you  data there. You can edit fstab to either mount it inot /home or mount elsewhere and link in the folders in /data into /home.

---

### Post by maja_z on 2010-10-10
yeah mörgæs, I think I'd want to stick with my configuration, but thanks!
sikander3786, is it really as simple as that? I mean (and this is probably just me being very simple) I would guess as much if I'd installed ubuntu first and windows second, but I didn't, windowss was my first one. but that sounds great!
also, with gparted, would I be able to merge the first, now free, partition with the second ubuntu one? just so I could have the system on my first partition if that makes sense?
thanks!

---

### Post by mörgæs on 2010-10-10
I was just thinking that support for 9.10 is running out in half a year, so you will soon have to think of an alternative. 

The more customised a system is, the riskier it is to dist-upgrade, so you might need a new install anyway within a short time.

---

### Post by sikander3786 on 2010-10-10
> is it really as simple as that

It is really that simple. You'll see yourself. No matter which OS you installed first and which one second, if Grub is installed, there should be no problems at all.

> also, with gparted, would I be able to merge the first, now free, partition with the second ubuntu one?

You can expand your Ubuntu partition to fill up the free space. That can be done in gparted. But it'll be better to use it as your /home partition as **oldfred** suggested above. That way, whenever you reinstall, you'll not lose your data.

> just download gparted (the iso or disk image) burn it to a cd and boot, and in there, you will see you can delete your win partition, then resize the linux one to be larger (the whole drive).

You can also install gparted inside Ubuntu. And you can also use Ubuntu Live CDs, if you want to perform some tasks that need to unmount your Ubuntu partitions.

---

### Post by oldfred on 2010-10-10
I typically do not like moving/expanding partitions left as that requires all data to be copied & verified to a new location. It can be done, has a little more risk than other partition changes but with all partition changes you need to have good backups.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)
cp without -a and copying as sudo root takes ownership (not good)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by maja_z on 2010-10-10
thanks guys, esp for the links oldfred! i'll have a look through tomorrow and hopefully will be fine on my own. 

i guess one reason to move everything is purely aesthetic, but from what i understand given i have an 'old school' hard drive, the first partition is also the fastest, so it's a bit of a waste to have 43 gig of prime real-estate  as just a data partition. so yes, ideally I would want the system there (while I save up for a system ssd).

as I said, i'll read through the tutorials, and don't worry, backup is my middle name!

p.s. also, this is what my disk looks like now (don't ask me why, I don't remember!) anything noteworthy?

$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a60b91a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41943040    7  HPFS/NTFS
/dev/sda2            5222        8486    26214400   83  Linux
/dev/sda3            8486       21540   104857600    7  HPFS/NTFS
/dev/sda4           21540       77826   452113408+   f  W95 Ext'd (LBA)
/dev/sda5           21540       77826   452113408    7  HPFS/NTFS

---

### Post by maja_z on 2010-10-11
Aw boy did I manage to mess this up already! (don't worry, its all backed up, nothing is lost (datawise) but my first partition has gone missing!)

Step 1 was me overanxiously trying to reformat the first partition while in ubuntu. I did unmount it, ran gparted and formatted it to ext4, but I got an error (didn't write it down though) something about the kernel and problems accessing... It did wipe the partition though. 
Step 1b at this point I noticed in the table that the first partition now had the "boot" flag, when it was the second one before. So fingers crossed I changed the second's flag to boot. (and rebooted later fine)
But so I figured I'd best do this again with the gparted live cd. 

Step 2 was me booting into the gparted cd, where it showed the first partition  as ext4. But because of the error before and because it only took half a second I figured I'd format it again. Now I got an error again, something again about the kernel not having access but weirdly it said something about sda5, even though it was sda1 I was formatting. Needless to say the "save details" of the error thing didn't really work for me - i.e. I did save it, but I have no idea where, because I guess my disk was unmounted anyway? I can try doing it again and copy the error text?
Step 2b and c - well then I decided to delete the partition, and create a new one in its place... all operations resulted in the same error. So now when I boot again normally the first partition is missing completely?

Sorry for the mess, any tips will be greatly appreciated!

---

### Post by oldfred on 2010-10-11
Boot flag does not really matter. Windows has to have it, grub does not use it, But some BIOS require a boot flag on a primary partition. Someone just an hour ago fixed his system just by putting a boot flag on a primary partition.

Show us your partitions with this or a screenshot from gparted.
sudo fdisk -lu

---

### Post by maja_z on 2010-10-11
thanks oldfred! i've done both, because they don't show the same thing.

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6a60b91a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    83888127    41943040   83  Linux
/dev/sda2   *    83888128   136316927    26214400   83  Linux
/dev/sda3       136316928   346032127   104857600    7  HPFS/NTFS
/dev/sda4       346034175  1250260991   452113408+   f  W95 Ext'd (LBA)
/dev/sda5       346034176  1250260991   452113408    7  HPFS/NTFS
mz@Jevgenij:~$

---

### Post by oldfred on 2010-10-11
It looks like sda1 is half changed from NTFS to ext4. I have seen before where different versions of utilities read different parts of drive and are inconsistent.

Since you have not data that you really care about in sda1 I would just try reformatting it again.

---

### Post by maja_z on 2010-10-12
Right, I tried reformatting it again in gparted live. This time I had a pen and paper ready. Here's what I get:

> calibrate /dev/sda1                                OK (green tick)
set partition type on /dev/sda1          Not OK (red do not enter sign)

libparted messages:

Error informing the kernel about modifications to partition /dev/sda5 - Device or resource busy. This means Linux won't know about any changes you made to dev/sda5 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.

Failed to add partition 5 (Device or resource busy)I don't understand what 5 has to do with anything. Could this have anything to do with swap btw? I'm not sure where I put it, but its in a folder somewhere?

Thanks!

---

### Post by oldfred on 2010-10-12
Often liveCD automount the swap partition to speed things up. If modifying anything related and often swap is in the extended partition so all logicals in the extended are seen as mounted as part of the extended. 
You can click on the swap and swapoff. It just is saying sda5 is in use, I think.

---

### Post by maja_z on 2010-10-12
> You can click on the swap and swapoff.I'm not sure I understand? My swap does not have its own partition, I believe I just gave it a folder, but I don't really know where it is? (although it might well be in sda5)

Another weird thing is this: I ran Disk utility and it says sda5 is unallocated space!? I've attached the screenshot. I can access it fine, all the data is still there, over 200 gigs worth and gparted sees it, but disk utility doesn't?

edit: OK, ignore the disk utility thing - I've rebooted and now it sees it fine. I've also found my swap. I've got a file called 4096Mb.swap on /mnt, which would make it sda2 I presume?

---

### Post by oldfred on 2010-10-12
I have always used a partition for swap. Your screenshot seems to show 3 partitions but it is saying you have 4? and it then is not showing the extended.

I might look at it with testdisk to see if it can make things more consistent.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by maja_z on 2010-10-12
Right, here's what I understand: I've got three primary partitions, and one extended which includes one logical. 
sda1 (P) the one where W7 was and is now 'unknown'
sda2 (P) bootable, this is where ubuntu is. 
sda3 (P) data partition, but its ntfs (I think I wanted that becaues of windows)
sda4 (E)
 - sda5 (L) also ntfs. 

This last fourth (sda5) partition has the following going on:
- I can access the data without a problem!
- Disk utility sometimes sees it and sometimes not (now again not) (see second screenshot I posted)
- gparted (inside ubuntu) sees it OK (see first screenshot I posted)
- gparted live I thought saw it OK, but now I noticed that it also had a 'danger!' traffic sign next to it (but because it's indented it was almost completely hidden) so I clicked on properties and got this:

> the device /dev/sda5 doesn't exist
ntfresize v.2.0.0 (libntfs 10:0:0)

ERROR(2): Failed to check '/dev/sda5' mount state:
No such file or directory.
Probably /etc/mtab is missing. It's too risky to continue. You might try another Linux distro. 
Unable to read the contents of this file system! 
Because of this some operations may be unavailable.
The following list of software packaged is required for ntfs filesystem support: ntfsprogs.

Partitions 2 and 3 are completely fine but so was 4?

---

### Post by oldfred on 2010-10-12
Since it is NTFS, you may want to run chkdsk. 

My XP install seemed fine but gparted had issues with it and I ran chkdsk and then it was ok in gparted.

---

### Post by maja_z on 2010-10-12
thanks! I've googled around a bit and found this recommendation:
> If you install ntfsprogs then there's a utility called ntfsfix which performs a  basic chkdsk and allows you to mount it cleanly. An example usage would be "sudo ntfsfix /dev/sdb1", obviously replacing the  drive and partition appropriately. would this be equivalent enough to chkdsk?

edit: the other suggestion I've found is to download a Windows Vista x64 recovery disc and run chkdsk from there? becaues apparently ntfsfix will not actually fix anything, just mark the partition as 'dirty' for it to be fixed by windows (which I do not have)? Should I give this a shot?

---

### Post by oldfred on 2010-10-12
Here are links to windows repair CDs.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by maja_z on 2010-10-12
Right, I'm not getting something?

So I downloaded the recovery disk (for Windows 7 64 bit if that matters) and booted it, got to the command prompt and first tried (naively, yes) chkdsk f: /r, which didn't work, because 'the drive doesn't exist' or something.
Then I tried chkdsk /r, which gave me an error about the drive not being locked?

I don't understand, how do I lock it?

And btw, thanks so much oldfred for sticking with me through this :) !

---

### Post by oldfred on 2010-10-12
Without the drive letter chkdsk works on the current drive which is probably your Cd so chkdsk will not work.

I do not have win7 but just to learn did download a repair Cd to see if I could copy it to a USB key from linux. 

diskpart 
exit   # to get out of diskpart
list disk    #should list volumes & drive letters

If it does not see your NTFS partition or the f: still does not work, testdisk has some advanced tools.

Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by maja_z on 2010-10-13
Ah, no closer to home I'm afraid! So:
1. booted with the Win7 recovery disk and tried diskpart, list disk, which gave:
Disk0    Online    596 GB   free 0B

2. so that wasn't too helpful, so instead I tried, just for fun, chkdsk c: /r, thinking maybe c might for some random reason be the one I want. And it seems it was!? It took a good hour and a half maybe, found no errors and produced the attached log file (which I later found in my 4th partition aka f, so I'm assuming that was the partition it scanned?)
That looks fine doesn't it? Or was /r maybe not the right option?

---

### Post by oldfred on 2010-10-13
I would go back and try testdisk. It also has advanced repairs.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by maja_z on 2010-10-13
I'm getting a bit beyond my depth here!

OK, so I've just spent a few hours with testdisk running through its 'deep search' The results were kind of weird - there were 7 partitions instead of 4 for example. also the sectors were overlapping. And there was a dedicated swap partition, which I've never had. But I tried assigning them logically, so P, *, P, P and L to correspond to 
1(P) the previous windows partition
2(*) the current linux partition
3(P) the swap partition (was afraid to delete it)
4(P) the current 100 Gig ntfs 
5(L) the current 460 Gig ntfs that's been acting up.

Or so I thought! Because as soon as I pressed enter, it said something about the structure being inconsistent or not logical or something and threw be back to the main menu... Thereby loosing the whole deep search! 

OK, so I'm guessing I should have probably worked a bit harder at setting the partitions. Such as adding one at the front maybe. I was also unable to get it to do a "E" label for some reason.. But it's just a pain waiting two hours for it to get through all the sectors! I'll try again tomorrow..

But before I get ahead of myself, should I try repairing the mft for sda5 first? In what order should I be doing this testdisking? Sorry for being so confusing! 

Its just that currently my system is running fine, I just don't have access to the first 40 gig on my disk. Partition 4 (sda5) is absolutely fine. I'm just afraid that this testdisk utility is going to make me delve deeper than I have to by messing up the partitions that are OK and even the system partition. Basically that's just me not understanding what I am doing really!

btw, there's a semi-usefull-looking screenshot icon in gparted. but i can't for the life of me figure out where it thinks it's saving the screenshots?!

---

### Post by mörgæs on 2010-10-13
I know it is annoying when people repeat themselves, but... are you sure that it is worth the effort to try to fix this drive rather than beginning from scratch? 

Of course it takes a little while to install your extra applications and so on after a fresh install of Ubuntu, but in the end isn't it both faster and safer?

---

### Post by maja_z on 2010-10-14
ha mörgæs, nice! I'm not annoyed at all, this was a good time to come back and repeat yourself! don't worry, I'm not forgetting that option, I just haven't reached the critical value of my time-invested/how-badly-do-I-want-to-figure-this-out ratio!

---

