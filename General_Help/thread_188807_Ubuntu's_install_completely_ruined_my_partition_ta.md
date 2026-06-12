---
title: "Ubuntu's install completely ruined my partition tables..."
date: 2006-06-04
forum: General Help
---

### Post by just2cool on 2006-06-04
Hey everyone. I'm mostly a Windows user, but I mess around in Linux sometimes (I have a Gentoo install on one of my PC's). Once I saw U6.06 with compiz&xgl, I knew I had to give it a try. So, I downloaded the desktop ISO and booted it off of my work laptop.

I played around with Ubuntu a little bit. I noticed that it had all of my hardware detected and functioning properly. That is, except my hard drive. I tried to mount it and it said something like "Unable to mount hda2". When I clicked more details, it said something like "hda2 is not removable, unable to start pmount". I didn’t really know what this exactly meant, except that it couldn’t mount my drive. I tried to reboot several times but I always received this same message.

Despite that, I ran the install anyway, hoping that it was just a glitch. I tried to let Ubuntu take care of the partitioning automatically, but after a few minutes of it trying, it said "Couldn't make enough space for installation" or something. I then proceeded to manually edit my partition tables. I could see my two NTFS partitions and I resized one of them to leave about 30GB for ubuntu. I created some ext3 partitions in the unallocated space, and hit next. 

I thought it was all ok now because it showed my partition information correctly and it was accessing my hard drive a lot. However, the next screen, where the partition assignment is, showed that the two new partitions I created were 0kb in size, and wouldn't let me assign root or swap to either of them. At this point, I knew there was a chance of my entire drive being completely messed up.

My thoughts were indeed correct. I took out the CD and rebooted with my fingers crossed, but naturally I received the dreaded "Error loading operating system." message. At this point, I only had about 50% battery life left and I never bring home my power pack from work. I needed to have a Windows environment for work on Monday, so I had two options: 1. Give up by repartitioning, reformatting, and reinstalling XP or 2. Put in one of my boot cd's with recovery tools on it. I decided on the latter.

On this boot CD, I first tried Active Partition Recovery. It showed 4 logical partitions as A: which were identified as FAT12. I looked at the headers and they were all completely messed up. It found one partition, which stores the Sony recovery information, but it could not find my main windows partition.

30% battery left. I tried running Partition Magic and it just identified the entire drive as "BAD PARTITION" and I couldn’t find any recovery options inside of the program.

25% battery left. I tried booting from an XP CD and went into the recovery console. I tried a “dir” on C: and it said “An error occurred during directory enumeration”. I then tried a chkdsk, only to see “This drive has one or more unrecoverable problems”. Well, thanks a lot Bill Gates.

20% battery left. I ran another partition recovery utility, which scanned my entire disk. Unfortunately, it got stuck about 75% of the way through, probably where the ext3 partition was supposed to be located.

10% battery left. I quickly ran the last partition recovery utility I had, which is called Disk Patch. I told it which drive to scan, and then shut my screen to conserve as much battery life as possible. Once my hard drive indicator turned off (about 20min later) I opened up my screen and it displayed 6 different partitions, which was incorrect. However, I selected the 2 NTFS partitions that were in "Fair" condition and hit repair. I then set my main windows partition to be active, took out my boot CD, and rebooted.

I was now at 4% battery left. To my amazement, after that flashy Sony BIOS loader went away, I was greeted with the Windows XP boot screen. I did not receive any blue screens during the bootup and I successfully logged into my desktop. It then automatically hibernated since my battery didn't have much juice left.



Now, I obviously can't log back into Ubuntu to see if I get the same error message when mounting my hard drive. But, has anyone else had a similar problem as above? I have heard from so many linux guru's that linux can handle NTFS reading and partition management just fine – and I trusted their opinion. My intuition said to not continue with the install based on the errors I was receiving, but instead I had the “NTFS partitioning is safe” mentality. Well, based on my unpleasant experience, I disagree. I think once I get my power pack I'll manually resize my NTFS partition within Windows and try the install again.

Anyway, thanks for listening to my rant. And if there's someone reading this who is experiencing a similar problem with partitioning, DO NOT CONTINUE.

---

