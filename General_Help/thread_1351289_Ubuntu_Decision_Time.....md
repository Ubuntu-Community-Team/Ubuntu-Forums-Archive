---
title: "Ubuntu Decision Time...."
date: 2009-12-10
forum: General Help
---

### Post by pluto4ps on 2009-12-10
Hi to all,

I recently taken big decision to switch from Windows (XP, Vista, 7) to Linux Ubuntu.

Q) Why I have taken this decision?

A) 
1. I am fed up with the maintenance of Windows.

2. Windows slows down after some time, after installing and uninstalling of applications & games.

3. After every uninstalling we need to delete files and registry entries left over by the applications & games.

4. Need to maintain Antivirus, Firewall, Clearing temp files, Registry, Defragment HDD.

5. Too costly when compared to free Ubuntu. 

6. And much more.....

My question is:

1. Whether is this the same in Ubuntu (like I have mentioned above with Windows)?

2. I have 64 bit Desktop, which one to install 32 bit Ubuntu or 64 bit Ubuntu?

3. I have seen lot of people having problems when upgrading from previous version of Ubuntu. Every 6 months new release.

4. Reason for Question 3 is: I have 1TB of HDD and lots of Data I will put in, so when I upgrade every 6 months, is my data safe?

5. I like games too, Will I get games to play on Ubuntu?

---

### Post by snowpine on 2009-12-10
1. I *always* recommend keeping Windows and setting up a "dual boot" with Ubuntu. This will allow you to choose between Ubuntu or Windows each time you boot the computer. 
2. 64-bit
3. I always recommend a fresh reinstall (rather than upgrading)
4.[ You need to learn about "partitioning". ]("https://help.ubuntu.com/community/HowtoPartition")If you put everything on the same partition, your data will get overwritten if you ever reinstall Ubuntu. If, however, you use a separate /home partition, you can upgrade or reinstall without losing your data. (However, you should always back up data regularly to an external disk, no matter what OS.)
5. Yes, there are many native Linux games. I find Battle Of Wesnoth very addictive. :) And because you'll be dual booting, you'll still be able to play your Windows games if you want.

---

### Post by pluto4ps on 2009-12-10
Thanks for your opinion (Snowpine) however, I have no reasons to keep Windows.

---

### Post by pluto4ps on 2009-12-10
So if I install and Uninstall applications and games on Ubuntu, will it slow down like Windows and is there any registry kind of thing in Ubuntu?

---

### Post by snowpine on 2009-12-10
Ubuntu uses the [APT package management system.]("http://en.wikipedia.org/wiki/Advanced_Packaging_Tool") It is more advanced than the Windows registry (in my opinion), and Ubuntu systems do not generally slow down over time (although it is a non-issue for me, because I reinstall every six months).

---

### Post by 5nak3 on 2009-12-10
I think you should really consider keeping windows even if it is a small part of your 1TB hard drive. Dual booting offers the best of both worlds. 

Gaming on ubuntu is a hit or miss thing. Many commercial games do not offer linux friendly options, some can be run through an emulator type program such as wine. But there is no guarantee whether or not the game will run 100%.

Whenever doing an upgrade it is important to backup your data and nothing can really be foolproof,but as snowpine already mentioned reinstall rather than upgrading maybe the best root.

I would suggest you have a read about ubuntu through a variety of sources (I do not have my bookmarks to hand on this computer so I cannot share any links), but try to get a feel about what ubuntu really offers and also what are the limitations.

It may also be an idea to post your system specs so as we can have a see if there is anything that will prove to be incompatible or may cause you trouble.

---

### Post by rahilm on 2009-12-10
I dual boot with windows , so i recommend you to do the same. (Just give it 25GB and forget about it)

If you are ready to completely quit it, i can't comment because i couldn't because of some pathetic reasons (all related to side effects of monopoly)
 
And you don't need to upgrade every 6 months. Just wait for LTS versions to get out. Latest will come by April next year i.e 10.04. Till then you can use karmic 9.10 which is the current version to get the hang of using ubuntu.

Due to limited Internet connectivity i have here, i never update my system, but it doesn't complain and i have no complaints about it.

And you can always make a different partition just to store important data. So , if by chance anything bad happens, it will happen only to the partition ubuntu is installed in and you can also use you data across distros.

---

### Post by scouser73 on 2009-12-10
**[COLOR="Red"]Answers[/COLOR]**

**1** - I've never known for Ubuntu to slow down after installing & uninstalling applications.

**2** - Download the 64 bit version of Ubuntu.

**3** - There seems to have been more issues with Karmic than previous releases of Ubuntu & I can only assume that is down to hardware.

