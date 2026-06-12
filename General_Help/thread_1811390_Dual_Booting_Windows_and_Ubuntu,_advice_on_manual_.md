---
title: "Dual Booting Windows and Ubuntu, advice on manual partitioning."
date: 2011-07-24
forum: General Help
---

### Post by ILuvMontyPython on 2011-07-24
I am buying a new computer. I currently use Ubuntu full time, but on my new one I am planning to dual-boot. 

Here's my question. My new computer will have a 500GB HD and 4GB Memory. I plan on using Ubuntu more than Windows, specifically for internet applications etc. Windows I plan on using for media and such. 

I will be partitioning the hard drive manually, and would like to know how much room I should give each OS, how to create a large section for all my files to swap (how does swapping work?) and any other partitions I need to make for recovery.

I've read the Ubuntu and Windows "How to Dual-Boot" tutorials, and I still feel kind of lost on a general size for partitioning each section.

Any help will be great!

---

### Post by hhh on 2011-07-24
Man, Monty Python and the Holy Grail is my favorite comedy movie of all time.

Swap is not file swap, it's virtual memory...
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Although there are huge arguments about swap size, or if you even need swap, the rule is twice your system RAM so you can successfully suspend/hibernate.

With all that hard drive space, you could probably just split it 60/40 Ubuntu/Windows and be fine.

---

### Post by GWBouge on 2011-07-24
How much space is your current Ubuntu setup using?  Would be a good starting point for a recommendation.

If Windows is going to be a media effort, I'd say give it as much as possible (400GB+), as media can take up space quick, and both OS's will be able to access your videos/music/pictures if you keep them on the NTFS partition.  30GB or so is plenty for a standard web-use Ubuntu setup, unless you've got a lot of space taken up with games, media, documents, emails, or specific applications.

Personally, my Ubuntu side is using just over 34GB, and has SO many more things than I'd even feel comfortable with throwing on Windows.  But, more than half of it is just a few games and projects, namely:  Ryzom (6.4GB), Regnum Online (2.2GB), Vegastrike (1GB), Nexuiz (~800MB), FlightGear (~600MB), and about 8GB worth of Blender models and animations.

On the other side ... my Windows 7 install is using about 55GB, and pretty much only has 3 games on it and a few small programs I prefer to make the experience a little less miserable (Notepad++, Irfanview, 7zip, CCleaner, etc), but a plain Windows 7 install is only about 20GB if I remember right?

---

### Post by Kira_Belka on 2011-07-24
1. 4Gb Memory is 4x1,5=6Gb for Hibernation (Under any windows) and 4x2=8Gb for Ubuntu
2. swap is virtual memory space placed on HDD..
3. I think best way to create use next scheme for 500Gb HDD:

-ntfs partition1 (near 80Gb just for system and applications)
-ntfs partition2 (300Gb mix space for ubuntu and windows it can be second logical disk for windows and persistent mount point for ubuntu) 
-ext4 /root (20-30 Gb)
-ext4 /home (80 Gb)
swapfs

---

### Post by oldfred on 2011-07-24
I would expect each of use to give somewhat different suggestions and none are really wrong. It will be up to you on how you use system.

I have seen that the minimum for windows 7 is about 30GB. You want to have 30% free as a minimum in the NTFS partition to have it work well. But you should create a d: drive or shared NTFS partition for all the data you may want to share between systems. I have my photos, Firefox & Thunderbird profiles in the shared so both systems (XP for me) can use the same bookmarks & email without rebooting.

So I might do 50GB for windows, 25GB for Ubuntu / (root), 4GiB (4+) for swap and the rest shared between /home as ext3 or ext4 and a shared NTFS partition depending on which you think may have more data.

---

### Post by moorhead98 on 2011-07-24
If your using Ubuntu **_just_** for browsing the internet, then nothing more than thirty/forty gigabytes are needed. But if you store emails, documents, and songs/videos on it, you'll need more.
But since you have a 500 gigabyte hard drive, and you want to partition it so there is one windows and one Ubuntu partition (correct me if i'm mistaken), then I would recommend splitting it equal. If your going to play games on windows, then split it closer to to 150 (for Ubuntu) and 350 for windows. 
When you said "any other partitions for recovery", did you mean backups? 
If you did, then don't worry about it. Just use Windows Backup for the windows partition, and deja dup for ubuntu, and save the backups to either two different Cd's or one (partitioned) backup hdd.
and as for swap, like hhh said, the rule is twice your system RAM so you can suspend/hibernate.
Hope that helped

---

### Post by ILuvMontyPython on 2011-07-24
If I have three partitions one for windows, one for Ubuntu, one for swap. Would I be able to get files from one OS to another? if not how would I do this?

---

### Post by Kira_Belka on 2011-07-24
> **ILuvMontyPython said:**
> If I have three partitions one for windows, one for Ubuntu, one for swap. Would I be able to get files from one OS to another? if not how would I do this? ??? did you read my post? Ubuntu can mount any ntfs partitions..

---

### Post by ILuvMontyPython on 2011-07-24
Kira_Belka

Sorry to sound like a complete noob. I was just trying to figure out all the terms and what I was looking at... Your explanation still has my slightly confused.

would this be a decent set up? do you see any flaws?

ntfs/ partition 1- windows 7 (50gb)
ext4/ partition 2- ubuntu (30gb)
ntfs/home- virtual HD (everything left)
ext 4/ root (8gb)

I'm still kind of confused by all this...

---

### Post by GWBouge on 2011-07-24
ntfs/ext4 - Filesystem types.  Windows only likes NTFS, Ubuntu needs to be installed on ext but can read either.

/home - Where all your settings, configuration, and personal stuff for Ubuntu goes.  Put it on an ext partition

/root (or just '/') - Where your Ubuntu OS goes.

swap - Think extended ram for Ubuntu, also used for hibernation/suspending.  Use about 2x your RAM.

So, you're not far off ... closer would be something like:

swap - 8gb 
ext4 /root - ubuntu 10-30gb, depending on your software needs.
ext4 /home - Up to you, nobody else really knows how much you'll use.  50gb would be more than enough for me.
ntfs - Windows 7 50-100gb, depending on how much software you plan to install.
ntfs - Shared between Ubuntu/Win7 for media - Use whatever's left.

Note:  Creating separate partitions for /home and a shared NTFS drive isn't really necessary, but it can make things a bit easier when it comes to upgrading or if something goes sour with your Windows install.  Personally, I prefer not having partition clutter or ending up trapping dead space on a particular partition, especially since I'm never really sure where I'll need the space.  So I just run a single ext4 for Ubuntu and a single NTFS partition for Windows on my main disk (and swap space, of course), but have an eSATA backup/media drive in NTFS.

---

### Post by ILuvMontyPython on 2011-07-24
Oh my gosh thank you so much! You cleared a lot up for me!

---

### Post by Anonimar on 2011-07-25
There seems to be a bit of confusion on what the OP was originally asking due to her/him mistakenly identifying the swap partition as something else.

From my understanding the OP wants to run windows 7 and ubuntu in their own partitions only big enough for the OS themself, nothing else.

Then they intend on making a huge NTFS partition where everything will go, files,games,music, everything.

Whether or not this is a good idea, or even possible I am not sure.  I myself don't use a shared partition like that.  I have a 50/50 split with each OS and the space they are allocated.

---

