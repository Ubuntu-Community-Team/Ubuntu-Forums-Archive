---
title: "Ubuntu live rescue cd 12.04 ddrescue problem"
date: 2012-08-23
forum: General Help
---

### Post by Lazer9 on 2012-08-23
I have a failing wd Sata green 2tb drive running windows 7 ultimate that has been giving me bad sector problems. I also have a bunch of programs and movies, etc.... Of which I'm trying to salvage. I currently have an rma with wd to have it replaced. 

I have a 3tb wd drive freshly formatted ntfs which am attempting to clone the faulty internal 2tb drive to with no success thus far :(

Having gathered snippets of information here and there, thus far using the Ubuntu live rescue disk 12.04 have managed to get what I thought to be a clone made using a combination of ddrescue commands but turns out when I do get back up and running via the faulty internal drive, discover now I need to start over as the 3tb usb 3 drive is no longer formatted/readable. I have reformatted it and things seem ready to proceed again but now upon booting back to the live rescue cd into the command prompt section in Ubuntu, I first get a scrolling screen of some kind of errors. Then when invoking: sudo lshw -C disk -short I no longer even get the drives to list the /dev/sda ect.... Info but rather jumped back to the $Ubuntu$Ubuntu: prompt. 

I have no clue what I did or am doing wrong. Any tips or ideas on how to proceed? 

Thanks

---

### Post by oldfred on 2012-08-24
Welcome to the forums.

How is 2TB partitioned & how is 3TB partitioned. The 3TB drive has to be gpt to use the full size as MBR(msdos) can only work up to 2TiB.

Then how are you coping data. The creator of gdisk to create gpt partitioned drive said you cannot use dd on gpt partitions as there is internal data that you must not overwrite.

It might be better to use rsync?

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by Lazer9 on 2012-08-24
> **oldfred said:**
> Welcome to the forums.

How is 2TB partitioned & how is 3TB partitioned. The 3TB drive has to be gpt to use the full size as MBR(msdos) can only work up to 2TiB.

Then how are you coping data. The creator of gdisk to create gpt partitioned drive said you cannot use dd on gpt partitions as there is internal data that you must not overwrite.

It might be better to use rsync?

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

Thanks for the reply. I'm at my wits end with this. Currently I'm back to trying my original attempt to first try to correct the bad sectors issue on my internal by running a program called HDD Regenerator from another boot disk. It completed over night but said I needed to reboot and run it again when I woke up this morning so have started that up again. I'm at work now and I know on the screen, the HDD Regenerator says its detecting XXX number of delays and doesn't seem to be moving.

Back to try to answer your questions. The External 3TB Drive is formatted NTFS with only 1 partition as far as I understand. I didn't do anything to re-partition it or anything.

The faulty Internal 2TB Drive, to be honest now, I have no idea if I've mistakenly created another partition on it or if it is still in it's original state of just 1 main partition also. I'm starting to wonder if I screwed something up further in my original attempt with the "Live CD" method running ddrescue and following some off-site link that I had printed out the commands such as:

sudo mkdir /mnt/usb0
sudo mount -t ntfs /dev/sdc /mnt/usb0
sudo ddrescue -r3 -v /dev/sda /dev/sdb /mnt/usb0/somerescue.log

Note: That last line I had to add --force at the end per a message that came up.

I'm so confused at this point and all I'm trying to accomplish is salvage data off the internal so I can restore it once the new replacement drive arrives. I'll check out that link about rsync and see if I can understand enough about that to have success.

Strange thing is, through all this, I was able to boot up last night (at least before my overnight re-visit to HDD Regenerator) into windows 7 via the Internal just fine and see all my data on C: drive but for some reason, whatever I tried with the Ubuntu Live CD ddrescue method via the listed commands, the new External F: drive (3TB) was no longer formatted or populating with anything and Win 7 told me I had to format it again which I did NTFS via "quick format" and have it's 2.72TB entire allocated space freed and ready again.

Any further suggestions or explanations as to what might be going wrong with my attempts are much appreciated. I would love to learn more in this process and especially the usage of Ubuntu in data rescue / data restore operation.

Many Thanks!

---

### Post by oldfred on 2012-08-24
Post these. If the 3TB drive is gpt your ddrescue will not work. Also dd is really intended to copy from same size to same size. Not sure if ddrescue then does not copy the empty space but dd which is the underlying program copies everything including empty space.

Run these and post results in code tags (highlight & click on # in edit panel above message). If new drive is not sdb change to correct drive.
sudo fdisk -lu
sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print

Download gdisk (its in repository) 
sudo apt-get install gdisk

sudo gdisk -l /dev/sdb

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by Royalist on 2012-08-24
I too, have today given up with ddrescue. It seems in my case, that it can only write output to a freshly formatted, unpartitoned target disk despite the -f option. I have reverted to dd. My version was downloaded as an ISO file from Remix, so I now have an  Ubuntu 12.04 live CD with no GUI. My current OS  is Ubuntu 11.10.

Rsync seems to be held in high regard. There is also a question mark in my mind over gddrescue v. ddrescue? I suspect that they are now one and the same.

Best of luck with your problem . Perhaps 3TBs is a step too far yet? :)

---

### Post by Lazer9 on 2012-08-24
> **oldfred said:**
> Post these. If the 3TB drive is gpt your ddrescue will not work. Also dd is really intended to copy from same size to same size. Not sure if ddrescue then does not copy the empty space but dd which is the underlying program copies everything including empty space.

Run these and post results in code tags (highlight & click on # in edit panel above message). If new drive is not sdb change to correct drive.
sudo fdisk -lu
sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print

Download gdisk (its in repository) 
sudo apt-get install gdisk

sudo gdisk -l /dev/sdb

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Thanks for the continued help with this. At work right now and have tickets to the Pirate game tonight so likely won't get to this until tomorrow and I will certainly report back.

Just one quick question regarding the (Download gdisk from repository)
- Is this going to work since I'm using the "Rescue -Live CD" in loading into Ubuntu upon boot via my DVD disk/drive? :o

---

### Post by oldfred on 2012-08-24
On a liveCD you can download anything to try it out, of course it is only in memory and will be lost when you reboot. 

If you have a liveUSB flash drive with persistence then you can save the download, but I think persistence just reinstalls the apps as the LiveCD image on the flash drive is not updated nor updatable.

---

### Post by Lazer9 on 2012-08-25
Here is where things stand. I am currently booted back into Windows7 on the failing drive while actually making this post. Still have yet to succeed on a backup/clone to the external 3TB WD My Book Essential which I need to accomplish as I have the RMA engaged and a replacement 2TB WD BLACK Sata Internal on it's way to replace the failing GREEN.
 
Upon booting up with the Ubuntu Live Rescue CD I now get the following error which scrolls down the screen on the left side while on the "purple" splash screen before bouncing to the command prompt. [COLOR=red][sdb] bad block number requested [/COLOR][COLOR=black](this lists repeatedly with some other series of numbers I believe then finally disappears and I'm given the command prompt after intitial startup - This never happened before I attempted my initial unsuccesful ddrescue command attempts in a prior session and I've tried numerous hard/cold boots, unplugged computer... waited ect... and now always get this error even when simply booting soley off the live CD) :confused:[/COLOR]
 
**sudo fdisk -lu **
 
```
Disk /dev/sda: 2000 GB, 2000396321280 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024065 sectors
Units = sectors of 1 * 512 = 512 bytes
 
Device    Boot    Start    End      Blocks        Id      System
/dev/sda1   *      2048   206847   104391    7       HPFS/NTFS
Warning: Partition 1 does not end on cylinder boundary.
 
/dev/sda2        206848  3907026943   1953415642   7    HPFS/NTFS
Warning: Partition 2 does not end on cylinder boundary.
 
Error: /dev/sdb : unrecognised disk label
Warning: Unable to open /dev/sr0  read-write (Read-only file system). /dev/sr0 has been opened read-only.
Error: /dev/sr0 : unrecognized disk label
```
 
**sudo parted /dev/sda unit s print**
 
```
Model: ATA WDC WD20EARS-22M (scsi)
Disk  /dev/sda: 3907029168s
Sector size (logical/physical) : 512B/4096B
Partition Table: msdos
 
Number    Start       End         Size            Type     FileSystem    Flags
   1          2048s    206847s    204800s      primary   ntfs           boot
   2          2068848s  3907026943s   3906820096s   primary   ntfs
```
 
**sudo parted /dev/sdb unit s print**
 
```
Error: /dev/sdb: unrecognised disk label
```
 
Other notes: As mentioned before, after my intitial attempt at running ddrescue via "live cd" to the then fresh external WD 3TB, upon getting back into Windows7 later, the F: drive which is the external WD 3TB of which I tried to clone to was no longer showing any capacity and I had to do a format back to NTFS in Windows7. It now shows recognised in Windows and as Drive F: with 2.72 Tb free of 2.72 Tb however, I'm no longer even seeing it as it seems via "live cd" bootup ?
 
I have not even attempted to pursue anything with the Download of gdisk as I'm awaiting a reply to this report I posted as to figure out what is going on and my best way to proceed.
 
Oh, and HDDREG continues to eventually complete hours later but always says to re-run it (again this is on the original boot (source drive) internal C: which is the Windows7 drive with the bad sectors that I am trying to clone over to my External).
 
Thanks!

---

### Post by oldfred on 2012-08-25
It still seems like there are partition/format issues on sdb. Still may be related to MBR vs. gpt?

Back to original issue.

Some have posted this as a good way to move Windows, but I do not know if it will reinstall to gpt?

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by Lazer9 on 2012-08-25
Yea I agree. I assume sdb is my new 3TB External drive if I'm following everything correctly here?
 
I am currently trying a "Full" re-format of it via Windows7 at the moment rather than the "Quick" option I last chose. Then I will boot back into "Live CD" and see if it is showing up before I proceed any further.

---

### Post by Lazer9 on 2012-08-25
Here is what I end up with after re-format of the external 3TB WD. Seems the problem is MBR and not GPT. Trying to figure out how to correct that.
 
[IMG]http://i47.tinypic.com/zkocaq.jpg[/IMG]

---

### Post by Lazer9 on 2012-08-25
Update:
 
Ok, I figured out the problem. I had to run the Western Digital Format Utility for the External and make sure I selected the "Defaults" instead of "Xp Compatible" and I have now ended up with this result:
 
[IMG]http://i50.tinypic.com/2mqp3ko.jpg[/IMG]
 
Now I just have to figure out the best way to proceed via the information you last provided vs.s using ddrescue or another cloning tool - maybe Clonezilla Live?
 
And if I should be partitioning the External 3TB with a 2TB partition to match the actual capacity of the faulty internal 2TB?
 
Hrmmm :popcorn:

---

### Post by oldfred on 2012-08-25
With Windows I do not know the issues of converting. But Windows will not boot from a gpt drive unless you have a new system using UEFI. And that would require a reinstall. You can use it for data and Windows 7 will read data in a gpt partitioned drive.

Otherwise you just have to go back to MBR and only have a 2TB drive as long as you want Windows. 

Ubuntu and most Linux will boot from gpt drives with BIOS or UEFI.

---

### Post by Lazer9 on 2012-08-25
> **oldfred said:**
> It still seems like there are partition/format issues on sdb. Still may be related to MBR vs. gpt?
 
Back to original issue.
 
Some have posted this as a good way to move Windows, but I do not know if it will reinstall to gpt?
 
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
 
Driveimage results:
 
Ran for aprox 2 hours, at 65% it found its first **Data Error (cyclic redundancy check) @ 1957292416 (17896 sectors) **This was at the 65% 1hr 36min mark
 
I finally chose **Ignore All **and the copy continued until 91% complete with a final error: **Range check error**
 
**Info: APPEXC:**
**Address: 005D4FB2**
**Stack dump:**
 
Tried reflectfree:
 
It doesn't even see my external drive so can't even continue to try to clone with it.
 
:icon_frown: There has to be a way...

---

### Post by Lazer9 on 2012-08-26
Ok here is where I am at. Back to attempting my backup of the main drive with bad sectors using ddrescue via the boot to Ubuntu Rescue Remix v12-04.

I have partitioned the external drive with a 1.95TB partition to use as the destination which is **sdb3**. The internal drive which I am trying to clone is **sda**.

I issue: sudo ddrescue -r3 -v /dev/sda /dev/sdb3 rescue.log

This returns a msg: output file exists and is not a regular file. Use --force if you really want to overwrite it, but be aware that all existing data in output file will be lost.

So I re-issued prior command with the --force at the end and the operation has begun.

Does this seem correct so far?

---

### Post by oldfred on 2012-08-26
I thought it was partition to partition or drive to drive, but I do not use dd unless I have to as it can be dangerous. I have not used ddrescue.

I prefer to just use rsync with parameters to preserve permissions & ownership.

But are you gpt or MBR? as I still do not think you can dd from MBR to gpt.

---

### Post by Lazer9 on 2012-08-26
> **oldfred said:**
> I thought it was partition to partition or drive to drive, but I do not use dd unless I have to as it can be dangerous. I have not used ddrescue.

I prefer to just use rsync with parameters to preserve permissions & ownership.

But are you gpt or MBR? as I still do not think you can dd from MBR to gpt.

I am pretty sure the faulty 2tb internal (source) drive sda is MBR and I know for certain the external 3tb (destination) drive sdb is GPT which I have created the 1.95 Tb partition identified as sdb3 that I am trying to clone to.

I am confused about rsync. Is this also supposed to have the ability to clone an image of a drive with bad sectors to an external drive partition? And if so, can you direct me to the commands needed to accomplish this based on my current config? I assume rsync is part of the live rescue cd of which I am booting from.

---

### Post by oldfred on 2012-08-26
rsync will not work around the bad sectors, but if the drive is corrupted ddrescue will not copy the corrupted partitions, it will just work around them.

---

### Post by Lazer9 on 2012-08-26
So not sure what that means to my situation. I know there are bad sectors but I am so far, still able to boot into the windows7 drive. It just occasionally hangs and the hard drive stays lit as being accessed for extended periods of time. I just want to clone whats there so I can restore it to the new internal drive that WD is sending me as per the RMA.

---

### Post by oldfred on 2012-08-26
Are you getting a new 2TB drive then? As then you do not have to have the MBR vs. gpt issues.

---

### Post by Lazer9 on 2012-08-26
> **oldfred said:**
> Are you getting a new 2TB drive then? As then you do not have to have the MBR vs. gpt issues.

Yep, they are sending me the WD Black Sata 2TB which is supposed to be more reliable than this failing Green model. Should I be just waiting to attempt a direct clone to it?

---

### Post by oldfred on 2012-08-26
That would probably be easier as then you can go MBR to MBR without issue. The maximum that MBR(msdos) supports is 2TiB.

The 3TB drive needs to be gpt to use the full 3TB, but Windows will only boot from gpt if booting with UEFI.

---

### Post by Lazer9 on 2012-08-26
> **oldfred said:**
> That would probably be easier as then you can go MBR to MBR without issue. The maximum that MBR(msdos) supports is 2TiB.

The 3TB drive needs to be gpt to use the full 3TB, but Windows will only boot from gpt if booting with UEFI.

Ok and thanks. I will probably be trying that method next once the replacement drive arrives.

As it stands now, I am several hours in with my current attempt and just a bit confused as to how/why the process even runs if the MBR to the GPT partition is a no go...

Is this why I had to add --force?

It's currently at 1316 GB rescued / errsize 3096 kb / errors 5 / Copying non-tried blocks...

Current rate: 20381 kbs
Average rate: 53512 kbs

---

### Post by Ceiber Boy on 2012-08-26
Hi, I'm sorry to read that your having so much trouble, I have been in similar situations and can empathise with your predicament.

Hear are a few (hopefully helpful) thoughts:
Use dd to clone your internal hdd to a file on your external hdd, using ubuntu live cd. 
Method:
 Boot ubuntu live cd
 Format external hdd as ext4.
 Now (somthing like) 'sudo dd if=/dev/sda of=/media/external/image.img

 Sit back relax, as 2tb will take a while!

When you new drive arrives:
 Install
 Boot ubuntu live cd
 Again somthing like 'sudo dd if=/media/external/image.img of=/devlsda'
**(look at 'man dd' for exact code!)**

After that bob should be your uncle. If I have missed somthing then I apologise but this should work.

Good luck

---

### Post by Lazer9 on 2012-08-27
> **Ceiber Boy said:**
> Hi, I'm sorry to read that your having so much trouble, I have been in similar situations and can empathise with your predicament.

Hear are a few (hopefully helpful) thoughts:
Use dd to clone your internal hdd to a file on your external hdd, using ubuntu live cd. 
Method:
 Boot ubuntu live cd
 Format external hdd as ext4.
 Now (somthing like) 'sudo dd if=/dev/sda of=/media/external/image.img

 Sit back relax, as 2tb will take a while!

When you new drive arrives:
 Install
 Boot ubuntu live cd
 Again somthing like 'sudo dd if=/media/external/image.img of=/devlsda'
**(look at 'man dd' for exact code!)**

After that bob should be your uncle. If I have missed somthing then I apologise but this should work.

Good luck

Thanks for that suggestion. I'm to the point where I'll try about anything.

What is the difference in dd vs.s ddrescue? Will dd work on a drive with bad sectors?

About the MBR to GPT issue, will dd work in this case when the internal (source) drive is MBR and the external is GPT?

And, assuming the above questions are yes, can I use dd to copy to a partition on the external and if so, what would be the command?

**Here is where things are this morning with ddrescue currently:**

[IMG]http://i47.tinypic.com/244nrrk.jpg[/IMG]

This is where it always hangs up and I end up having to re-format the destination (external) drive and start over...

How many hours should I let it run?

---

### Post by Ceiber Boy on 2012-08-27
Will reply when I get home, can only do so much on a phone.

---

### Post by oldfred on 2012-08-27
I do not think dd or any of the related programs like ddrescue will work on mbr to gpt copies. The issue is the structure of a gpt partition is different.

dd is intended for copy from same size to same size (and type). I think ddrescue adds the retry and skip to attempt to copy drives with issues.

But you may be able to copy to an image file on the gpt drive if space is available.

Full image backup
GNU ddrescue (packaged as gddrescue, though once installed the command is "ddrescue") 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


Do not use dd to copy partition with gpt due to unique guids & UUIDs post #12, copy of entire drive may work.
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)

Post #12 is by the author of gdisk for partitioning gpt drives. He really knows the inner workings of gpt partitioning.

---

### Post by Lazer9 on 2012-08-27
> **oldfred said:**
> ...But you may be able to copy to an image file on the gpt drive if space is available.

Full image backup
GNU ddrescue (packaged as gddrescue, though once installed the command is "ddrescue") 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


Thanks for the clarification regarding **dd**. I won't try that.

About the above (gddrescue), I am totally confused again as I followed that link and the commands seem to refer exactly to what I'm invoking ddrescue already. ](*,)

I don't understand how to install/run it any different that what I'm already doing with the live cd?

---

### Post by oldfred on 2012-08-27
The instructions show several versions. You can use dd to copy a drive, a partition or copy to an image. In your case from mbr to gpt, only the image will work. 
When you get new drive, then you may be able to use the full drive copy.

---

### Post by Lazer9 on 2012-08-27
> **oldfred said:**
> The instructions show several versions. You can use dd to copy a drive, a partition or copy to an image. In your case from mbr to gpt, only the image will work. 
When you get new drive, then you may be able to use the full drive copy.

Ok so basically I want to do the mentioned  [gddrescue]("apt:gddrescue") method via that link as an image copy:

**So, if /dev/sda is unreadable, you will need to  acquire another disk  (or other media) onto which to save the output  image.  You will need to  have more room on the new media than on the  failed disk. **

```


sudo ddrescue -r 3 /dev/sda /media/usbdrive/image /media/usbdrive/logfileRun successive passes like this: 

sudo ddrescue -r 3 -C /dev/sda /media/usbdrive/image /media/usbdrive/logfile
```Instead of what I've been doing with the ddrescue in trying to clone via:

```
sudo ddrescue -r3 -v /dev/sda /dev/sdb3 rescue.log --force
```So question:

How does this part get pointed to copy to sdb3 (the partition of the external drive)?:

```
/media/usbdrive/image /media/usbdrive/logfile 
```

---

### Post by oldfred on 2012-08-27
You are copying an entire drive to a partition with dd, so it does not match whether MBR to MBR or mbr to gpt.

The example with /media/usbdrive/image assumes you have temporarily mounted a usb drive (named usbdrive)  in media. yours should be something like /dev/sdb3/image.

Or:

sudo ddrescue -r 3 -C /dev/sda /dev/sdb3/image /dev/sdb3/logfile

When done you should have two files in sdb3, image & logfile. Make sure you have 2GB as it will copy entire drive to image. (part of reason I do not like very large partitions, easier to have smaller partitions and separately copy them.).

---

### Post by Lazer9 on 2012-08-27
> **oldfred said:**
> You are copying an entire drive to a partition with dd, so it does not match whether MBR to MBR or mbr to gpt.

The example with /media/usbdrive/image assumes you have temporarily mounted a usb drive (named usbdrive)  in media. yours should be something like /dev/sdb3/image.

Or:

sudo ddrescue -r 3 -C /dev/sda /dev/sdb3/image /dev/sdb3/logfile

When done you should have two files in sdb3, image & logfile. Make sure you have 2GB as it will copy entire drive to image. (part of reason I do not like very large partitions, easier to have smaller partitions and separately copy them.).

Ok I think I am starting to understand.

What would be the command to mount the external usb drive partition assuming it is sdb3?

---

### Post by oldfred on 2012-08-27
It depends on how you mount it. I always label partitions and then they mount under the label. You can add labels with gparted or Disk Utility. If not labels it may mount by UUID or size?

I mount fixed disks with fstab, but label partitions otherwise both so I can remember what they are and to make it easy to temporary mount with Nautilus.

I do not think dd or ddrescue is normally the best way to copy data and with a huge 2TB partition it may take all night or more. But if your drive has issues it may be the only way. I prefer rsync for backups and my most important data I copy to DVDs regularly.

---

### Post by Lazer9 on 2012-08-27
Ok maybe I'm over thinking this but say I issue:
```
[CODE]sudo lshw -C Disk -short
```[/CODE]

And the drive(s) list in the subsequent report, sda, sdb, ect....

Does this mean they're mounted? Or does the partition for the destination of the image or clone still need mounted somehow first?

I found this sort of command somewhere amongst my feverish googling:

```
[CODE]mkdir /mnt/usbdrive
mount /dev/sdb3/ /mnt/usbdrive
```[/CODE

Would this be what I need?

Sorry for all the questions. I'm trying very hard to learn. [-o<

---

### Post by oldfred on 2012-08-27
Since you can name a mount point anything you want that works.

To see what you have mounted

mount

Your lshw only shows drives, not partitions nor mounts.

---

### Post by Lazer9 on 2012-08-28
I am still trying to absorb all the information given to me in this thread and very much appreciate it. 

Thought I would post an update (screenshot) on where things stand on my current ddrescue attempt that I started a couple days ago and where it is at in comparison to my last screen shot and ask if anything stands out? Should I let this process continue to run OR stop it and go the (image) route and/or just wait for the WD 2TB Internal drive replacement and then try to ddrescue straight to it being it will presumably be MBR to MBR?

[IMG]http://i50.tinypic.com/302c7eb.jpg[/IMG]

---

### Post by oldfred on 2012-08-28
I cannot tell, but I do not know ddrescue. It looks like the old one in that you are copying sda to sdb3 not to an image file?

---

### Post by Lazer9 on 2012-08-28
> **oldfred said:**
> I cannot tell, but I do not know ddrescue. It looks like the old one in that you are copying sda to sdb3 not to an image file?

Yea that is correct. I know you have pointed out where going MBR to GPT partition was likely not possible since I had re-visited another run with it. I have let it go on during the  preceding discussions just for shits and giggles... :lolflag:

It seems to still be working on things. In the past, I would end up ending the process about here and end up with nothing and having to boot back into windows and reformat that partition of the USB external drive (source) as it was no longer recognized. I'm simply wondering if I let this thing go for a while longer, if it would have a chance at actually completing and giving me the cloned copy OR is this deemed not possible due to the MBR to GPT condition and am I just wasting my time letting it run.

---

### Post by oldfred on 2012-08-28
I do not know details, not even sure a drive to partition with just MBR would even work as a drive is different than a partition. DD is a very low level tool that is very powerful but with that power it then can be very dangerous.

Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by Lazer9 on 2012-08-28
> **oldfred said:**
> I do not know details, not even sure a drive to partition with just MBR would even work as a drive is different than a partition. DD is a very low level tool that is very powerful but with that power it then can be very dangerous.

Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Is dd and ddrescue one in the same then regarding being very dangerous & low level?

Maybe I am already somehow doing more harm than good. :shock:

I would love to use the rsync but a couple of problems.

1) I don't even begin to understand it and how to use it.

2) I don't think it is meant for copying from a "bad sector" disk as is my case OR maybe I am wrong on that presumption?

