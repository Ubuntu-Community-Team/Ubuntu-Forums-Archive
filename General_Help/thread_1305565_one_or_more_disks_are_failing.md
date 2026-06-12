---
title: "one or more disks are failing"
date: 2009-10-30
forum: General Help
---

### Post by bds28338 on 2009-10-30
so I just updated to Karmic Koala... and the first thing I'm greeted with is "one or more disks are failing". I'm going to take a educated guess and say that the disk isn't actually failing, but that it has to do with having updated to Karmic. Has anyone else had anything like this happen? Just to be on the safe side, there's a disc icon in the upper right dock which it is having me click on, I select my drive and it says "disk has many bad sectors".

Once I've clicked on that it gives me different "attributes" all of which say good or N/A EXCEPT for the following.

REALLOCATED SECTOR COUNT - Count of remapped sectors. When the hard drive finds a read/write/verification error, it marks the sector as "reallocated" and transfers data to a special reserved area (spare area)

ASSESSMENT
Warning

VALUE
Normalized: 100
Worst: 100
Threshold: 5
Value: 8848628 sectors

On a possibly related note, I did start the upgrade, but the update manager started trying to download something or other and told me it could not find it on the server I had selected (a chicago server). So it let me exit, I changed to the main server, and the update went on without a hitch.

---

### Post by alphaniner on 2009-10-30
Are you getting these error reports from Palimpsest?  If so see [this]("http://ubuntuforums.org/showthread.php?t=1305452"), [this]("http://ubuntuforums.org/showthread.php?t=1302565") and [this]("https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136").

Long story short, it could be a bug.

---

### Post by bds28338 on 2009-10-30
yeah, no I was reading up on it as soon as I posted. Just kinda freaked me out, didn't want to have to get a new hard drive... completely confident it's not failing though, never had a single problem with it in Windows or Jaunty.

---

### Post by dj-toonz on 2009-10-30
It is a bug, I had the same problem when I was using fedora 11 & now Ubuntu 9.10 on a brand new hard-drive (it's a new feature in Ubuntu 9.10) all the features from fedora come over to Ubuntu :) if you want to see what new features Ubuntu is getting in the next distros, have a look at fedora as what's in Fedora 12 will be in lynx 10.4 :-p

---

### Post by peersi on 2009-10-30
I have exactly the same problem - it also makes booting up at least twice a slow as before the upgrade - I'm thinking reload from iso disk ???

---

### Post by arnab_das on 2009-10-30
had the same problem. reported it. think its a bug. (or a prob with ext4, hope not!)

---

### Post by P4man on 2009-10-30
It IS a bug. ignore the message  or disable it by going
system > administration > disk utility
Select the drive > more information
check "dont warn me if the disk is failing"

---

### Post by JBAlaska on 2009-10-30
Just the same I would double check the S.M.A.R.T with another tool, just to be safe.

Try GSmartControl, a graphical user interface for smartctl (from Smartmontools package).
 Both  GSmartControl and smartmontools are in the Karmic repository.

---

### Post by P4man on 2009-10-30
> **JBAlaska said:**
> Just the same I would double check the S.M.A.R.T with another tool, just to be safe.

Try GSmartControl, a graphical user interface for smartctl (from Smartmontools package).
 Both  GSmartControl and smartmontools are in the Karmic repository.

When it reports 8848628 relocated sectors you can bet your life its misreading. Most drives only have 100 to 200 spare sectors to remap bad sectors to.

---

### Post by smCw6GNakQn300£ on 2009-10-30
I am getting the exact same message with Karmic.

I dual-boot with Windows 7, and I've never had a problem either in Windows, or Jaunty.  I even got this disk error message when trying the Karmic Live CD, so I'm not worrying TOO much about it...

---

### Post by P4man on 2009-10-30
> **BRY said:**
> I am getting the exact same message with Karmic.

I dual-boot with Windows 7, and I've never had a problem either in Windows, or Jaunty.  I even got this disk error message when trying the Karmic Live CD, so I'm not worrying TOO much about it...

Neither windows 7 nor jaunty have a smart monitoring tool built-in as far as I know, so them not reporting it would be normal :)  Anyway use common sense if the reported value is so impossibly high, then its a reading  or interpretation error. If you'd see something like 30 relocated sectors, then Id worry.

---