**4** - Check [[COLOR="Red"]**Ubuntu: How To Partition**[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition")

**5** - I'm not a gamer so I can only hope someone else can better answer that for you.

> So if I install and Uninstall applications and games on Ubuntu, will it slow down like Windows and is there any registry kind of thing in Ubuntu?

Ubuntu doesn't have a registry like Windows.

---

### Post by Simian Man on 2009-12-10
> **pluto4ps said:**
> 1. Whether is this the same in Ubuntu (like I have mentioned above with Windows)?
In general, no.

> **pluto4ps said:**
> 2. I have 64 bit Desktop, which one to install 32 bit Ubuntu or 64 bit Ubuntu?
You *can* install either.  Which one you *should* install is some matter of debate.  One of the factors involved is how much ram you have.

> **pluto4ps said:**
> 3. I have seen lot of people having problems when upgrading from previous version of Ubuntu. Every 6 months new release.
4. Reason for Question 3 is: I have 1TB of HDD and lots of Data I will put in, so when I upgrade every 6 months, is my data safe?
It depends how you setup the system when you install it and also how you do the upgrade.  The important thing is you *can* upgrade without worrying about losing any data.  There are a few ways to do that and the best depends on how you want to set your system up.

> **pluto4ps said:**
> 5. I like games too, Will I get games to play on Ubuntu?
There are many free, native games on Linux of surprising quality.  You can also play some Windows games on Linux with software called "wine".  In general though, if you're a gamer, Windows will offer a much better experience in this arena though.

---

### Post by pluto4ps on 2009-12-10
My System Specifications:

Motherboard: ASUS A8N SLI PREMIUM.
RAM: 512MB.
Processor: AMD Athlon 64 3500+
Graphics Card: NVIDIA GeForce 6200 TurboCache(TM) 128MB.

---

### Post by zdunham on 2009-12-10
To me the whole decision here should be based on games. I use both Xubuntu (close enough to Ubuntu) and Windows and for basic every day use (office stuff, web browsing, email, etc.) Xubuntu works just fine and it doesn't seem to slow down. My Windows XP box doesn't slow down too much either but it has ridiculous hardware so not a fair comparison. Never had any problems with updates or upgrades for either.

I used to be a huge gamer before I finished college (and thus have no time anymore) and I can tell you that for hardcore gaming you want to be on a Windows machine. There are plenty of free and addicting games on Ubuntu but if you are into the big name games you don't want to be running them in WINE on Ubuntu (a lot won't even work that way at all).

---

### Post by TitanusEramius on 2009-12-10
I must agree with Zach, I myself plays quit a bit and have been multi-booting between Ubuntu x64 and XP x32 with no trouble what so ever. It took half a day to set up, and XP seems to run better now when it only have to support gamming. I then use Ubuntu for filemangement, applications, surfing and so on.

For the matter of x32 Vs. x64 I would choose Ubuntu x32 due to your hardware, but as mentioned earlier, some debate between the versions are going around.

Just be sure to read a bit on how to set up multiboot as it can be tricky. Hopes this helps.

Te

---

### Post by roozbeh on 2009-12-10
Well my opinion as a new comer to ubuntu is that for sure keep windows xp.

Most commercial and advance games come for windows,few are available for linux, so you have to use windows or hope that they work with wine or maybe in virtual machine.

In my opinion, installing/uninstalling programs in windows really (sometimes) slows down the computer and leave you with some unwanted data files\registery files.
But for my case, i even dont know where does linux programs get installed and when i do uninstall them, are there any leftovers or not? The problem is that there is no installer like windows and you use apt system, so no choice but to trust it, and there is usually no costum configuration available and no directory path to select for installation directory, so that after uninstall you know where to look at and see what has happened.
Maybe the mistake is to compare it with windows, but i really liked the way windows handle installation.

Also in my case, somethimes installing/uninstalling leave you with corrupted config files which does break a functionality (at least in windows it slowed things down).(this happened to me with firestarter which because of it i lost my internet connection).

So for me the maintance rate is almost same, maybe also higher in ubuntu as there are lot more softwares (that you never knew about them because you used windows ones) and if you find yourself addicted to installing new programs yo have to spend plenty of times for the first time to get to your desired configuration.
The only and biggest plus here is that you 99% of times will find a solution to your problem in linux world becuase of its great community (although somethimes you have to spend 2-3 days to get the solution) and in windows if you hit a deadend, it is a deadend, you have to install windows again.

I totally agree with 4,5, no need for antivirus and it is free.

---

### Post by bigsmitty64 on 2009-12-10
I also recommend the dual boot option, and another thing to consider is,

"Motherboard: ASUS A8N SLI PREMIUM-[SIZE=3][COLOR=RoyalBlue]RAM: 512MB[/COLOR][/SIZE]"

If you can, I would get some ram,

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820145505&cm_re=ddr_ram-_-20-145-505-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145505&cm_re=ddr_ram-_-20-145-505-_-Product)

Its fairly cheap, and will make a world of difference.