---

### Post by oldfred on 2012-08-28
ddrescue as I understand it is dd with additions to try to reprocess or skip bad sectors.

rsync is good for backup if you want file by file copy. Not sure what it does with corruption. 

I prefer to separate system from data and just reinstall system and backup data only.

discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by Lazer9 on 2012-08-29
As expected, the recent clone attempt with ddrescue ended up finally completed and apparently failed as once I do get rebooted back into windows, the (G) drive which is the aprox 2TB GPT partition of the external is unreadable and needed reformated.

I am also getting a {SMART} error upon booting up which directs me to the bios then I have to hit "Advanced" and exit without saving and the drive boots up fine into windows.

So I suspect I am doing continued damage by trying to run ddrescue, ect... to the bad sectors and am soon going to be **** out of luck.

My replacement (RMA) WD 2TB Black internal SATA replacement drive has yet to arrive. I expect it any day.

I would like to proceed one last effort before hand and attempt to create an "image" of the failing drive to the partitioned 2TB space on the 3TB External. At this point I am rather confused on how to go about this regarding the commands / mounting / ect...

Can someone  please give me a straightforward command structure on how to accomplish/try this one last method? Again, my internal (failing) drive is identified as /dev/sda and the external partition is /dev/sdb3

Please refer to my previous screenshots in this thread if you need more exact info as to my setup.