### Post by SpearZ on 2009-10-30
Similar problem here.  I tried the upgrade from Jaunty to Karmic yesterday using Update Manager, which actually failed and hung all my USB devices...so I decided to go for a fresh install (I wasn't confident I could fix the problem and I like a fresh install now and again anyway ;-))

After the install I was greeted with the 'DISK HAS MANY BAD SECTORS' in Palimpsest Disk Utility.
"Reallocated Sector Count: Normalised 97, Worst 97, Threshold 10, Value 147 sectors".
When does it perform this check?  The "Value 147 sectors" seems constant whether I boot from my install, or from the Live CD.

Right now I'm running "e2fsck -c" to see what happens.
I'm hoping it is a bug, or at least e2fsck will mark the bad sectors and I can continue using the disk.
Should I be worried? :-(

---

### Post by P4man on 2009-10-30
> **SpearZ said:**
> Similar problem here.  I tried the upgrade from Jaunty to Karmic yesterday using Update Manager, which actually failed and hung all my USB devices...so I decided to go for a fresh install (I wasn't confident I could fix the problem and I like a fresh install now and again anyway ;-))

After the install I was greeted with the 'DISK HAS MANY BAD SECTORS' in Palimpsest Disk Utility.
"Reallocated Sector Count: Normalised 97, Worst 97, Threshold 10, Value 147 sectors".
When does it perform this check?  The "Value 147 sectors" seems constant whether I boot from my install, or from the Live CD.

Right now I'm running "e2fsck -c" to see what happens.
I'm hoping it is a bug, or at least e2fsck will mark the bad sectors and I can continue using the disk.
Should I be worried? :-(

Hmm.. A relocated sector count of 147 sounds credible and would indeed point to imminent failure. e2fsck is not going to help here, as long as the drive still has spare sectors, it will remap them automatically and invisibly to the OS or filesystem. The problems will only occur once the drive exhausted all spare sectors (palimsest will tell you how many it has. Mine have 100 and 200). 

Anyway you need a SMART diagnosing tool too reveal this information (like palimsest). Try another smart tool to verify, but in your case I WOULD worry your disk may be about to fail.


**edit**: it seems you already exceeded the amount of spare sectors you have, if palimsest is right, you woul have 97 spares (and 147 bad ones). So e2fsck might pick it up, Still try running a different harddrive diagnosis program, like one included on Ultimate Boot CD.

---

### Post by SpearZ on 2009-10-30
> **P4man said:**
> Hmm.. A relocated sector count of 147 sounds credible and would indeed point to imminent failure. e2fsck is not going to help here, as long as the drive still has spare sectors, it will remap them automatically and invisibly to the OS or filesystem. The problems will only occur once the drive exhausted all spare sectors (palimses will tell you how many it has. Mine have 100 and 200). 

Anyway you need a SMART diagnosing tool too reveal this information (like palimsest). Try another smart tool to verify, but in your case I WOULD worry your disk may be about to fail.

Ah ok, thanks for the info!
I just used GSmartControl and ran the Short-Self-test.  It seemed to complete ok, but also shows the same info as Palimsest regarding the 147 sectors.  I think I will just carry on as normal and make sure /home is backed up to another drive just in case everything goes wrong.  Sorry to clutter this thread.  The other errors seem to be an actual bug, and mine might just be a drive about to fail.  Thanks for the help though!

---

### Post by P4man on 2009-10-30
> **SpearZ said:**
> Ah ok, thanks for the info!
I just used GSmartControl and ran the Short-Self-test.  It seemed to complete ok, but also shows the same info as Palimsest regarding the 147 sectors.  I think I will just carry on as normal and make sure /home is backed up to another drive just in case everything goes wrong.  Sorry to clutter this thread.  The other errors seem to be an actual bug, and mine might just be a drive about to fail.  Thanks for the help though!

Sounds like a plan. Also keep an eye on that number if it increases any further then you might as well order a new drive already.

---

### Post by CharlesA on 2009-10-30
I had the same thing happen on one of my other boxes. Kinda freaked me out, since the drive in it is quite old.

Thanks for the info on other SMART tools. :-)

---

### Post by amarendra on 2009-10-30
Under Reallocated sector count I got this result:

```

Normalized: 100
Worst:      100
Threshold:  24
Value:      65537 sectors
``` [url]

And I read replies. I am kinda scared. But just 1-2 days before I had checked with HDDLife, HDDHealth and another program in Vista and all of them OKed my hard disk. 

I am running an 160 GB Fujitsu HDD (ATA FUJITSU MHW2160BH) on Dell Vostro 1500 since September 2007.
I just bought a WD Passport Essential 500 GB. I will backup my data. I may have to risk it though as can't afford another so soon.

Guys, tell about any another software in Windows or Linux which can help me counter check the claims. Can't run day long commands here.

---

### Post by P4man on 2009-10-30
> **amarendra said:**
> Under Reallocated sector count I got this result:

```

Normalized: 100
Worst:      100
Threshold:  24
Value:      **65537** sectors
``` [url]


Clearly a bogus warning caused by the same bug as everyone else here got (except SpearZ, who's drive probably really is about to fail).  Relax, Your drive is fine, but that doesnt mean you shouldnt make that backup anyhow

---

### Post by amarendra on 2009-10-30
Damn it! Now, I want to believe it's a bug.

BTW 
@P4man: See, we get exactly same count :p

---

### Post by alphaniner on 2009-10-30
Don't just believe, confirm!

See if the manufacturer of your HDD offers diagnostic tools.  If not, I recommend [SeaTools for DOS]("http://www.seagate.com/www/en-us/support/downloads/seatools").  It's made by Seagate for their drives, but in my experience it will at least do a surface scan on any brand of HDD.

---

### Post by amarendra on 2009-10-30
@alphaniner:

Yeah you are right. I will loom for a Fujitsu tool. And I have backed up data on a friend's PC in our network and on my ExtHDD.
Thanks

---

### Post by P4man on 2009-10-30
> **alphaniner said:**
> Don't just believe, confirm!

See if the manufacturer of your HDD offers diagnostic tools.  If not, I recommend [SeaTools for DOS]("http://www.seagate.com/www/en-us/support/downloads/seatools").  It's made by Seagate for their drives, but in my experience it will at least do a surface scan on any brand of HDD.

There is no harm in running that I guess, but it also wont tell you much. If the "damage" is so severe that a surface scan picks it up then there is a good chance a filesystem check would pick it up, or just using the drive would start throwing errors. Basically, you're too late.

What palimsest and other SMART monitoring tools do is query the drive's firmware for "hidden" defects that it recovered from itself, like bad sectors it relocated to spare sectors, as every modern drive does. If that happens its transparent to the user, to file system checks and surface scans (afaik), but is an indication the drive is beginning to fail, especially if those numbers go up over time. It also checks other parameters like vibration, spin up time and stuff that could indicate imminent failure, but those things are not necessarily producing read or write errors. Yet.

Clearly there is a bug in palimpsest that reports incredible amount of relocated sectors (like 65500 and more) with certain disks. 
If you suspect palimpsest from giving bogus info in that regard, run another smart monitoring tool. Boot from [ultimate boot cd]("http://www.ultimatebootcd.com/"), there is one on there (as well as diagnose programs for every harddisk vendor I ever heard off).

---

### Post by rey1321 on 2009-10-30
Hey Guys!!!!
have the same problem here,
I don't know how to read this:

Normalize:  1
Worst:      1
Threshold:  0
Value:     -1 sectors

is this really bad, I didn't have any problem with
Jaunty and I just Upgrade to 9.10,
my HD is a maxtor.

Please help!!!:(

---

### Post by rhackenb on 2009-11-01
I saw this error as soon as 9.10 installed.  Glad to see a lot of others are having it.  I'm afraid to turn off the warning but I think there is no problem at all.  

Is Ubuntu addressing the issue?

---

### Post by ephonk on 2009-11-04
One more in the "same problem" catagory, but like an idiot I bought a new drive.  In my case it's the "Current Pending Sector Count" on a Samsung 250GB laptop drive (HM250JI).  They're only $50 so I bought another and plugged it in.  Same errors.  
Downloaded the Samsung drive diagnostic utility and let it run through the whole diagnostic suite a couple times including the surface tests.  The drive is 100% clean.
Virgin drive, no dual boot.
I disabled Palimpsest.  
9.10 has been very nice otherwise...

---

### Post by Sadaiyappan on 2009-11-06
I just installed Ubuntu Karmic Koala on my brand new dell mini 10v.  It gives me the one or more disks are failing message.  I'm pretty sure its a bug as this is a new system.  what should I do?  ignore it?  or send it back to dell and ask for a new disk?

---

### Post by fie on 2010-02-14
> **rey1321 said:**
> 
Normalize:  1
Worst:      1
Threshold:  0
Value:     -1 sectors


I've got this same issue, in the middle of running a full scan. How I can have -1 bad sectors amazes me. I'm assuming it's just the error code for it not being able to figure it out.

---

### Post by Sentience on 2010-02-26
I had the same problem. However, instead of just being a false warning with no further harm occuring, all 3 computers that were running Karmic seem to have permanent hard drive problems and 2 out of 3 of them have completely failed and wont even start. 

I think that certain hard drives are actually being destroyed by the settings of this operating system....Either that or something is happening to the firmware or there is a problem with how the partitions are written or something.

This is causing objective damage to the harddrives and happening on too many computers in the same household too close to installation to be a coincidence.


Has anybody figured this out yet?

---

### Post by etyrmi on 2011-04-10
I get a similar warning :
Normalized: 100
Worst: 100
Threshold:5
Value: 65544 sectors

Not sure whether this is a real problem or not. Disk Utility is not a stable program in my experience. I will check manufacturer (Compaq) and the Ultimate Boot CD. And hopefully edit this post.

---