That board supports up to 4 GB of ram. 512mb is not sufficient,especially with windows, and that could be a CONSIDERABLE reason of slowdown if you are a gamer.

---

### Post by zdunham on 2009-12-10
> **pluto4ps said:**
> My System Specifications:

Motherboard: ASUS A8N SLI PREMIUM.
RAM: 512MB.
Processor: AMD Athlon 64 3500+
Graphics Card: NVIDIA GeForce 6200 TurboCache(TM) 128MB.

Also, as someone else said, you probably want a lot more RAM than that (depending on the games you play and if you want them looking good or not). For a lot of graphic-intensive games you want at least two gigabytes of RAM. This could also be contributing to "slowness" of Windows (Ubuntu would run everyday applications perfectly fine on 512 MB of RAM). 

As a side note: I'm still using an ATI Radeon x800 XT 256MB and even that is not good enough for a lot of new games so if you want to go nuts with the graphics you probably want a heftier video card.

---

### Post by Lvcoyote on 2009-12-10
> **bigsmitty64 said:**
> I also recommend the dual boot option,

"Motherboard: ASUS A8N SLI PREMIUM-[SIZE=3][COLOR=RoyalBlue]RAM: 512MB[/COLOR][/SIZE]"

If you can, I would get some ram,
That board supports up to 4 GB of ram. 512mb is not sufficient,especially with windows, and that could be a CONSIDERABLE reason of slowdown if you are a gamer.

+1
Your not really trying to run Vista and Win 7 with 512mb of ram are you??  Even running XP with that little amount of ram can be problematic.

As many have stated, you really should dual boot with Windows, especially being a new Ubuntu user.  There will be a learning curve you will go through at first and having a copy of an OS your familiar with to get you through would be wise.  If you have not used Ubuntu in the past, then you really have no idea if you will need Windows along side.  When you get to the point that you feel you can do any and everything with Ubuntu that you need, then by all means ditch Windows.  Until you reach that point, completely removing windows from your options would be foolish IMHO>

---

### Post by SVEN1 on 2009-12-10
I have switched from Windows to Ubuntu 8.10 last Feb.
No going back to Windows as a whole. I use Ubuntu 98% of the time.
Ubuntu puts fun back into computers. Too much cool stuff to play with.
I run VirtualBox and installed Windows XP for Windows programs that I really need to use.
Managed to get Wine functioning and have gotten some Windows programs to work in it.
Basically the only game I play is Urban Terror and do not have any problems using a Radeon x1900xtx video card.

You can always save your current hard drive and buy another, install it into your computer and then install Ubuntu. For any reason your not happy with Ubuntu, you can always pop your old hard drive back in. With that option you won't loose any data if you mess up a dual boot installation.

By the way Ubuntu updates are painless.

:D

---

### Post by beetleman64 on 2009-12-10
Answers to your questions:

1. Generally no, as Ubuntu and Windows are incredibly different beasts in terms of security, stability, etc.

2. Use 64-bit unless you have issues with drivers, etc.

3. I personally have never found this, although it's always a good idea to keep backups of your data should it come to that

4. As above

5. Yes, Wine will emulate many Windows games, and there are many open source/Linux games such as Super Tux Kart and Alien Arena.
edit: the games thing isn't really an issue for me, the graphics in my PC are so bad that most games (Windows or otherwise) won't run.

I run 3 computers. They run Ubuntu, Ubuntu and OpenSolaris. No issues to report. I also have designs on making a home server which will also run Ubuntu SE.

---

### Post by Simian Man on 2009-12-10
> **pluto4ps said:**
> My System Specifications:

Motherboard: ASUS A8N SLI PREMIUM.
RAM: 512MB.
Processor: AMD Athlon 64 3500+
Graphics Card: NVIDIA GeForce 6200 TurboCache(TM) 128MB.

With that little RAM, I'd definitley go 32 bits.

---

### Post by zaphod777 on 2009-12-10
> **pluto4ps said:**
> Hi to all,

I recently taken big decision to switch from Windows (XP, Vista, 7) to Linux Ubuntu.

Q) Why I have taken this decision?

A) 
1. I am fed up with the maintenance of Windows.

2. Windows slows down after some time, after installing and uninstalling of applications & games.

3. After every uninstalling we need to delete files and registry entries left over by the applications & games.

4. Need to maintain Antivirus, Firewall, Clearing temp files, Registry, Defragment HDD.

5. Too costly when compared to free Ubuntu. 

6. And much more.....

My question is:

1. Whether is this the same in Ubuntu (like I have mentioned above with Windows)?

2. I have 64 bit Desktop, which one to install 32 bit Ubuntu or 64 bit Ubuntu?

3. I have seen lot of people having problems when upgrading from previous version of Ubuntu. Every 6 months new release.

