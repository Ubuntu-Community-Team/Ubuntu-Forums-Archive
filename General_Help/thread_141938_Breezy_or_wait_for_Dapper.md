---
title: "Breezy or wait for Dapper?"
date: 2006-03-09
forum: General Help
---

### Post by Ubuntuud on 2006-03-09
Hi, I have been experimanting with linux for the past few months, but now I would like to settle without changing of distro every week. My question is: should I wait for Dapper to be released or take Breezy? Are there significant changes in Dapper that can't be missed nor installed in Breezy? Thanks in advance.

---

### Post by aysiu on 2006-03-09
You can install Breezy and then upgrade to Dapper later.
If you have a separate /home partition, you can install Breezy, then install Dapper and not lose any of your settings and preferences.

---

### Post by issueperson on 2006-03-09
Dapper's coming out pretty soon, so if you don't feel like upgrading, i'd just wait personally.  it'll be a cleaner install than trying to update it, and there will be more support for it in the long run.

---

### Post by aysiu on 2006-03-09
If you have a separate /home partition, you can do a clean install of Dapper and not lose any data or settings.

---

### Post by towsonu2003 on 2006-03-09
try a bunch o other distros while you're waiting

---

### Post by earobinson on 2006-03-09
Dapper is a huge improvment imo, but still in testing so they could break it any time before the release but chances are they wont, Its a risk you take, and really it comes down to personal choice.

---

### Post by earobinson on 2006-03-09
[QUOTE=towsonu2003]try a bunch o other distros while you're waiting[/QUOTE]
best answer ever!

---

### Post by Ubuntuud on 2006-03-09
[QUOTE=towsonu2003]try a bunch o other distros while you're waiting[/QUOTE]
I allready did, but the only community that really helped me is this one, so I would like to stick with Ubuntu.
I think I'll make two partitions, I wonder why I did not think of that myself...
But then I still have one question, how big should my not /home partition be?

---

### Post by aysiu on 2006-03-09
For your / partition, I'd allocate about 6 GB to be safe (I use only 3.5 on my full installation). Then use the rest for /home

---

### Post by Ubuntuud on 2006-03-09
But shouldn't I keep some free space for software (I install alot...) Since I have 60GB I think that I will keep 14 GB free for installation, right now, I'm using just 10GB with my /home directory (with 50% junk) so I don't think I will get in a need of lots of free space. Thanks anyway.

---

### Post by mattotoole on 2006-03-10
[QUOTE=issueperson]Dapper's coming out pretty soon, so if you don't feel like upgrading, i'd just wait personally.  it'll be a cleaner install than trying to update it, and there will be more support for it in the long run.[/QUOTE]

You're thinking like a Windows user.  A Debian system like Ubuntu upgrades cleanly.  If you're still worried about this, just keep your /home partition and reinstall everything else.

---

### Post by steve.horsley on 2006-03-11
I'd say go with Breezy. Dapper isn't even in beta yet, and as such isn't really a good start for a relative newby. I personally use a pair of 10G partitions to keep a working and an experimantal distro on.

---

### Post by tOpEzz on 2006-03-11
use breezy 1st, then if dapper release just upgrade only... later u boring if no ubuntu.. kekekekeke.

---

### Post by Ubuntuud on 2006-03-11
I would like to try a bit with an other distro two, first Gentoo looked quite challenging, but on the long run it might be a bit too much of a challenge. But could anyone recommend another distro to double-boot with Ubuntu?

---

### Post by adamkane on 2006-03-11
The Uber-Users like Slackware.

---

### Post by towsonu2003 on 2006-03-11
did you try debian by the way? I'm thinking to switch and try to see how its hardware detection works.

---

### Post by ubtpenguin on 2006-03-11
[QUOTE=Ubuntuud]But shouldn't I keep some free space for software (I install alot...) Since I have 60GB I think that I will keep 14 GB free for installation, right now, I'm using just 10GB with my /home directory (with 50% junk) so I don't think I will get in a need of lots of free space. Thanks anyway.[/QUOTE]

Yeah actually that was my big problem always.

how much space is need for applications.

That is really crap actually hehee

Anyone have any suggeestions?

I have 400GB harddrive.

I don't have separated partition arrrgggg.

\\:D/ 

Partition is headache for me.

---

