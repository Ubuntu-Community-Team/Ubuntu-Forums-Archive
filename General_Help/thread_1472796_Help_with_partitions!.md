---
title: "Help with partitions!"
date: 2010-05-04
forum: General Help
---

### Post by rvgsd on 2010-05-04
Hi! 
I have a 25 GB hard-disk, with windows XP on 18 GB and Lubuntu on 6GB. 
Is it possible now to Increase the space of the Linux partition. It is fine even if i have to do a clean conplete reinstall of Lubuntu. 
Can i take some space from the windows partition without disturbing the windows OS?
Thanks for any help!

---

### Post by WorMzy on 2010-05-04
Boot into Windows and use the disk partitioner to reduce the size of the Windows partition. Then boot into Lubuntu and use Gparted to increase the size of the Lubuntu partition.

That's probably your safest bet. You'll probably want to defragment your Windows partition before you resize it though.

---

### Post by spydeyrch on 2010-05-04
> **WorMzy said:**
> Boot into Windows and use the disk partitioner to reduce the size of the Windows partition. Then boot into Lubuntu and use Gparted to increase the size of the Lubuntu partition.

That's probably your safest bet. You'll probably want to defragment your Windows partition before you resize it though.

I know that in Vista and Win7 you can use the disk partitioner to do that but I am pretty sure that that ability/function became available in vista and was not doable in XP. Even though the disk management tool is almost the same, I am pretty sure that it won't allow you to shrink your XP partition from with XP.

But, if you download GParted and burn it to a cd then boot from it, you can use that to shrink your XP partition. Just be careful, backup all your personal files, and defragment your XP partition prior to using GParted.

-Spydey :o

---