Many thanks!

Ron

---

### Post by oldfred on 2012-08-29
I have not used ddrescue but did you use the command I posted in #31? The extra /image should then save as a file not overwrite the partition.

---

### Post by Lazer9 on 2012-08-29
> **oldfred said:**
> I have not used ddrescue but did you use the command I posted in #31? The extra /image should then save as a file not overwrite the partition.

Thanks for that reference. Admittedly I've been getting lost in the whole discussion while fighting down other links and such. Will give that a try later once home! :D

---

### Post by Lazer9 on 2012-08-29
Ok, game changer. The replacement drive has arrived. So now I have equal 2tb to 2tb internals. Best way to proceed with a direct clone of bad sectors drive to new one?

---

### Post by oldfred on 2012-08-29
I would think so. 

But if whatever is bad is important then new drive will not work.

---

### Post by Lazer9 on 2012-08-29
> **oldfred said:**
> I would think so. 

But if whatever is bad is important then new drive will not work.

So would:
```
ddrescue -r 10 -v /dev/faulty_drive /dev/newdrive optional_logfile.log
```

Be the appropriate command replacing faulty_drive and newdrive with respective sd*x* values?

---

### Post by oldfred on 2012-08-29
I would think so, but I do not have ddrescue installed, so I do not know which parameters are most important. It looks like you have 10 retries?

