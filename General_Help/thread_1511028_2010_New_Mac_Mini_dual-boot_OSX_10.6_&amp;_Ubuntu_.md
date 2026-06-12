---
title: "2010 New Mac Mini dual-boot OSX 10.6 &amp; Ubuntu 10.04 questions"
date: 2010-06-16
forum: General Help
---

### Post by A440 on 2010-06-16
The new Mac Mini has just been refreshed. I'm thinking of getting one as a general admin machine, as they run very quietly.

I'd like to able to dual boot it with Ubuntu 10.04 and I have a few questions. The hard-drive is 350gb. Would it be possible to dual boot with OSX on two fairly small partitions, say 50gb for each OS. Leaving a remaining partition of around 250gb to keep files on for both OSX and Ubuntu? I've read about this for windows/ubuntu dual boots, but can't seem to find much on OSX/Ubuntu dual boots and whether you can share files easily between them and having common drives for data storage.

Also, general tips on dual booting a Mac Mini with Ubuntu 10.04 would be welcome (not a lot out there that I can find).

Thanks.

---

### Post by lxac on 2010-06-17
50gb each is more than enough, you can probably reduce that if your main storage will be the shared space.  For a common file system, I think you either need to get OSX to access an ext3 partition, or get ubuntu to access a HFS+ partition.  Or get them both to access FAT or NTFS. I think all are possible, but someone else might be able to give you a better idea of the reliability of each.

I think you can use boot camp to partition the drive as though you were going to install windows, and then when you get to partitioning when installing ubuntu just remove the partition you created for windows and use the free space it creates. I say this because I think the partition table needs to be MBR instead of GPT and boot camp sorts this out for you.

Use rEFIt for booting :
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

---

### Post by A440 on 2010-06-17
Thanks Ixac. Good to know that it's possible. Yep, would be very handy to know what the optimum way to format the shared storage would be.

---