### Post by turbojugend_gr on 2006-06-04
Well my friend, I have to congratulate you on your persistance. Well I am preety handy when it comes to installing OSes and managing partitions and filesystems, well I have to say you pulled something weird over there.

First the message you got while on live cd, was because you didn't give the correct options and mount location. If you wish to mount a drive while in Live CD environment you should edit the /etc/fstab file as root and add a line similar to this:
```
 /dev/sdb1       /winxp          ntfs    defaults,umask=002   0     1
```

then you should type in a terminal :```
sudo umount -a
sudo mount -a
```

As for the problems you encountered, it seems to me you have done a serious mistake while partitioning, I 've never had a problem while resizing, partioning with a linux installer for ages, (including distro's like Suse, fedora, debian) I can't believe you got into this mess like that! Anyway I can't be sure there's always a possibility of sth going wrong...

I hope I was helpful.

---

### Post by just2cool on 2006-06-04
Yeah, I know. I partitioned NTFS file systems without problems in Linux before. 

But I know for a fact that it was not user error this time. I triple checked everything before I hit next. All I did was resize my big NTFS partition by 30GB and created a few ext3 partitions on that new unallocates space. I don't know why those 2 new ext3 partitions were showing as 0kb, either.

But I have another question for you. As I said, the automatic partitioner failed as well. Do I have to manually set aside an unallocated partition or is that supposed to handle that automatically as well?

As for the mount thing - I thought Ubuntu was like Knoppix in that it would automatically know how to mount file systems. I guess not. I'll try that in the terminal when I get the chance.


Thanks.

---

### Post by mannheim on 2006-06-04
You aren't the only one who has had problems when resizing NTFS partitions with the ubuntu installer. There's a confirmed bug report on a similar-looking issue [here]("https://launchpad.net/distros/ubuntu/+source/parted/+bug/32529"), and other reports of problems in these forums.

---

### Post by just2cool on 2006-06-05
I manually resized my NTFS partition with pmagic and was able to create 2 new ext3 partitions within the ubuntu installer without trouble. Everything is running great - including compiz.

But I now know what it probably was. I never shutdown my Windows install completely, rather, I hibernate it. I was under the impression that hibernating just throws a file on the root and that was it. However, it has to do something different - for instance, does it change a bit in the partition header so windows knows to load the hibernate file? Before I initially started the install, I thought I did a complete shutdown but when I was able to get windows back up and running, it resumed from hibernation. And when I used pgmagic, it told me that Windows was in a hibernated state so I'd have to shutdown properly before partitioning. It would be nice if ubuntu did the same thing, but I guess I'm just retarded.

So, in a nutshell, NEVER RESIZE AN NTFS PARTITION IN A HIBERNATED STATE! :)

---

### Post by denjin on 2006-06-05
I don't know why they didn't use a new version of gparted anyway.  They are using a very old one.

I had one friend have it hose his NTFS drive somehow during the install as well when he resized.  Well, XP wouldn't boot any more but he could at least get to his data in Linux.  In his case it was due to some Thinkpad tools partition not being seen properly during the install I think.

It worked just fine for me anyway.

---

### Post by galileon on 2007-02-03
VERY SIMILAR STORY HERE

but the other way around:)

I had Ubuntu Edgy on my tablet pc for a week, but i had left a 10gig partition at the begining of my drive to install xp if i so wanted later.

now yesterday i decided to give xp tablet ed a try, and installed it.

it saw my ext3 partitions as unknown, which wasn't too bad.

but i have a 40 gig hdd, with partitioned into:

primary - 10gig
extended - 30gig
in the extended, i had:
5gig /
2gig swap
22gig /home

now windoze xp told me i had the following partition table:
10gig unknown
30gig unknown
5gig unknown
2gig unknown
22gig unknown

amazing isn't it? windoze saw 69 gig in a 40 gig hdd!!!!!

that's not all:

i tried to install it in the 10gb partition anyway. i forgot about the Boot Record Trojan that ships with every copy of windoze: it completely wiped out my GRUB and i couldn't boot Ubuntu again.

now i tried to use a live cd to restore my grub. and i found that windoze had not only messed up my boot record, but my partition table was hosed as well. 

not wanting to spend ages trying to recover from what damage windoze had done, i decided to nuke the partition table and start over. 