This may take a very long time.

---

### Post by Lazer9 on 2012-08-29
> **oldfred said:**
> I would think so, but I do not have ddrescue installed, so I do not know which parameters are most important. It looks like you have 10 retries?

This may take a very long time.
Yea I wasn't sure of the 10. It was mentioned to me from another site: [http://superuser.com/questions/467591/best-way-to-clone-a-2tb-wd-green-internal-drive-with-bad-sectors-to-a-3tb-partit/468020#468020](http://superuser.com/questions/467591/best-way-to-clone-a-2tb-wd-green-internal-drive-with-bad-sectors-to-a-3tb-partit/468020#468020)
:-\"

---

### Post by Lazer9 on 2012-09-01
Well I'm nearly 36hrs in and this is where I'm at:

[IMG]http://i47.tinypic.com/scw9yp.jpg[/IMG]

---

### Post by oldfred on 2012-09-01
You did not change block size again, default 128 sectors makes it very slow.

---

### Post by Lazer9 on 2012-09-02
> **oldfred said:**
> You did not change block size again, default 128 sectors makes it very slow.
Lol and crap. how do I do that and is it worth canceling the current attempt and restarting it with a different block size?
:(

---

### Post by oldfred on 2012-09-02
I doubt if it is worth changing. With 2TB it is going to take a very long time either way.

Full image backup
GNU ddrescue (packaged as gddrescue, though once installed the command is "ddrescue") 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Some where I had found these suggestions:
> When using ddrescue on a drive that has significant damage, the following options are suggested:
   1. -r 2 (maximum 2 retries, otherwise it takes too long)
   2. -d (Don't let the OS try and access the drive, it can add too much time to any bad block retries)
   3. -c 8 (The 128 sector default can complicate and slow things)
   4. -v (The more info the better)
   5. -n (If the disk is really bad, this won't waste as much time on the unreadable blocks)
sudo ddrescue -r 2 -d -c 8 -v -n infile outfile [logfile]


see
man ddrescue
and
info ddrescue

---

### Post by Lazer9 on 2012-09-02
Appreciate the help and suggestions. It is currently on: 
**Retry 4[sda] Add. Sense: Unrecovered read error - auto reallocate failed**

I assume this means I am at pass 4 of the 10 from my original command line?

Fingers crossed. If this doesn't produce anything after x more days, I'll try your last posted method. I have about 24 days left until the old drive is due back to WD.

Comment: Why do I keep having to add that --force to the end of my command when initiating? Doesn't this mess things up if I chose to actually use the logfile and it requires this upon the next session command? (It says "but be aware that all existing data in output file will be lost.) This I don't understand. Is this my failure to mount or unmount the device first and if so, I still havn't figured out that part. (sigh)

---

### Post by Lazer9 on 2012-09-04
The process is up to **Retry 8[sda]Sense: Unrecovered read error - auto reallocate failed** 

Am I even going to expect to end up with anything after all this? Beings the old [sda] drive does/did still boot and function in windows7?

Edit: Process has been now running 84 hours +

---

