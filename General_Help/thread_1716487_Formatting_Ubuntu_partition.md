---
title: "Formatting Ubuntu partition"
date: 2011-03-28
forum: General Help
---

### Post by tcdevotie on 2011-03-28
Hi,

I recently installed Ubuntu on a partition on my HP mini, but did so without being connected to the internet to get the updates needed etc.  Needless to say I am now going to format the partition and then reinstall Ubuntu while connected to the internet to solve my problems.

However, I am new to this and want to make sure I'm doing this correctly.  I downloaded Paragon Partition manager - free edition to format the partition.

Now, it simply gives me the option to format the partition where I have linux.  Is this going to be safe to do and all that?  I'm a bit unsure.

---

### Post by garvinrick4 on 2011-03-28
Can you boot into linux you installed from CD? If so do not need to reinstall just need to open repositorys and update and upgrade. Let me know.

---

### Post by An Sanct on 2011-03-28
Updates and upgrades are *optionally* available while you install. They are also available after installation, so it is okay (and fast) to install first and update later.

---

### Post by tcdevotie on 2011-03-28
Sorry, should have included that information.  

No, I booted from a USB because the HP mini I have doesn't have a disk tray.  I'm having issues with the internet connection.  I made a post about it in the networking section and the recommendation was to reinstall Ubuntu with the ethernet cord attached and working so that I can install updates as Ubuntu is being installed.  I didn't do this previously.

---

### Post by ajgreeny on 2011-03-28
It will still be faster to install with no connection, then use a cable ethernet if needed, to do all the updates more quickly.  It is the way I generally do things as it means less waiting around when the install is going on, and you can quickly see if there are any other problems that may need sorting, before doing all the updates.

Don't bother to reinstall, just attach the ethernet cord and update now!

---

### Post by tcdevotie on 2011-03-28
That's my main issue that, again I didn't seem to include.  Here's the link of what I posted a few days ago about it. 

[http://ubuntuforums.org/showthread.php?t=1714451](http://ubuntuforums.org/showthread.php?t=1714451)

I plug in the cable, it recognizes the connection but I can't go online with firefox and when I go to additional drivers it says there's an issue with the connection.  Wireless and wired are enabled.

---

### Post by An Sanct on 2011-03-29
You don't need an optical drive, to install Ubuntu. Installation can also be done from a "Live USB", which is created from the downloaded ISO ([general instructions from www.ubuntu.com, number **2**]("http://www.ubuntu.com/desktop/get-ubuntu/download")).

From what I could see in the other thread, your problem lies in the IP configuration. Have you checked the configuration is according to you ISP/router?

---

### Post by tcdevotie on 2011-03-29
I did install from a Live USB.  The internet connection could be the issue but I did try to set it up manually which did not seem to help as no drivers were available still and firefox still would not load a page.  

Right now I have the paragon partition manager free edition to delete the Linux partition so that I can reinstall it with the ethernet attached which should solve the connection issue.

However, I need to know if it's going to be ok to simply format the partition with the paragon manager?

Will this be a faster solution or are there other suggestions?

---

### Post by oldfred on 2011-03-29
But if just reinstalling you do not have to repartition unless you want  to change partitions and even then you can do it as part of the install.  Use manual install and choose the same partitions you now have.  Reformatting the partition is part of the install. You have to choose which partition is / (root), and what format. If you have a separate /home you choose it and normally not to reformat to save your data.

I think you got side tracked on the issue with wireless that is difficult to resolve without a wired connection. But if you have a Ethernet hard wired connection you should be able to update and fix your current install.

If you want to repartition, I would not use Paragon but you can just use the liveCD (USB) you have. gparted is in System, Administration on the liveCD.

---

### Post by tcdevotie on 2011-03-29
Ok, that sounds great if it will simply replace the Ubuntu I have already installed.  The main reason I want to reinstall with the connection up and running is because it seems like it will make my issue with the internet much easier to resolve with me being so new so as I do not mess something important up or make things more difficult.

I'll try it out in a few hrs or so and post back the results.  Thanks

---

### Post by tcdevotie on 2011-03-29
Ok, some really bad news.  I went to install it again with the USB drive, worked well, but when it got to the point where I got the slider to choose how much space I wanted to give it I had an option of choosing entire partition......I did not choose the entire hard drive and when I clicked entire partition it did not tell me it was installing ubuntu on the entire hard drive......it seems that is what has happened and I've now lost everything  that I had on windows.  I'm sick to my stomach...


I'm pretty sure this is a lost cause and probably ruined everything, but is there any way to recover what was lost and undo this?

---

### Post by earthmeLon on 2011-03-29
I normally boot a system with a gparted or Ubuntu livecd. If you chose to use the Ubuntu livecd, you can go to System>Administration>Gparted to partition your system.


Gparted will allow you to pick which drive you are partitioning (in the upper right hand corner).  Be very careful and make sure you are indeed on the correct hdd.

Typically, you will want to have at least two partitions:
  The first is a 'swap' partition.  People recommend different sizes, but normally you want to mirror your RAM.  If you have 4GB RAM, you want 4GB swap.   Swap acts as memory, like RAM, but is saved onto your HDD.  This is helpful for times when your computer needs more than the available amount of physical RAM.
  The second will be your linux partition.  You can look into which filesystem to use, but most likely you will find that ext3/ext4 will suit your needs.

When you go to install Ubuntu, tell it you want to use advanced/custom partitioning and tell it your swap partition is swap, and your other partition is whichever type and tell it to mount at '/'.


I personally take it a little bit further and have a '/boot' partition and a '/home/' partition.

What this means is that my '/' (root) mount and my '/home' mount are on two partitions.  They are actually on two separate hdds.

This way, I can provide more space for /home/, as that is where most of my applications/downloads reside.  It also helps when upgrading, by keeping my personal data separated.

I hope this wasn't confusing, but helpful.

**I would recommend at least creating a swap partition in addition to your main partition.**



Edit:
> when I clicked entire partition it did not tell me it was installing ubuntu on the entire hard drive   O_o

---

### Post by tcdevotie on 2011-03-29
I'm sorry, but that wasn't helpful because it didn't pertain to what my post was about, not trying to be rude, but what I explained happened was the Ubuntu installation didn't tell me it was going to use the entire hard disk for Ubuntu when I only wanted to replace an earlier installed version of Ubuntu that I gave 32 gig of partition space.  I have lost my window OS that was my primary and all memory. 

I am asking if there's a way to reverse what I've done.  I doubt there is but I really hope so.

---

### Post by earthmeLon on 2011-03-29
> **tcdevotie said:**
> 

However, I am new to this and want to make sure I'm doing this correctly.  I downloaded Paragon Partition manager - free edition to format the partition.

Now, it simply gives me the option to format the partition where I have linux.  Is this going to be safe to do and all that?  I'm a bit unsure.

My response was being drafted before you ruined your partition.  I think it may have been helpful prior to your 'bad news'.

In the future, make sure you always TELL the installation how you want it to be partitioned (advanced), ESPECIALLY if you have critical data on the machine.

Sorry if you feel it was off-topic.  I hope that you are able to find a solution to your problem :D

---

### Post by oldfred on 2011-03-29
You will not be able to recover your windows install as part of it was over written. IF you want to recover anything do not use drive.

 If you have data that you did not back up you can use photorec to recover data files as it just scans drive looking for file signatures. It takes a very long time depending on size of drive and you have to have another drive with lots of room to copy data to.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)