### Post by rvgsd on 2010-05-04
Thanks for the replies!
Yeah..the partitioner is not available in XP :(. Thats why i was doubtful.
So if I take use Gparted through my bootable USB with the Lubuntu setup, would it be possible to shrink the windows partition?

---

### Post by garvinrick4 on 2010-05-04
> **rvgsd said:**
> Thanks for the replies!
Yeah..the partitioner is not available in XP :(. Thats why i was doubtful.
So if I take use Gparted through my bootable USB with the Lubuntu setup, would it be possible to shrink the windows partition?
gparted can shrink the XP no problem but as stated defrag maybe 2 or 3 times.
Then shrink size of xp and then increase size of ubuntu in gparted. I have said it before but gparted can do anything except kiss you good night. I have tried just about everything in gparted and it all has worked. 
 gparted has its own live cd also, just go to there web site download there .iso file to desktop and Burn a cd. Nice to have handy. I let a Windows guy use it once and he thought he was in another world. He could not format his hdd for nothing and gparted did it in a second or two. Had to ask him for my disk back 2 or 3 times. Everyone should burn their own.

---

### Post by spydeyrch on 2010-05-04
> **garvinrick4 said:**
> gparted can shrink the XP no problem but as stated defrag maybe 2 or 3 times.
Then shrink size of xp and then increase size of ubuntu in gparted. I have said it before but gparted can do anything except kiss you good night. I have tried just about everything in gparted and it all has worked. 
 gparted has its own live cd also, just go to there web site download there .iso file to desktop and Burn a cd. Nice to have handy. I let a Windows guy use it once and he thought he was in another world. He could not format his hdd for nothing and gparted did it in a second or two. Had to ask him for my disk back 2 or 3 times. Everyone should burn their own.


I would agree, defrag about 2 or 3 times and use defraggler, not the built in defrag tool in windows. Also, keep a copy of gparted with you on a free usb drive. You can create a live version via UNetBootin or just burn it to a cd too and that will be live. My dad is a computer guy (software programmer/consultant) and has been for approx. 30 years. Had his own business for 7 years, contracted with microsoft, worked for Adaptec, Roxio, Sonic Solutions, HP, currently for Intel, both of us have written tech articles for AMD/ATI (he wrote the tech stuff, I edited and gave him the ideas), We also have done contracting work for FEI. When his home machine went down a few months ago, he tried everything, and I mean EVERYTHING that he could think of to reformat the drive but nothing would work. so eventually he came to me and asked me what to do as I usually had some "exotic", as he would call it, way of doing things. So I gave him a copy of GParted, told him what to do and left fate to run her course. He thought it was the coolest thing ever and was very grateful for it.

I never leave my house with out a live persistent USB and GParted. Never know when I am going to need it!

So use GParted and you should be fine. It is pretty straight forward and simple in design and function. If you do have questions, you know where to go to get the answers ..... here.

-Spydey :D

---

### Post by rvgsd on 2010-05-04
> **garvinrick4 said:**
> ........ I let a Windows guy use it once and he thought he was in another world.............haha that was a nice one!!
My laptop is old..you would have guessed from the hard disk size :) (thats why Lubuntu too!).

---

### Post by C.S.Cameron on 2010-05-04
I tried resizing a XP partition once with gparted and windows did not work.
I then re-sized it back to what it was and it worked again.

---

### Post by garvinrick4 on 2010-05-04
> **C.S.Cameron said:**
> I tried resizing a XP partition once with gparted and windows did not work.
I then re-sized it back to what it was and it worked again.Did you ever keep at
it until you found out what you did wrong. It isn't the software, like most mistakes I make it
is called User Error.

---

### Post by spydeyrch on 2010-05-05
Gparted has always worked for me on several different machine of varying age, components, and OS. It is what I recommend, always.

There have been times when I thought that it failed at what it did and the result didn't work, but that ended up being your basic PEBKAC, so not GParted's fault.

-Spydey :lolflag:

---

### Post by srs5694 on 2010-05-05
Just to add another perspective to this GParted love-fest, here are some problems with it (some of which have been fixed in recent versions, but since so many people have said that GParted has *always* been great, I figure mentioning old bugs is fair game):


[list]
[*]GParted tends to flake out and give no data whatsoever (or sometimes it even crashes) when partition tables are malformed in certain ways, such as partitions that overlap or extend beyond the end of the disk. This makes it impossible to correct such problems with GParted. By comparison, fdisk shows you the partition table, malformed as it is, and enables corrections. AFAIK, this problem is still current.
[*]GParted refuses to work on partitions that are currently mounted. By contrast, fdisk enables making changes to such disks, although the changes won't be used by the kernel until you reboot. The way fdisk does it can simplify things, since it can reduce the number of reboots required to achieve certain goals. AFAIK, this limitation of GParted is still current.
[*]GParted conflates partition type codes (stored in the partition table) and filesystem types (a property of data in the filesystems), making it impossible to change one without changing the other. AFAIK, this issue is still current.
[*]AFAIK, it's not possible to change a partition type code to anything GParted doesn't understand, so if you want to create a partition that's of some unusual type, you won't be able to do so with GParted. AFAIK, this is a current limitation.
[*]I've run into problems where GParted refuses to make a change, claiming that it could not simultaneously satisfy all the specified constraints. The error messages have been non-specific enough that I couldn't figure out what the problem was. Making the equivalent change using other tools, such as fdisk or gdisk, has always been easy, and GParted has been happy to deal with the resulting partition tables. Although I don't have test cases for this, I believe this issue is still current. At the very least, I ran into it just a few days ago with GParted 0.4.5 (not the very latest version, but pretty recent).
[*]Some versions of GParted delete hybrid MBRs and boot loaders on GPT disks. (This problem has been fixed, at least for boot loaders, but I don't recall about hybrid MBRs.)
[*]Some versions of GParted set incorrect partition type codes for FAT and NTFS partitions when editing GPT disks, rendering the partitions unusable by Windows or OS X. (Thankfully, this bug has been fixed in the latest versions.)
[*]GParted makes it difficult (but not impossible) to properly align partitions for the new Advanced Fomat disks (those using 4096-byte physical sectors and 512-byte logical sectors) or certain types of RAID array. Fortunately, all Linux disk partitioning tools are improving on this score, but the last I knew, GParted was behind the curve on this one. It'll probably be much better in a few more months.
[/list]


I'm sure there are other problems with GParted that I'm forgetting. IMHO, GParted's strengths (and the strengths of libparted and other libparted-based tools) lie in its ability to move/resize partitions and to manipulate filesystems along with partitions. The fdisk family does a much better job of providing direct access to the true partition table data for MBR disks, and I wrote GPT fdisk to do the same for GPT disks. Each family of tools has its place; each has its strengths and its weaknesses. (The main weaknesses of both fdisk and gdisk lie in their text-mode user interfaces, which many novices find difficult compared to the GUI GParted; and in the fact that they manipulate partitions only, not the filesystems they contain.)

---

