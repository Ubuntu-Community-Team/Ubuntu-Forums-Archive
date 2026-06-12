---
title: "Does 1080p (flash) video run perfectly on a Pentium 4 2.8 GHz CPU with 1 GB RAM?"
date: 2012-10-04
forum: General Help
---

### Post by s3a on 2012-10-04
My mom wants to be able to watch high-definition videos (most importantly flash videos) and her current 903 MHz Pentium 3 computer (with 384 MB RAM) doesn't cut it so, I was hoping someone could tell me whether it would work perfectly or not before I buy it. By perfectly, I mean at least 30 frames per second with 1080p video.

Any input would be greatly appreciated!

---

### Post by GeForce 9500GT on 2012-10-04
I run flash video's / youtube video's directly from the internet on my flatscreen tv using a P4 3.0GHZ with 2 gig of ram and onboard GPU. Don't have any problems. I think 1 gig is the minimum nowadays. Best advice: just try it out and see if you encounter any issues.

---

### Post by rai4shu2 on 2012-10-04
For normal video, 1 GB would be plenty. For Flash, I don't know. Maybe, maybe not. Either way, it will need hardware acceleration to get smooth playback. See:

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

---

### Post by Chelidze on 2012-10-04
I want to share my experience about linux and i think it will answer your question 

 On linux flash runs twice as slow opposed to windows, I head Pentium 4 3.0 GHz with 1 GB RAM and gforce 6500 before it exploded from overclocking ir used to run 1080P youtube videos just fine not great you could notice sometimes it would drop frames but not often, but it was running xp and i do not know how would it run under linux

---

### Post by Statia on 2012-10-04
> **Chelidze said:**
> 
 On linux flash runs twice as slow opposed to windows, 
......
but it was running xp and i do not know how would it run under linux

:confused:

---

### Post by Chelidze on 2012-10-04
> **Statia said:**
> :confused:

Is that sarcasm ??

I love Gnu/linux/ubuntu but i am not a fan boy and will not defend by telling lies Flash on linux is just massed up

I cannot enter flash have websites with ubuntu just chugs same website on windows + antivirus no problem runs great

---

### Post by s3a on 2012-10-04
Thanks for the responses but I'm still not fully convinced as to whether I should purchase it or not. I'm actually not new to Linux; it's just that I don't have any functional hardware with such specs and the only reason I would buy that computer is so that my mother can watch videos until I upgrade my own computer (which will be in a few years) and I don't want to make her wait if I don't have to since the Pentium 4 is relatively cheap but not so cheap as to just throw the money away especially since I'm in a tight financial situation.

The computer I'm planning to get might have a weak video card so I expect there to be no GPU acceleration. I was hoping the CPU could handle it all (assuming no multitasking is being done).

