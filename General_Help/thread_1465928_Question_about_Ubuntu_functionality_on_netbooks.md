---
title: "Question about Ubuntu functionality on netbooks"
date: 2010-04-29
forum: General Help
---

### Post by Noobs*McGee on 2010-04-29
Hey Forums,

So, I recently purchased a really nice desktop pc from iBuyPower along with an Asus 1201HAB netbook, replacing my Toshiba Satellite laptop (whose system board died after a faithful four years of virtually flawless operation :() on which I had Windows 7 and Ubuntu 9.10 dual boot.

Having grown quite fond of Ubuntu in the short time I was using it (less than a year), I decided I wanted it on my new desktop, and, if possible, on my netbook as well.  I've already installed Ubuntu on my desktop, and it's running great, so now I'd like to get it installed on my netbook as well.  I knew about UNR/UNE before my old laptop died, and I thought it might be cool to try it out on my new netbook.  However, I put both the UNE and the regular Ubuntu Desktop installers on a flash drive to try out, and when I went to try them out on my netbook (via Live Boot from the flash drive) it was *very* sluggish. 

Which brings me to my question:  is this sluggishness inherent to use on a netbook, or does it have something to do with booting from a flash drive?  The netbook has pretty decent specs (I think): Intel Atom Z520 Processor @ 1.33 GHz, 1GB RAM, 150GB HDD

Does anyone have any experience with this netbook specifically, or with either or both Ubuntu distros (UNE and Desktop) on any netbook?  Do you think the OS with operate more smoothly once installed, and would you recommend one distro over the other?

Any input would be greatly appreciated!

Cheers,
NM

---

### Post by Noobs*McGee on 2010-04-30
Any thoughts?

---

### Post by CharlesA on 2010-04-30
I noticed the same thing on my Asus 1005HA netbook. It seemed like Lucid took almost 2 minutes to go from "loading screen" to desktop. The machine is running a 1.66Ghz Atom with 2GB of RAM.

I tried it in a VM yesterday on my desktop (booted off iso) and it took maybe 20-30 seconds to load.

I don't know if it's cuz it's going off of USB or if it's just the netbook.

Ubuntu 9.10 would boot in about 30-45 seconds.

---

### Post by GSF1200S on 2010-04-30
Its definitely due to using it on a flash drive.

I have Windows XP on my Asus 1005HA-P, and it has gotten amazingly slow in just a few months.. I have a core list of programs installed, Eset Nod32 antivirus (one of the lightest and best), and all I did was use WinSCP and Firefox- still slow.

I used Ubuntu 9.10 Beta 2 a while ago and it was very fast, but I had a network manager bug that made me go back to XP (has been fixed in 10.04). Im installing 10.04 UNE as we speak and I can guarantee the speed will be better than my Windows install.

The only legitimate complaint one could wage that I can think of is that you might lose battery life with UNE. For me, it was the opposite, but I reason this is due to my programs on Windows constantly taxing the hard drive. Ubuntu lasted about 10 minutes longer just sitting idle (yes, I timed it), and that was back on 9.10 b2. I say go for it, or maybe dual boot if you have the space.

EDIT** I will let you guys know the boot time on mine when I get done installing- Im currently trying to help people get 10.04 issues fixed, install, and monitor this thread.. Give me a little time, and Ill report back.

---

### Post by snowpine on 2010-04-30
Live mode performance will always be slower than installed performance. You will have to install Ubuntu to get an accurate benchmark. Also make sure you have the [proper graphics drivers installed]("http://ubuntuforums.org/showthread.php?t=1229345") ([GMA500 is not supported]("http://ubuntuforums.org/showthread.php?t=1428736") "out of the box" by Ubuntu) as that will make a **huge** difference in perceived performance.

Speaking of benchmarks, I have read that your chip is [comparable to a Pentium 4 or Celeron]("http://www.cpubenchmark.net/cpu_lookup.php?cpu=Intel+Atom+Z520+%40+1.33GHz") so make sure your expectations are realistic. :)

---