### Post by srs5694 on 2010-06-17
Linux is happy on a GPT drive, and OS X prefers GPT (it won't install directly to MBR). I don't know if there are any Mac-specific reasons to dual-boot using a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which is the ugly and flaky GPT/MBR combination that Apple uses for Boot Camp; but if at all possible, I recommend avoiding that configuration because it's so prone to problems. Note that some tools will convert GPT into a hybrid MBR without telling you what they're doing. Apple's Disk Utility does this if you use it to create a FAT partition, for instance. Part of what Boot Camp does is to set up a hybrid MBR.

As to filesystem sharing, in theory you could use an HFS+ partition as a /home partition in Linux and an equivalent in OS X (IIRC, OS X puts its home directories in the /Users directory, so you'd mount the one partition as /home in Linux and /Users in OS X). I know of three caveats:


[list]
[*]By default, Linux can write to HFS+ if its journal is disabled, but not if the journal is enabled. Thus, you'll have to either use a non-journaled HFS+ partition or locate and install the modifications that enable Linux to write to a journaled HFS+ partition. I don't have references to these modifications, offhand. (A non-journaled filesystem will work fine for the most part, but the filesystem check process will be slower after a power failure, system crash, or other uncontrolled shutdown.)
[*]Linux and OS X use different user IDs (UIDs) for their first users, by default. You should be able to modify one or the other OS so that you use the same UID number in both OSes, and that should smooth over ownership issues.
[*]I don't know offhand if program configuration files in Ubuntu and OS X might step on each others' toes. It might be safest to use two home directories, one for each OS. You could always create symbolic links into each others' directories to facilitate sharing data.
[/list]


Instead of using a shared /home (or /Users in OS X) partition, you could create a separate data-exchange partition and keep each OS's home directories in its native filesystem format. Either you'd have no separate /home or /Users partitions or you'd have separate partitions for these purposes and you'd use the shared-data partition for only the subset of your data you need to share between the OSes.

Note also that OS X doesn't give many install-time options for how to partition the disk, and of course a new Mac will come set up from the factory. Thus, you may need to repartition and move data around between partitions if you decide to do something non-standard for OS X, such as put /Users on its on partition.

---

### Post by A440 on 2010-06-17
Thanks for reply srs5694. I'm following what you say (up to a point)...are you suggesting that it's a bad idea to create drive partitions with bootcamp & disk utility? which appears to the the way that most methods on the web suggest. Is there a preferred way to partition the drive so you end up with 2 or 3 GPT drives? 

In summary could a usable system most likely be say 150gb OSX, 150gb Ubuntu, with 50gb as HFS+ (non-journaled) for files that need to be shared?

---

### Post by Old MacDonald on 2010-07-09
@A440, how did you get on?

It's been three weeks and no further posting, so I wonder what happened next?

Thing is, I too am about to attempt this madness. Have been keen to try Ubuntu Studio for a while, and my recent acquisition of OS X 10.6 Snow Leopard and consequent backing up of all my files prior to a diskwipe and fresh reinstall seems the perfect opportunity.

My presence here is because this is the best (well, pretty much only) thread I've found with anybody installing the latest Ubuntu and OS X dual-booting on an iMac. Perhaps by searching sucks, but here I am (hello everybody! :) ).

So, I have just swiped the x86 ISO via torrent and am about to burn it to DVD. I already have a 32GB partition on my 320GB internal iMac drive as I used Boot Camp and WinXP many moons ago and subsequently formatted it to HFS+ (journalled). This was where I was thinking I could plonk Ubuntu Studio.

In previous Linux efforts, when I were a personal Windows user ~100% of the time, I remember the advice was to plop Windows on first, because Linux would always play nicely and put on an appropriate dual boot tool.

Try it the other way round, I was assured, and you'd find yourself having to start from scratch as Windows would excrete merrily all over your initial non-Windows OS installation.

Therefore, I was thinking I could just install each OS simply and easily, i.e. OS X  first on the big partition, then pop in the Ubuntu disk and plop Ubuntu  onto the 32GB partition.

Is this insanity?

If I don't hear back from anyone before I proceed to ward me off this path of potential danger, I shall attempt to report back upon my discoveries.

Godspeed.

Old MacDonald.

---

### Post by GreenLeafz on 2010-07-16
Greetingz, 

I am installing now ubuntu 10.04 64bit on my imac. I was previously running hardy heron nicely apart from it was impossible to install flash player on it, the sound did not work either although i fixed that in the end, but why would i want an os that cant play flash vids online lol.  I did post on here about it but had no response what so ever :cry: . So i thought screw it ill go for a newer release and hope it does not have those issues ie unable to install the flash plugins either through terminal or manual, it was cursed with errors. Which i have to say is SERIOUSLY Dissapointing.

Well, i come here now in extra disappointment after downloading 10.04 32 bit. It ran perfectly from the live cd and installed perfectly, the only thing is, when it came to reboot for the first time after installing and spitting out the live cd, it booted but froze! All it had was a black screen that said GRUB in the top left and a flashing cursor after that.  I am assuming it was GRUB hanging and had issues, i don't know i'm not a programmer!!!!!!! Now like the problems in Hardy i tried numerous things but to no avail, again REALLY REALLY DISAPPOINTING! 

So, now i am downloading 10.04 64bit and see if that makes any difference. If no luck with that then i will be saying a firm ADIOS to any form of linux.

PEACE

---

### Post by donwinchell on 2010-10-24
Dear all,
I have successfully gotten both 9.10 and 10.04 to dual boot with Mac OS X.
It did take some twisting and turning and I had the grub problems, the partitioning problems and  problem I have not seen which is I could not find 'Boot Camp' honest, looked everywhere.  But I was able to use the disk utility to set up the partitions, maybe this is the same thing as Boot Camp.

I did get 10.04 to work PERFECTLY, except, it comes with php5.3 which would not run a lot of things. I spent a good half a day following lots of advice to get it to roll-back to php5.2 and stay there, but finally gave-up and reinstalled 9.10.  Everything works great, except...
I can not REboot (note the RE). it boots fine, it runs fine and it will even boot into linux from Ifit 

---but if I do a command line REboot, it shuts down linux OK, but then hangs with a message of "shutting down "
it will not actually turn off the hardware (the mac mini) and restart.--

This did work fine under 10.04 but not under 9.10.  and I have upgraded grub.

sorry that I have not contributed any answers, but I will post how to get the mac to boot into linux instead of OSx once I get back to the office and can see what I did.
Not urgent, just annoying.  thanks in advance

---

### Post by srs5694 on 2010-10-24
FWIW, I got a used Mac Mini 1,1 recently, and I've been experimenting with this. I've gotten it to work without those bloody flaky awful hybrid MBRs that cause so many problems. I need to do some more experimentation to nail down a few details and streamline the procedures. When I'm done, I'll put up a Web page about it. With any luck, the procedures will work with other Intel-based Macs, but there are possibly important differences in CPUs and video support....

---