Adobe says ( [http://www.adobe.com/ca/products/flashplayer/tech-specs.html](http://www.adobe.com/ca/products/flashplayer/tech-specs.html) ) that Flash requires a 2.33 GHz CPU. Does that website list the minimum system requirements or the recommended system requirements?

I might be able to insert an AMD HD4850 video card but I'm not sure if I will or if the power supply will be able to. I know that the CPU would bottleneck that GPU but the GPU would probably be lying around somewhere not being used otherwise.

---

### Post by pqwoerituytrueiwoq on 2012-10-04
I think i have a 2.8Ghz P4 in on the shelf here which version of Xubuntu (10.04, 12.04, or 12.10) are you going to be using?
don't overpay for old hardware when you can build a new budget system for under 300 easy

---

### Post by s3a on 2012-10-04
12.04. Basically, the most up-to-date LTS is my style.

Also, thanks for the warning about the money but, I'm aware that significantly better computers can be made at a cheap price. :) It's just that I want to minimize the price and have the computer at least just meet my mother's needs until I give her my current computer.

---

### Post by pqwoerituytrueiwoq on 2012-10-04
i had 10.04 in 32bit onhand but i think the nic on this thing kicked the bucket  while it was
i know i had 10.04 installed on this box before, back when it had a hdd worked great, windows could not do over 1366x768 res i could get 1600x900 on xubuntu
time to get the other box out (i have 2 of these boxes)
i can confirm it will display 1920x1080
why cant i cant a network connected, i know the cable is good i tested it with my laptop
downloading 12.04 32bit now

have not been able to install flash to test anything just so you know

got 12.04 downloaded and booting up (4:30 est)
WT the old box hates my 8' Ethernet cables but likes my 100' one (4:35 est)
it barley handles playing 480p at 1920x1080
both 1080p and 720p have really low fps
with 720p the audio gets out of line with the video (hear it before you see it)

---

### Post by s3a on 2012-10-04
Actually, if I'm not mistaken, her screen resolution is 1280x800 but she can get a few more pixels by choosing 1080p instead of 720p so does that count as 1080p (aka 1920x1080) or (approximately) 1280x800 in terms of CPU stress?

Edit: You edited your last post and said the computer displays at 1080p but did you mean it displays a 1080p flash video at 1080p or just that you logged in and used the computer for "regular things" at 1080p?

Edit #2:
Did you use the proprietary flash or an open source alternative? Could you please try viewing a 1080p flash video with the screen resolution at 1280x800 (or the closest resolution to that which you can achieve)?

---

### Post by pqwoerituytrueiwoq on 2012-10-04
flashplugin-installer (11.2.202.238ubuntu0.12.04.1) on firefox 14.0.1
resolution:1280x768
both 720p and 1080p full screen playback suck 360p looks best
test video:
[http://www.youtube.com/watch?v=XSGBVzeBUbk](http://www.youtube.com/watch?v=XSGBVzeBUbk)

do you have any old hardware to work with? (case/sata dvd/sata hdd/power supply)

attached copy of hwinfo from P4 system

---

### Post by s3a on 2012-10-04
I tested that video on my laptop which runs (the frozen) Debian 7.0 Wheezy/Testing at 480p using the open source gnash (0.8.11) player on Iceweasel (=Firefox fork) 10.0.7 and it ran perfectly however, the laptop has a Pentium Dual Core E2180 CPU (the CPU is a Core 2 Duo with less L2 Cache and not a Pentium D). My laptop is also running in 64 bit whereas my mother's computer would be running in 32 bit.

I have parts lying around in a closet but, I think a bunch of the parts (particularly the motherboard) are fried so, I can't build her a computer or build one for me to test. (If I could build one for me to test, I would just give that to her.) The parts are essentially an entire computer excluding the tower (but, to reiterate, at least one of the parts are fried).

---

### Post by pqwoerituytrueiwoq on 2012-10-04
this is a quality budget build (2.5" bay adapter is needed to properly mount ssd, but you can safely leave it on the bottom of the case plugged in)
[[IMG]http://i.imgur.com/friYBs.png[/IMG]](http://i.imgur.com/friYB.png)

---

### Post by Stonecold1995 on 2012-10-04
I'm pretty sure it'd work.  That CPU seems powerful enough, and the amount of RAM doesn't really matter that much (flash videos don't use much memory).  Of course, if the flash videos are written poorly, they may be too CPU intensive and will run slowly anyways.  For example, my laptop has a quad-core i7 @ 2.4 GHz with 16 GB of RAM, and yet there are still some flash videos and games that run *ridiculously* slow.  So don't expect *all* flash videos to run perfectly.

---

### Post by Statia on 2012-10-05
> **Chelidze said:**
> Is that sarcasm ??


No, that is utter confusion. You state Flash is twice as slow on Linux as on Windows. A very firm statement, yet you give it without any source for verification. Instead you offer to tell us your own experience, but then you proceed to tell us about a machine that runs XP. As far as I know XP is a flavour of Windows, not a Linux distribution.

I guess you are trying to say "look, a machine with this and this specification already drops frames playing Flash videos while running XP, so the experience in Linux is going to be twice as bad", but it doesn't really come across and you still don't substantiate your "twice as slow on Linux"claim, which I find hard to believe.
(Besides, XP is an 11 year old OS. I would expect it to perform worse than Linux in most respects)

Do you have a link to any benchmarks that show a 50% lower FPS on the same hardware for Linux vs Windows?

---

### Post by sumancs on 2012-10-05
Depends on your OS. 1080p flash runs perfectly on my Pentium 4 PC (3GHz) with 512MB RAM with WinXP installed.

---

