---
title: "Bare metal backup"
date: 2010-02-13
forum: General Help
---

### Post by Manyette on 2010-02-13
Can anyone suggest the correctl place to post to obtain answers on a real bare metal backup facility.  My questions thus far have either been ignored or given less than satisfactory answers. So far I have tried PING, rsync, Clonezilla and tar.  All have one or another problem.  I'm sure that this is in part to my own ignorance and partly due to running the 64 bit version of Karmic,  but I cannot seem to find anyone who has reasl answers.  I'd appreciate any advice offered.

---

### Post by chewearn on 2010-02-14
Those tools you cited work well.  So, the question is what is not working for you?  What requirement is lacking?

---

### Post by nixclusive on 2010-02-14
There are many ways to backup a linux system. Some of the the tools you have listed are used to make *file system* backups. i.e. they do not include the boot loader itself which is not normally visible. If you are comfortable with installing and configuring a boot loader you can use "tar" to make whole snapshots of your filesystem or "rsync" to go for incremental backups.

Your system being 64-bit has nothing to do with your ability to backup and restore.

---

### Post by Manyette on 2010-02-14
> **chewearn said:**
> Those tools you cited work well.  So, the question is what is not working for you?  What requirement is lacking?

Thanks for at least responding.  Hasn't happend prior to this.  Clonezilla, which I thought would be a good answer apparently has a bug with the 64 bit system.  (Karmic).  1-It blobs the screen when asking for the destination.  2-It frequently (and inconsistently) tells me that my disk is full and aborts when I have a 320 gig USB HD with over 270 gigs free space.  It will always do this if there is already one of it's own backups on the USB HD.On occasion it will get one good backup, but I can never get a second, ebven if I delete the prior backup. ????  Yes, I have downloaded it multiple times, and burned more than one cd to hold it, so it is not a program fault in that sense.  I have the feeling that there is some characteristic of the USB HD that is causing this problem, but I have not been able to find it.  The permissions are correct, and the disk has plenty of spare room.  As for some of the others, rsync refuses to backup the .gvfs directory, which I do not understand, since it is as the system installed it, and I have never had any reason to change it, or even enter that directory.  TAR will not (at least for me) restore to bare metal.  The list goes on and on.  As a real newbie to Ubuntu, which I love, and consider one of the best of the current OS's out there, this all pains me, because I feel that any reasonable OS will provide a simple and easy backup procedure.  Right now, all I have is two "DD" copies of the boot and data sectors, plus a TAR backup file, and that is just not a reasonable backup system.  Understand that although before retiring, I was a hardware engineer for 23 years, and a programmer for another 35.  I ams simply totally new to Linux in any form.  I'm sure that most of this is my own ignorance, but when I ask questions, I either get no answer, or an answer that does not work, at least for me.  Apologies for the long post.  I will furnish any answers you desire, but this is already too long.

---

### Post by Manyette on 2010-02-14
> **nixclusive said:**
> There are many ways to backup a linux system. Some of the the tools you have listed are used to make *file system* backups. i.e. they do not include the boot loader itself which is not normally visible. If you are comfortable with installing and configuring a boot loader you can use "tar" to make whole snapshots of your filesystem or "rsync" to go for incremental backups.

Your system being 64-bit has nothing to do with your ability to backup and restore.

My own preferences are to always do "snapshots".  While reinstalling ubuntu is easy, and quick, the customization to the system takes hours, and this to me is just not reasonable.  And yes, Clonezilla does seem to have a problem with and EMT64 system.

---

### Post by howefield on 2010-02-14
> **Manyette said:**
> Can anyone suggest the correctl place to post to obtain answers on a real bare metal backup facility.  My questions thus far have either been ignored or given less than satisfactory answers.

It is difficult to find any of your questions that have not been answered apart from your (single) posting last week about Clonezilla, in which case it is perfectly reasonable to "bump" the post back up once every 24 hours.

Posts can quickly drop down the listings and someone who has the answer may often simply not see it.

> So far I have tried PING, rsync, Clonezilla and tar.  All have one or another problem.  I'm sure that this is in part to my own ignorance and partly due to running the 64 bit version of Karmic,  but I cannot seem to find anyone who has reasl answers.  I'd appreciate any advice offered.

Clonezilla is a quite excellent piece of software, 64 bit or otherwise.

What file systems are you trying to back up ? (and what version of Clonezilla are you trying ?)