### Post by happyt8r on 2010-04-30
I have been having the same issue with sluggishness on my Asus Eee 900HA after clean installing 10.04UNE to replace 9.10UNR.  Its almost as if its not running in 1.6ghz and running in the 900mhz mode instead. Everything works its just slow.

---

### Post by bodhi.zazen on 2010-04-30
I found a standard installation ran faster then UNE on my netbook.

---

### Post by GSF1200S on 2010-04-30
While plymouth does not work on startup (it works on shutdown), it is quite fast for me. It boots in about 22 seconds (windows took almost a minute). Applications open quickly for me. I dont like the purple or the placement of the min/max/close buttons :) but thats an easy fix..

---

### Post by KegHead on 2010-04-30
Hi!

I have a Dell mini 9 running standard 10.04.

Specs: 16gb ssd, 2gb ram.

It runs great, satisfied with the performance.

I updated via the terminal.

KegHead

---

### Post by Noobs*McGee on 2010-04-30
Thanks for the replies guys, I appreciate the input.  I guess I will give dual booting the new 10.04 with my current XP install.  Hopefully it will turn out to be just running from USB that is causing the sluggishness.

@snowpine
> **snowpine said:**
> Live mode performance will always be slower than installed performance. You will have to install Ubuntu to get an accurate benchmark. Also make sure you have the [proper graphics drivers installed]("http://ubuntuforums.org/showthread.php?t=1229345") ([GMA500 is not supported]("http://ubuntuforums.org/showthread.php?t=1428736") "out of the box" by Ubuntu) as that will make a **huge** difference in perceived performance.

Speaking of benchmarks, I have read that your chip is [comparable to a Pentium 4 or Celeron]("http://www.cpubenchmark.net/cpu_lookup.php?cpu=Intel+Atom+Z520+%40+1.33GHz") so make sure your expectations are realistic. :)

I realize that the Atom processor is not a beast or anything (it is just a netbook after all) but as far as I have read/heard, it is one of the better processors you can get in a netbook, and it runs Windows XP with decent speed & minimal hangups.  Given that Ubuntu (esp. UNE) is supposed to be much more lightweight than Windows, I would expect that it would run with at least equal, if not greater speed than Windows.  Thus, I don't think my expectations are unrealistic.

---

### Post by Jynxx on 2010-04-30
I have an Asus 1005HA-P and run Windows 7, Ubuntu and BackTrack on it. I have had no problem running Ubuntu on it and find it is much quicker than my windows install. I'm not running off a live CD so I'm sure its quicker than running from USB. I'm also running the full Ubuntu version and not the netbook.

---

### Post by snowpine on 2010-04-30
The processor speed is meaningless if you don't have the correct graphics drivers installed, as menus will be slow to open, the display will be sluggish, video will not work well, etc. Please click the links in post #5 to read more.