### Post by kar-tar on 2006-03-11
better question:

Why doesn't "apt-get install upgrade" work reliably in ubuntu.  I still haven't heard a good explanation of why this is the case.  We're Debian based after all.

---

### Post by kar-tar on 2006-03-11
also re: partitioning.

People familiar with Windows are used to having gigs and gigs of applications.  This is probably not going to be the case in Linux.

There just isn't the Linux equivalent of an MS Office full install or Half Life 2 or other such pieces of software that take up 500+ megs a piece.  Most pieces of linux software are a few dozen megs or less, usually much less.  I like to try out just about every interesting bit of Linux-compatible software out there, and I'm not much of one for uninstalling.  I've never had / come close to taking up 10 gigs, even on boxes that ran for *years* without a reformat.

If you've got a desktop, find an old harddrive (don't worry so much about gigs, just go for high rpm) and make that /.  Then get the biggest drive you can get your hands on and make that /home and swap.  (You're going to need to read simultaneously from / and swap much more often than from /home and swap)

I'm waiting for laptops to start coming with built in 1 gig high-speed flash drives for swap and boot.

---

### Post by jaja23bd on 2006-03-11
hi
  I have three partition for Linux .. and they are..
  /boot
  /
  /linuxswap
 ...............
  which one you guys are calling /home.
.....
 BTW, Can i install Dapper by making another partition and keep it as seperate Operating system. Also i have two HDD and lots of free space :). The first HDD configuaration like

 dha1 -- fat32 -- /wxp1 -- 7.7 GB - primary >> windows xp 
 dha2 -- ext3 -- /boot -- 200 MB --  primary --boot flag
 dha2 -- ext3 -- /boot -- 11 GB -- primary -- >> Ubuntu 5.1 breezy
>> extended partition
 dha3 -- fat32 --/wxp11 -- 9 GB -- logical 
 dha4 -- fat32 --/wxp2 -- 9 GB -- logical >> windows xp 2nd OS
 dha5 -- fat32 --/wxp22 -- 8GB -- logical
 dha6 -- fat32 --/other -- 18GB -- logical >> basically nothing there
 dha7 -- linuxswap -- logical
........................

  So now can i resize (I can do that via partition magic) dha6 and make another partition, so there i can install DAPPER.. Or is there any better way??

 Thanks..

 Regards

---

### Post by atoponce on 2006-03-11
[quote=Ubuntuud]I would like to try a bit with an other distro two, first Gentoo looked quite challenging, but on the long run it might be a bit too much of a challenge. But could anyone recommend another distro to double-boot with Ubuntu?[/quote]

I'd still recommend Gentoo.  It is *A LOT* easier to install, now that the 2006.0 LiveCD was released.  It has a graphical installer after the LiveCD has booted, and will walk you through everything.  Once up, you can tweak your system to your hearts content.  If Gentoo scares you, then install Debian stable ro unstable.  You can never go wrong with Debian.

---

### Post by Ubuntuud on 2006-03-12
I think Debian is a bit to similar to Ubuntu, I tried Gentoo, but had no graphical installer, now there is one I might give it another go...

---

### Post by atoponce on 2006-03-12
[quote=Ubuntuud]I think Debian is a bit to similar to Ubuntu, I tried Gentoo, but had no graphical installer, now there is one I might give it another go...[/quote] For the Gentoo graphical installer, you need to get the latest [LiveCD, 2006.0]("http://www.gentoo.org/main/en/where.xml").  The LiveCD needs to be running, with the GUI and everything, before you can launch the installer.

---

### Post by Ubuntuud on 2006-03-13
A LiveCD with an installer???

---

### Post by engla on 2006-03-13
[QUOTE=Ubuntuud]A LiveCD with an installer???[/QUOTE]
Look for it in the next Dapper release
;-)

---

### Post by aysiu on 2006-03-13
It's called the *Espresso Installer*. You can see [here](http://shots.osdir.com/slideshows/slideshow.php?release=593&slide=36) screenshots of it in action.

---

### Post by byen on 2006-03-13
In addition to this I think we will also have a [new program]("http://www.ubuntuforums.org/showthread.php?t=119637") that will help us update/upgrade from Breezy to Dapper without having to manually change anything.... I know its not a big deal but sure makes things easy!

---