I thought you were going to use manual install which avoids the known bug in instructions that just bit you.

---

### Post by tcdevotie on 2011-03-29
I tried but it wouldn't work that way for some reason.  This has upset me a lot.  Thank you for your help though.

---

### Post by oldfred on 2011-03-29
Do you have a good back up of your system. Or at least your data and the recovery DVD's from your system? 

If not you may be able to get a set of recovery DVD's from your system vendor. Some charge for them.

Some users just convert to Ubuntu as they are not that invested into windows. Others have to have Windows for certain applications.

---

### Post by earthmeLon on 2011-03-29
I've been able to get official Windows ISOs from MSDN/Microsoft.  [MyDigitalLife]("http://mydigitallife.info") also provides a mirror of these ISOs.

If you chose not to buy the 'recovery' disks which contain bloatware, make sure you check the ISOs hash value vs [Microsoft's Website]("http://technet.microsoft.com/en-us/subscriptions/downloads/default.aspx?PV=36:350:DVD:en:all") to ensure it's official, legitimate, and hasn't been tampered with.

---

### Post by Hakunka-Matata on 2011-03-30
Is this off topic?  I don't care, cos I've been working for two days attempting to get dban disc wiper to clean a dying Seagate 250GB 7200RMP SATA NEW HDD I bought from Tiger DIrect last month.  Finally I discovered ```
[COLOR=Magenta]_**SHRED**_[/COLOR]
``` ABOUT TIME.  

I'm tagging this msg with Shred, Wipe, write zeros,

---

### Post by tcdevotie on 2011-03-30
The HP mini's do not come with back up CDs as they do not have disk drives so I didn't have a back up of that kind.  My biggest issue is that I didn't have the money for an external hard drive to back everything up so it's lost unless the above suggestion for recovering it will work.   It's partly my fault and the fault of the program being misleading in that it didn't tell me it was taking up the entire hard drive.  I'll just have to make do with what I have now and try and install windows again in the future and see if the preset buttons like mute and all that on the keyboard will work for it.

Thanks for your help.

---

### Post by oldfred on 2011-03-30
Sorry that happened. If I thought you were going to do something other than manual install, I would have posted kansasnoobs notes, see below.

There is a bug filed, but since it is just confusing instructions, the designers did not want to accept it as a bug. The will not fix current versions, but Natty is much improved.

You could add to the bug, but I do not know if it does anything now.

Kansasnoob filed the bug.

Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

---

### Post by tcdevotie on 2011-03-30
I appreciate it, hopefully I'll be able to get most of the files deleted.  I do not know how it's going to work getting the files back but if I get them back my road will be that much easier.

---

### Post by Hakunka-Matata on 2011-03-31
> **oldfred said:**
> Sorry that happened. If I thought you were going to do something other than manual install, I would have posted kansasnoobs notes, see below.

There is a bug filed, but since it is just confusing instructions, the designers did not want to accept it as a bug. The will not fix current versions, but _**[COLOR=Red]Natty is much improved.[/COLOR]**_

You could add to the bug, but I do not know if it does anything now.

Kansasnoob filed the bug.

Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

to OP & oldfred:  in Natty-amd64 Desktop installer at least (and probably all the other iterations) as of ~17 March 2,011 the partitioner works as advertised.  I used the manual install to a pre-existing partition and it worked slick as a whistle, but had been failing invariably with error (141?) prior to that. The daily build that night fixed that problem and I installed several versions the next day without problems.  And I might add, **natty is working super swell** at this time (31 March, 2011).  Is that par for the course on an Alpha3 release?

---