i installed windoze first, then installed my ubuntu work horse.

but i wasted about 5 hours (mostly for the two times installing xp, but also for configuring my tablet for normal use in linux - nvidia drivers, screen and wacom rotation, plus installing stuff through automatix...)  which could have been better used...






> **just2cool said:**
> Hey everyone. I'm mostly a Windows user, but I mess around in Linux sometimes (I have a Gentoo install on one of my PC's). Once I saw U6.06 with compiz&xgl, I knew I had to give it a try. So, I downloaded the desktop ISO and booted it off of my work laptop.

I played around with Ubuntu a little bit. I noticed that it had all of my hardware detected and functioning properly. That is, except my hard drive. I tried to mount it and it said something like "Unable to mount hda2". When I clicked more details, it said something like "hda2 is not removable, unable to start pmount". I didn’t really know what this exactly meant, except that it couldn’t mount my drive. I tried to reboot several times but I always received this same message.

Despite that, I ran the install anyway, hoping that it was just a glitch. I tried to let Ubuntu take care of the partitioning automatically, but after a few minutes of it trying, it said "Couldn't make enough space for installation" or something. I then proceeded to manually edit my partition tables. I could see my two NTFS partitions and I resized one of them to leave about 30GB for ubuntu. I created some ext3 partitions in the unallocated space, and hit next. 

I thought it was all ok now because it showed my partition information correctly and it was accessing my hard drive a lot. However, the next screen, where the partition assignment is, showed that the two new partitions I created were 0kb in size, and wouldn't let me assign root or swap to either of them. At this point, I knew there was a chance of my entire drive being completely messed up.

My thoughts were indeed correct. I took out the CD and rebooted with my fingers crossed, but naturally I received the dreaded "Error loading operating system." message. At this point, I only had about 50% battery life left and I never bring home my power pack from work. I needed to have a Windows environment for work on Monday, so I had two options: 1. Give up by repartitioning, reformatting, and reinstalling XP or 2. Put in one of my boot cd's with recovery tools on it. I decided on the latter.

On this boot CD, I first tried Active Partition Recovery. It showed 4 logical partitions as A: which were identified as FAT12. I looked at the headers and they were all completely messed up. It found one partition, which stores the Sony recovery information, but it could not find my main windows partition.

30% battery left. I tried running Partition Magic and it just identified the entire drive as "BAD PARTITION" and I couldn’t find any recovery options inside of the program.

25% battery left. I tried booting from an XP CD and went into the recovery console. I tried a “dir” on C: and it said “An error occurred during directory enumeration”. I then tried a chkdsk, only to see “This drive has one or more unrecoverable problems”. Well, thanks a lot Bill Gates.

20% battery left. I ran another partition recovery utility, which scanned my entire disk. Unfortunately, it got stuck about 75% of the way through, probably where the ext3 partition was supposed to be located.

10% battery left. I quickly ran the last partition recovery utility I had, which is called Disk Patch. I told it which drive to scan, and then shut my screen to conserve as much battery life as possible. Once my hard drive indicator turned off (about 20min later) I opened up my screen and it displayed 6 different partitions, which was incorrect. However, I selected the 2 NTFS partitions that were in "Fair" condition and hit repair. I then set my main windows partition to be active, took out my boot CD, and rebooted.

I was now at 4% battery left. To my amazement, after that flashy Sony BIOS loader went away, I was greeted with the Windows XP boot screen. I did not receive any blue screens during the bootup and I successfully logged into my desktop. It then automatically hibernated since my battery didn't have much juice left.



Now, I obviously can't log back into Ubuntu to see if I get the same error message when mounting my hard drive. But, has anyone else had a similar problem as above? I have heard from so many linux guru's that linux can handle NTFS reading and partition management just fine – and I trusted their opinion. My intuition said to not continue with the install based on the errors I was receiving, but instead I had the “NTFS partitioning is safe” mentality. Well, based on my unpleasant experience, I disagree. I think once I get my power pack I'll manually resize my NTFS partition within Windows and try the install again.

Anyway, thanks for listening to my rant. And if there's someone reading this who is experiencing a similar problem with partitioning, DO NOT CONTINUE.

---