4. Reason for Question 3 is: I have 1TB of HDD and lots of Data I will put in, so when I upgrade every 6 months, is my data safe?

5. I like games too, Will I get games to play on Ubuntu?

1. I run x64 the only issue I have had is flash can be a pain to get working but the new Google Chrome has flash built in so no worrys there I recommend chrome it is pretty fast and stable. Though change the default theme it is ugly.

Might want to add 2-4 GB  of ram it is pretty dirt cheap these days but that isn't really required.

2. Rather than dual booting I like to use virtual box for XP just in case I need IE.

3. I like to do a clean install but you don't have to upgrade every 6 months you can wait untill you want to. 

I recomend trying a live CD to make sure graphics and wireless all work without tweaking.

4. Partition Home drive on  a seperate partition and it is fine. But backup data just in case.

5. Ubuntu has some games but I use my PS3 for that.

---

### Post by pluto4ps on 2009-12-11
Thanks for your time and I never thought that I would get such a response from people around here.

I am using Windows XP on desktop.
I have laptop which runs Vista on it.
[COLOR=RoyalBlue]**I will definitely upgrade my desktop RAM to 2GB.**[/COLOR]
After upgrading RAM I will install 64bit Ubuntu 9.10.
[COLOR=RoyalBlue]**I will install Virtual Box to run Windows XP, as I was doing to run Ubuntu in Windows XP Virtual Box earlier.**[/COLOR]
I hope this would give me complete switch over from Windows to Linux on my Desktop.

Thanks once again friends.

---

### Post by derrick81787 on 2009-12-11
> **pluto4ps said:**
> Thanks for your time and I never thought that I would get such a response from people around here.

I am using Windows XP on desktop.
I have laptop which runs Vista on it.
[COLOR=RoyalBlue]**I will definitely upgrade my desktop RAM to 2GB.**[/COLOR]
After upgrading RAM I will install 64bit Ubuntu 9.10.
[COLOR=RoyalBlue]**I will install Virtual Box to run Windows XP, as I was doing to run Ubuntu in Windows XP Virtual Box earlier.**[/COLOR]
I hope this would give me complete switch over from Windows to Linux on my Desktop.

Thanks once again friends.

I like that setup.  When I first switched (4 or 5 years ago) I dual booted Win XP and Ubuntu.  Once I got used to Ubuntu, I formatted over Windows and never went back.  Running it in Virtual Box is probably a better alternative than having to reboot just to do a simple task, assuming you only need Windows to run a few apps.  Seamless mode is pretty cool, too, from what I hear.

---

### Post by lykwydchykyn on 2009-12-11
> **pluto4ps said:**
> Thanks for your time and I never thought that I would get such a response from people around here.

I am using Windows XP on desktop.
I have laptop which runs Vista on it.
[COLOR=RoyalBlue]**I will definitely upgrade my desktop RAM to 2GB.**[/COLOR]
After upgrading RAM I will install 64bit Ubuntu 9.10.
[COLOR=RoyalBlue]**I will install Virtual Box to run Windows XP, as I was doing to run Ubuntu in Windows XP Virtual Box earlier.**[/COLOR]
I hope this would give me complete switch over from Windows to Linux on my Desktop.

Thanks once again friends.

Sounds good, but I hope you aren't planning on playing games in virtual box.  I've got a 3 GHz pentium D with 4 GB of RAM and a whopping great Nvidia card but even old games don't run well in VB.

---

### Post by Jason Cook on 2009-12-11
> **pluto4ps said:**
> Thanks for your opinion (Snowpine) however, I have no reasons to keep Windows.

As many other people have stated keeping Windows is a good idea. I had Windows installed on my netbook (so no way to reinstal) and wish I had it to play games and such.

---

### Post by pluto4ps on 2009-12-12
I installed Ubuntu 9.10 64bit and its great to see that I am playing with OS...Usually in Windows...Windows will play with User.....

I attached a screen shot of the system monitor just to know whether Ubuntu is running normally...

Thanks for helping me...

---

### Post by zaphod777 on 2009-12-12
looks fine to me. But it is hard to really tell too much from the screen shot. Usually the only time I really tax my machine is when I am converting videos. 

I bet Linux runs faster than Windows ever did.

---

### Post by zaphod777 on 2009-12-12
> **Jason Cook said:**
> As many other people have stated keeping Windows is a good idea. I had Windows installed on my netbook (so no way to reinstal) and wish I had it to play games and such.

If you contact the manufacturer I am sure you can get re-install media usually costs about $35. Not sure how much gaming you can do on a netbook though.

---

### Post by Jason Cook on 2009-12-12
> **zaphod777 said:**
> If you contact the manufacturer I am sure you can get re-install media usually costs about $35. Not sure how much gaming you can do on a netbook though.

I will try contacting them but I usually play games on my Desktop (which has Windows) anyway.

---

