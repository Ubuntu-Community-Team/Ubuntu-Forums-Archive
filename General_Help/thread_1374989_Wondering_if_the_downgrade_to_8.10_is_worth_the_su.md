---
title: "Wondering if the downgrade to 8.10 is worth the support"
date: 2010-01-07
forum: General Help
---

### Post by grkstln on 2010-01-07
Hi, I posted this in the installation and upgrades section too, but I thought I would post it in here too seeing it is also pretty much a general question.
 
I was just wondering if anyone knew if it was worth installing ubuntu 8.10 instead of the latest version to support my ati mobility radeon x1400.
 
I tried out the latest version last night but it was giving me issues out of the box and not letting me run in the resolution I wanted. I found a driver from ati that supported the x1400 but I guess it only supports versions 8.10 and below and was giving me an error yesterday when I tried to put it on the latest ubuntu version.
 
I'm new to all this so I'm not really sure what the difference between 9 and 8 are in terms of ubuntu. I'm pretty much just wondering if it's worth finding 8.10 so I can get the driver I need, or if I'm gonna run into even more problems with an older version of ubuntu and should just stay with windows.
 
Like I said I'm completely new here so sorry if I asked anything extremely obvious. lol
 
Thanks in advance for any help or advice anyone can give me on this.

---

### Post by Guitar John on 2010-01-07
You are going to have to reinstall.  You would probably be better off going with [8.04 LTS]("http://releases.ubuntu.com/hardy/") since that will have support until April 2011.

---

### Post by khelben1979 on 2010-01-07
So you did try the older version of ATi Catalyst together with Ubuntu Karmic?

If the hardware gives you trouble, you might consider get something cheap to replace it with. In my opinion: to not be able to run updated software feels like a bad idea, but then again, it's up to you of course.

---

### Post by grkstln on 2010-01-07
Ya, It gave me some error telling me that the current version was not supported. Not really 100% sure what it said word for word as it was last night. I was giving linux mint a try as I read that it was easier for newbies like me and that it was still ubuntu under the hood.
 
At times like this I really wish I had a desktop so I could easily replace it. But I'm not that good at soldering as it is so I could really see myself messing something up if I tried to replace what's in my laptop.
 
So what I'm really wondering is am I going to be running into any compatibility issues or going to miss out on anything substantial by using the 8.04 LTS? I like the fact that I won't have to worry about losing support for a little over a year, but on the other hand I feel like I might be missing out on a good amount of stuff by using an older version.

---

### Post by mcduck on 2010-01-07
> **khelben1979 said:**
> So you did try the older version of ATi Catalyst together with Ubuntu Karmic?

If the hardware gives you trouble, you might consider get something cheap to replace it with. In my opinion: to not be able to run updated software feels like a bad idea, but then again, it's up to you of course.

The old version of drivers doesn't work with the Xorg used in new butnu versions (and recent releases of just about all Linux distributions).

By the way, I'm using 9.10 with the default opensource drivers without any problems on my laptop that has Mobility Radeon X1600. Although these cards have slightly different chips (RV515 on Radeon X1400 and RV530 on X1600) they *should* both be supported equally by the opensource radeon driver (which claims to support all R500 series chips.. Actually they claim to fully support R100–R500 and partially support R600/R700 series.

Anyway, if the radeon driver just doesn't work for you, you could try the radeonhd driver since it has some support for R500 series chips..

---

### Post by grkstln on 2010-01-07
Hrmm....
 
Well that leads me to ask if the default open source driver that comes with ubuntu would be the same one that mint would come with? I'm assuming it is but I thought I would just make sure seeing I have nothing installed right now so just getting rid of mint and replacing it with ubuntu would be no big deal if it would make all this easier.

---

### Post by mcduck on 2010-01-07
Since Mint is based on Ubuntu (basically it *is* Ubuntu, only with some extra applications and minor customizations to the desktop) it should have exactly the same drivers the equivalent Ubuntu version has.

I actually find it quite strange that you have problems with that graphics card. Based on all my knowledge it should work just fine.

Still, it might make sense to try the Ubuntu live-CD, just to make sure that there's no Mint-specific problem causing your problems. No matter how unlikely that really is, it doesn't really cost you anything to try if you just have some thumb drive or empty CD available (and no problems downloading a CD image).

You could also try some of the PPA repositories that provide new graphics driver versions, like this one: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates").

And of course you *can* just install some older Ubuntu version, but I wouldn't since sooner or later that version will loose support anyway, so at some point you have to get the system working with recent versions or stop using Linux completely. To me it would make sense to try to get things working now rather than move to outdated release just to get a little more time before having to solve the actual problem.

edit: By the way, do you have /etc/xorg.conf file now? If you do, could you post it's contents. If you don't, perhaps you should try to create one to get the correct resolution, assuming the only problem you have is not getting the resolution you want and otherwise graphics are working fine.

---

### Post by llawwehttam on 2010-01-07
If i were you I would leave it till april and use the 11.04 LTS version and see if that works. There will probably be new drivers by then too.

Drivers have always been a problem in linux. Pity or I would use nothing else. As it is 6 of my computers are various linux distros and my gaming machine is dual booted ubuntu and win7.

---

### Post by grkstln on 2010-01-07
First off, thanks for all the responses so far everyone. It's pretty awesome to find people that actually want to help a newbie like me haha
 
But ya, I'll have to give that and radeonhd a try later once I get home. 
 
Just out of curiosity though, do you think I would be missing out on anything big, or run into any type of compatibility issues if I end up having to use 8.04 instead of the latest version? I'm not really sure what the difference between the two are.

---

### Post by mcduck on 2010-01-07
> **grkstln said:**
> First off, thanks for all the responses so far everyone. It's pretty awesome to find people that actually want to help a newbie like me haha
 
But ya, I'll have to give that and radeonhd a try later once I get home. 
 
Just out of curiosity though, do you think I would be missing out on anything big, or run into any type of compatibility issues if I end up having to use 8.04 instead of the latest version? I'm not really sure what the difference between the two are.

Well, the difference is better performance, faster boot, newer versions of all programs, bunch of new applications and desktop features and of course year and a half worth of development which is quite a lot in Linux world..

For me every single Ubuntu release has been a noticeable improvement over previous one so I wouldn't even consider using older versions unless there really was no other options.

Anyway, you should probably check the xorg.conf thing first before even trying any other driver version. Like I said if the only problem is the resolution that should be fixable simply by creating xorg.conf and defining the resolution(s) you want there.

edit: to find out the differences in the versions you can simply read the release notes for each Ubuntu and Gnome version.

---

### Post by grkstln on 2010-01-07
What exactly is the /etc/xorg.conf file?

---

### Post by mcduck on 2010-01-07
It's a configuration file where all your graphical environment's system-wide settings (like video cards, their drivers, input devices like mice and keyboards etc) can be configured.

By default latest Ubuntu versions don't have that file and instead try to automatically detect everything, but if the automatic detection doesn't provide correct results all the settings can still be configured by creating that file and adding the options there.

Assuming the resolution problem is the only issue and your graphics drivers are otherwise working fine it's possible to just create that file and add a couple options there to tell the system what resolutions it should give you. That's sometimes necessary, for example if the graphics card is working like it should but display itself isn't detected correctly and therefore the system doesn't know what resolutions the display supports.

edit: by the way, it's actually /etc/X11/xorg.conf. Clearly the automatic detection has worked fine for me since I managed to give wrong path for one of the most important configuration files of a Linux system.. :D

---