---

### Post by Manyette on 2010-02-14
What file systems are you trying to back up ? (and what version of Clonezilla are you trying ?)
howefield is offline Report Post   	Reply With Quote

As I said earlier, I am trying to do a snapshot of the entire system.  For me, the best approach is a snapshot of the entire system.  15 minutes to backup, and another 15 minutes for a restore, if required.  Customization of a new install is hours, and just makes no sense to me.

---

### Post by nixclusive on 2010-02-14
I'm not familiar with Clonezilla, however, you should be able to make a copy of your filesystem using tar. The following command can be used to make a backup:

```
tar -cpf <path-to-backup-file> / --exclude=/proc/* --exclude=/lost+found --exclude=/tmp/* --exclude=/var/tmp/* --exclude=/dev/* --exclude=<path-to-backup-file>
```

using /proc/* instead of just /proc makes sure the contents of the given directory are excluded while the directory's presence itself is noted.

This method does not include your boot loader and the required changes to /etc/fstab when you're restoring your system. You will need to install grub and make relevant changes to the file /etc/fstab to reflect any changes to the destination device's UUIDs. :)

---

### Post by howefield on 2010-02-14
> **Manyette said:**
> What file systems are you trying to back up ? (and what version of Clonezilla are you trying ?)
howefield is offline Report Post   	Reply With Quote

Huh ?

> As I said earlier, I am trying to do a snapshot of the entire system.  For me, the best approach is a snapshot of the entire system.  15 minutes to backup, and another 15 minutes for a restore, if required.  Customization of a new install is hours, and just makes no sense to me.

I agree, Clonezilla for me takes about 7.5 minutes to back up the entire system, bootloader, partitions, the lot. And about half that to restore. 

Now again, what file systems are you trying to back up ? (and what version of Clonezilla are you trying ?)

---

### Post by Manyette on 2010-02-14
> This method does not include your boot loader and the required changes to /etc/fstab when you're restoring your system. You will need to install grub and make relevant changes to the file /etc/fstab to reflect any changes to the destination device's UUIDs. 
That is anexcellent tip about the "proc" directory, however this provedure, which I have used, is neither simple nor easy, which I expect from a backup system.  The restore, if required, should not need so much effort.

---

### Post by Manyette on 2010-02-14
Howefield, Nixclusive, and Chewearn, Please believe me that I am grateful for your replies.  I am NOT trying to be difficult.  Of the many systems I have used over the years, a backup and a restore is one simple command.  I just have trouble believing that such is not available in Linux.  As I said earlier, Clonezilla looked to be the answer to my prayers, one you get used to it's idiosyncrasies.  "Read from or Save to" is not useful to a newbie.  Destination and source would be much more useful terms, to my way of thinking.  If one of you guys are using a Core 2 EMT64 system, I am sure you have seen the fact that it blobs the screen when asking for the destination directory, not to mention the earlier problem I mentioned about getting a disk full message when there is more than enough space on the drive.  I do appreciate all that you have offered, and if that is what is required, well, perhaps that is what I must do, but I do find it disappointing all the same.  And again, I do offer thanks to you all.

---

### Post by nixclusive on 2010-02-14
Perhaps you can take a look at [SystemRescueCd](http://www.sysresccd.org/Main_Page) if Clonezilla isn't working for you for any reason. :)

---

### Post by howefield on 2010-02-14
> **Manyette said:**
> Howefield, Nixclusive, and Chewearn, Please believe me that I am grateful for your replies.

Yes, so much so, you are reluctant to answer a couple of simple questions. I asked twice, I won't ask 3 times.

Good luck, I hope you get what you want.

Your assertions of what Clonezilla can/can't do whilst may be the case for your specific setup/knowledge is simply not the case for other users,  "Core 2 EMT64 system" is simply a red herring that has no bearing here.

---

### Post by Manyette on 2010-02-14
Dear Howefiled, my apoologies, but I was trying to answer 3 folks at once.  Since I do not have the CD loaded, I can only tell you that the version I am using is the latest stable version on the website.  As to what I am trying to back up, you must have missed my first post.  I want a snapshot of the entire system.  And telling me that core 2 is not relevant missed the point that the system literally blobs the screen on the request for the destination drive.  It also misses the point that on a 320 gig USB external derive,m with 270 gigs of free space, it gives me a "disk full" and aborts the backup.  I think this indicates a problem of some sort, especially as I have used it to get a successful backup, but rarely, and most of the time I get the disk full and abort.  Yes, I may be doing something wrong, (probably), but I do not know what that might be.

---

### Post by Manyette on 2010-02-14
> **howefield said:**
> Yes, so much so, you are reluctant to answer a couple of simple questions. I asked twice, I won't ask 3 times.

Good luck, I hope you get what you want.

Your assertions of what Clonezilla can/can't do whilst may be the case for your specific setup/knowledge is simply not the case for other users,  "Core 2 EMT64 system" is simply a red herring that has no bearing here.

Version is 1.2.3.27.  Stupid of me, but I had to reboot to the CD to get it.  should have written it on the CD.

---

### Post by howefield on 2010-02-14
> **Manyette said:**
> Dear Howefiled, my apoologies, but I was trying to answer 3 folks at once.  Since I do not have the CD loaded, I can only tell you that the version I am using is the latest stable version on the website.  As to what I am trying to back up, you must have missed my first post.  I want a snapshot of the entire system.

None of that answers the question(s), the advice I'd give would depend on the file system(s) you were trying to back up/image. For someone with a purported lifetimes experience in hardware and software as yourself, I'm amazed at how difficult it is to explain what file system(s) you are dealing with. ;)

> And telling me that core 2 is not relevant missed the point that the system literally blobs the screen on the request for the destination drive.  It also misses the point that on a 320 gig USB external derive,m with 270 gigs of free space, it gives me a "disk full" and aborts the backup.  I think this indicates a problem of some sort, especially as I have used it to get a successful backup, but rarely, and most of the time I get the disk full and abort.  Yes, I may be doing something wrong, (probably), but I do not know what that might be.

My point is that your issues are not likely to be caused by you running an EMT64 CPU. They are not so unique or special.

Anyway, as I said, Good Luck, I'll bow out and leave you. :p

---

### Post by Manyette on 2010-02-14
Howefield, I'm very sorry I have offended you.  My apologies.  I thought I had answered your questions.  Again, I am sorry, I do know you were trying to help me.  At his point I am just very frustrated.  I still think you have missed some of my posts in this thread, and that's why I thought I had answered them.  If I cannot attribute it to the 64 bit system, and I've alreadyn stated that it was Karmic, I don't know what else you might have wanted to know.  Again, I'm sorry I've offended.

---

### Post by howefield on 2010-02-14
> **Manyette said:**
> Howefield, I'm very sorry I have offended you.  My apologies.

Have no fear on that score, you haven't and couldn't. I only post again here to make that clear. :) 

> I've alreadyn stated that it was Karmic, I don't know what else you might have wanted to know.

Yes, you said that several times, none of which I missed. 

Karmic is the version of Ubuntu that you are running, but that says nothing of the file system that you employ to run it on, nor of any others that may be on your system.

---

### Post by Manyette on 2010-02-14
You are correct, I did NOT understand your question.  Seems plain now.  Backup drive USB ext3.  system is default karmic, ext4.  This particular system is an HP71, another is An Acer 5570Z, 32 bit.  Desktop is a Pentium IV, all are running 9.10 Karmic.  All except the backup drive are ext4.  No dual boot anywhere.  The 32 bit systems do not have the "screen blobbing" problem that the EM64t system does, but fail on "disk full" in all other cases.  If any of that helps.  And whether I could or not, I certainly did not intend to do so.

---

### Post by louieb on 2010-02-14
For a bare metal backup and restore. Nothing beats the the **dd**  command for ease of use.  It will copy off a file, a partiton, or a hdd.   

in its most basic form **dd if=source of=target **

Its fast, its easy, works with any file system and its  unforgiving - has the well eared nickname of data destroyer. Make sure the source and target are really what you want.  

Anyway heres my favorite link.  [Learn the DD command - LinuxQuestions.org]("http://www.linuxquestions.org/questions/showthread.php?t=362506")

---

### Post by Manyette on 2010-02-14
Hk louieb, I am aware of it, and thanks for the pointers.  Liked the "data destroyer" reference.  I'll look at it, but it does seem to have sme disadvangages on a really large drive.  Thanks much.

---

### Post by nixclusive on 2010-02-15
Hello there, I downloaded and tried Clonezilla myself and it seems to work fine for me on an Intel(R) Core(TM)2 Duo CPU E7500 @ 2.93GHz processor (from /proc/cpuinfo). Clonezilla itself is a set of bash/perl scripts to drive other helper programs like partclone, ntfsclone, partimage, dd, etc. (from [Clonezilla download page](http://clonezilla.org/download/sourceforge/)) so I highly doubt the issue with 64 bit computing. However, I do not have experience with hardware so I could be wrong.

Other than that, I prefer "tar" approach for backing up my system because its file system independent and allows me a lot of flexibility when I need to restore it back. Not saying that you should do the same but just an opinion. :)

I'm sure somebody would be able to help you with this sometime soon. Good Luck.

---

### Post by Manyette on 2010-02-15
> **nixclusive said:**
> Hello there, I downloaded and tried Clonezilla myself and it seems to work fine for me on an Intel(R) Core(TM)2 Duo CPU E7500 @ 2.93GHz processor (from /proc/cpuinfo). Clonezilla itself is a set of bash/perl scripts to drive other helper programs like partclone, ntfsclone, partimage, dd, etc. (from [Clonezilla download page](http://clonezilla.org/download/sourceforge/)) so I highly doubt the issue with 64 bit computing. However, I do not have experience with hardware so I could be wrong.

Other than that, I prefer "tar" approach for backing up my system because its file system independent and allows me a lot of flexibility when I need to restore it back. Not saying that you should do the same but just an opinion. :)

I'm sure somebody would be able to help you with this sometime soon. Good Luck.
Hi Nixclusive, I thank you for that, it is useful information.  Since I posted earlier, I have tried a couple of other things.  Snce for me, and I don't know why, when Clonezilla asks for the destination, it blobs the screen, and I have to cancel and start over, and the next pass through it works properly. So instead of beginner mode, I got brave and tried expert mode, with some trepidation, but it turned out to be quite straigtforward, and that worked perfectly.  However I still then ran into the problem of "disk full", when the disk has over 270 gigs free.  I suspect that the problem is that my source disk is formatted as ext4, whereas the backup USB drive is USB ext3.  So I still have a problem, and I have found no way to format the external USB drive as ext4.  Still trying to find out why.  And of course, I still don't know why a processor very similar to mine should not blob the screen on the destination request, while mine does, but that is at best the least of the problems.  But I do thank you for the additional information.  I'll keep trying to find the answer. Thanks again.  I do use tar, but in every case I have to do a reinstall, and then reconfigure all my customizations, although I can recover all my own home files from the tar backup, and that is a pain.

---

### Post by Manyette on 2010-02-15
Hi Nixclusive, could you describe your external drive, and could you put a second backup on that same drive?  If you have the time, it might help.  I know you've alreaedy wasted a lot of time, but a bit more info about the external drive would help.

---

### Post by Manyette on 2010-02-18
Just to put a close to this thread, my error was in trying to backup an ext4 partition, which is not supported by partimiage at this time.  Thanks to all who tried to help.

---

### Post by barinov2000 on 2011-01-03
Anyone aware of Mondo Rescue package? It's pretty amazing what it does. It doeas bare metal backup and does it on a live system, too.
[URL="http://www.mondorescue.org/"]
http://www.mondorescue.org/[/URL]

Good luck!

P.S. Don't use the one in standard repositories. Get the latest binaries from the site and try it.

[IMG]http://www.mondorescue.org/images/screenshots.png[/IMG]

---

### Post by Terry of Astoria on 2011-01-06
I just finished restoring this system from a custom rescue DVD which I created a few minutes ago using Clonezilla Live! I'm so happy I could shout!
It was very easy. I burned the AMD64 stable release, LiveCD version of clonezilla, since I happen to be on that type of system, booted it, and cloned the entire disk at once, including the boot sector, 2 Ext3 partitions, and the Ext4 system partition, to an image which I chose to store on my external drive. By the way, Clonezilla live paused during startup, prompting me with the option to plug in my USB drive as an potential storage unit.
    Apparently Clonezilla can clone partitions as well as entire disks. I haven't tried that yet. I first created the image using Clonezilla Live, and then rebooted Clonezilla and created a recovery DVD iso image from within Clonezilla which I subsequently burned from within Ubuntu. Later I booted from that recovery DVD, started Clonezilla, confirmed the recovery procedure, and voila! The recovery was successful! I am now typing here on the recovered system.

---