(edit) Also, forum Search is your friend:
[http://ubuntuforums.org/showthread.php?t=1373329&highlight=1201HAB](http://ubuntuforums.org/showthread.php?t=1373329&highlight=1201HAB)
[http://ubuntuforums.org/showthread.php?t=1413201&highlight=1201HAB](http://ubuntuforums.org/showthread.php?t=1413201&highlight=1201HAB)

As for "Ubuntu (esp. UNE) is supposed to be much more lightweight than Windows" I am not sure where you are getting that misinformation. Compare hardware requirements for the two operating systems:

> Ubuntu Netbook Remix is designed to run well on netbooks with typically minimal specs, i.e.:

    * Intel Atom processor @ 1.6 GHz
    * 512 MiB of system memory (RAM)
    * 4 GB of disk space
    * Screen of 1024x600 resolution
    * Graphics chipset with support for visual effects 

> The minimum hardware requirements for Windows XP Home Edition are:

    * Pentium 233-megahertz (MHz) processor or faster (300 MHz is recommended)
    * At least 64 megabytes (MB) of RAM (128 MB is recommended)
    * At least 1.5 gigabytes (GB) of available space on the hard disk
    * CD-ROM or DVD-ROM drive
    * Keyboard and a Microsoft Mouse or some other compatible pointing device
    * Video adapter and monitor with Super VGA (800 x 600)or higher resolution
    * Sound card
    * Speakers or headphones

---

### Post by GSF1200S on 2010-04-30
> **Noobs*McGee said:**
> Thanks for the replies guys, I appreciate the input.  I guess I will give dual booting the new 10.04 with my current XP install.  Hopefully it will turn out to be just running from USB that is causing the sluggishness.

@snowpine


I realize that the Atom processor is not a beast or anything (it is just a netbook after all) but as far as I have read/heard, it is one of the better processors you can get in a netbook, and it runs Windows XP with decent speed & minimal hangups.  Given that Ubuntu (esp. UNE) is supposed to be much more lightweight than Windows, I would expect that it would run with at least equal, if not greater speed than Windows.  Thus, I don't think my expectations are unrealistic.

No, its not unrealistic. It must be either your netbook or a display driver though- it blows XP out of the water for me, and I barely have anything installed on XP.

---

### Post by SoulSurvivor on 2010-04-30
I have an early MSi Wind model with 1 GB ram, 80 GB HD, Intel Atom 1.6 Ghz, and dual boot XP / Ubuntu 9.10.  It runs fine.  Not sure if the boot up is 30 seconds, but somewhere around there and 45 seconds.  Definitely running up to speed for my satisfaction.

Just a few things seem to be buggy such as the brightness.  On start-up my brightness keeps twitching until I select a menu from the top bar.  But with some more exploring I figure I can find solutions (I'm a Ubuntu noobie)

---

### Post by mje1708 on 2010-05-03
I have an Asus EEE pc900 (2 gig Ram installed) - not even an atom processor!

It came loaded with windows xp and performance was very disappointing. A friend recommended Easypeasy (based on ubuntu 8 i think?) and after installing that I never looked back. Moved on to 9.10 netbook remix and now 10.04 netbook remix. My machine now runs fast and smoothly and is a pleasure to use. It boots from nothing in around 35 seconds with 10.04. Everything appears to work with just a few tweaks after installation - answers to make these few minor tweaks I found easily online.

I tried 10.04 out on a flashdrive first and performance was very sluggish - there is no comparison with speed you will get when installed properly.

I hope your installation does the same for you.

Regards

Mike

---

### Post by Noobs*McGee on 2010-05-03
Thanks a bunch for the input Mike/mje1708, yours was exactly the input I was hoping for, from someone who's tried multiple distros on a comparable machine from both flash boot and full install.  Not that I don't appreciate everyone else's input, you've all been incredibly helpful, and some of you brought up some things I wouldn't have thought to ask about.  Thanks again to everyone, and I'll let you know how the install goes as soon as I get the free time to give it a go.

Cheers!
NM

---

### Post by mje1708 on 2010-05-03
One piece of advice I would give you is not to use the upgrade route - try a fresh install instead. I know this is a pain if you are already using an earlier version and you have lots of things set up just as you want but I found on both my desktop and my netbook that issues arose when using upgrade. Fresh install works so much better.

Best of luck.

---

### Post by Noobs*McGee on 2010-05-03
> **mje1708 said:**
> One piece of advice I would give you is not to use the upgrade route - try a fresh install instead. I know this is a pain if you are already using an earlier version and you have lots of things set up just as you want but I found on both my desktop and my netbook that issues arose when using upgrade. Fresh install works so much better.

Best of luck.

Not a problem, I haven't installed any other OS on the machine since I bought it.  Was waiting to find out if it would run smoothly.  Thanks for the warning though.

Cheers!

---

### Post by Noobs*McGee on 2010-06-21
So I finally got around to installing Ubuntu 9.10 desktop on my Asus Eee PC 1201HAB Netbook, and it seems to run fine (if very slightly sluggish compared to Windows).  Problem is, I want to upgrade to 10.04, but every time I try to do so (2 tries thus far) my display goes all wonky.  I.E. the display becomes highly distorted or pixelated.  The first time I tried, I wasn't sure if the upgrade was continuing normally behind the distorted display or not, so I manually shut down my netbook and restarted, then attempted the upgrade again (getting the message before starting the upgrade the second time that "Not all updates can be installed" and that I should "Run a partial upgrade to install as many updates as possible".  Well, after trying this again, I again ran into the distorted display and was forced to manually shut down the computer again.  I am about to make a third attempt in the hopes that the issue will "resolve itself", but I'm doubtful, and I thought I should get some input from the community to see if anyone else had encountered a similar problem?

Edit Update:
I encountered the same display issue the third time around.  I'm  currently letting the computer run to see if it works through the issue  (the upgrade box suggested a remaining time of approx 1.25 hrs, so I  will let it run for about that long and see what happens).  If it can't  work through the issue, I think I would like to remove this install of  Ubuntu and do a clean install of 10.04 downloaded from online, but I'm  not quite sure how to do that.  If anyone can give instructions, or  direct me to some good instructions for doing that, I would really  appreciate it.

---

### Post by Noobs*McGee on 2010-06-21
3 hrs later and the display is still borked and it doesn't seem that the upgrade is progressing.  I have a pretty slow internet connect at home, so I might leave it running overnight to see what happens, but I'm guessing not much.  We'll see.  Any input is still appreciated though...

---

### Post by snowpine on 2010-06-21
> **Noobs*McGee said:**
> Problem is, I want to upgrade to 10.04, but every time I try to do so (2 tries thus far) my display goes all wonky.  I.E. the display becomes highly distorted or pixelated. 

Does your netbook use GMA500 graphics by any chance?
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

> **Noobs*McGee said:**
> getting the message before starting the upgrade the second time that "Not all updates can be installed" and that I should "Run a partial upgrade to install as many updates as possible".  

Partial upgrades are a little tricky...
[http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

---

### Post by kidrocky on 2010-06-22
I'm a computer newbie so please pardon me if my post is very rudimentary. 

Last February, I bought a Dell mini netbook (1.66GHz, 1GB, 250GB, 10.1", 1024X600) with Windows 7 Starter pre-installed. Because I cannot change the wallpaper (it's the sole reason), I decided last week to try the Ubuntu 10.04 remix off a USB.

Anyway, I downloaded the image (actually I downloaded both remix and desktop images) from the Ubuntu site including the 'universal-usb-installer' and make the startup usb in Windows. I was satisfied so I decided to multi-boot with Ubuntu 10.04 remix but during installation to a spare space (I deleted my windows recovery disk), I was getting errors and the installation failed. I run the installation again but I still cannot get a successful install.

Next, I booted to Windows and make a startup usb for the Ubuntu 10.04 desktop image and booted from the made usb. The installation was successful. After booting to ubuntu, I updated and installed drivers and programs using steps googled and searched on this ubuntu forum site ( i was using my work pc googling for information until my wireless is working - initially my wireless was not working after the installation).

A week later, I have installed, tried and removed programs through the Ubuntu Software Center. Although, there are plenty of bugs still present in this OS using it is excellent and hopefully these bugs will be fixed.

Currently, I am multi-booting with Windows 7 Starter and Ubuntu 10.04 Desktop on my netbook but it has been 8 days since I booted from Windows. I planned to try again the remix but I have spent countless hours already in setting up the desktop version so I think I do not need to install the remix although I think the remix version is faster in a netbook.

The issues with the ubuntu on my netbook:
1. the applets sometimes moved to other areas in the panel after a reboot even though they are locked.
2. some program windows cannot be displayed fully (maybe because i'm not using the optimized remix on a netbook?)
3. some windows programs cannot be run (i cannot run most programs with Wine).
4. If a program hangs up in fullscreen I cannot force quit it.
5. On music players, I always have errors in playlists during a program restart.

On the bright side:
1. It runs faster than Windows (maybe much faster if i'm using the remix?)
2. Have a lot of free games and educational programs.
3. Finally, I can change wallpaper anytime with anything!

---

### Post by Noobs*McGee on 2010-06-22
> **snowpine said:**
> Does your netbook use GMA500 graphics by any chance?
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)



Partial upgrades are a little tricky...
[http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)


Thanks for the response snowpine.  I'm not sure if my netbook uses GMA500, but I will give it a look when I get a chance.  I'll let you know if I have any success.

-NM

---

