---
title: "Ubuntu 11.04 keeps freezing up on me!"
date: 2011-06-13
forum: General Help
---

### Post by patrick848 on 2011-06-13
I don't know what's happening here, but my computer keeps freezing in Ubuntu...  I can't figure out what's triggering it, because it happens when I'm doing different things.  The time between freezes is always different, sometimes hours, sometimes a whole day, and sometimes back-to-back after a reboot.  The only way to get out is a hard reset.  Whatever sound is playing will just continue to loop.  It's happened while watching (non-full screen) YouTube, while using Eclipse (Luckily had just saved work), and while just general browsing.  I tried reinstalling 11.04 because it happened before, and for a little while I thought it was fixed, but in the past few days it has picked up again.  The only thing I can think of that I have installed was some new drivers for my BCM43225 wireless because it was always slow.

---

### Post by metafile on 2011-07-02
Same thing happens for me. I'm running Ubuntu 11.04 on an Acer laptop with vga switcheroo set to use integrated graphics. I've been using this setup for about a couple of months now. I've been getting Compiz freezes almost since the very installation, but that happened like once a week, and killing compiz usually helped.

Since about two or three days ago, I'm getting almost 1 freeze a day, and it's impossible to even go to console mode (alt-shift-f1), the system becomes unresponsive to keyboard (yet mouse does work).

I also often make the laptop go to sleep and back again, maybe this is somehow related. This issue hasn't yet annoyed me enough to start debugging it myself. 

Just a "plus one" comment.

---

### Post by catbeef on 2011-07-02
I'll throw my troubles in this thread as well, instead of making a whole new one - though the causes are likely to be different, who knows.

So I burned the Ubuntu 11.04 64bit CD, booted from CD for a test, quite liked the design and decided to give it a partition alongside Windows 7.
But Ubuntu has been freezing up randomly during use, mouse/keyboard unresponsive and no garbled graphics, and I mean completely randomly, anywhere from right at login, after 5 minutes, after 10 minutes, after 15.. longest without a freeze was maybe 30 minutes. Using any program, using no program, no difference.
At first there was occasional Kernel Panics, but since upgrading the kernel to 2.6.39 there have been no panics, only freezing.

Have googled this to death and nothing that helped anyone else has helped me, tried a few kernels, Natty 2.6.39 through to r4.. Been through a vast variety of nvidia drivers with no difference in crash rate. Disabled Unity, no change.
Reinstalled Ubuntu a few times without updating, still crashes. Memtest says my ram is fine.
Can't find anything that seems out of place in the system logs apart from [this](http://i55.tinypic.com/2gso01x.png) which repeats every 20 seconds.. but I am not 100% sure what I would be looking for, so tips welcome~
Have monitored temperatures and fan speeds just waiting for a crash, nothing out of the ordinary precedes.. regular temps, regular speeds.

Really not sure where to go from here, this is my first real venture into Linux (disregarding those when I was young and bEiNg CoOl!!1) and while it was indeed a challenge I was looking for, this freezing is a little too maddening.

AMD Athlon 64 x2 3800+ @ 2.4ghz
Asus A8N-SLi, 2x1GB DDR1 ram
nVidia GeForce 9800 GT

Any other information you might need I am more than happy to provide, this is all I can think of right now though.
PC is a little old but all my hardware seems to be working well enough for Windows. I think I will go and try installing 10.04 or 10.10 right now!

Some curious updates..

10.10 had some new problems but they seem common and related to nvidia, but no random freezing after 2 hours - not long but positive!

I then installed Xubuntu 11.04, which suffers the same random freezing.. but it tends to happen after an hour or near two hours, not the constant login-30 minutes of before. But again, no errors in the logs.. seems the problem must be somewhere between the desktop and the kernel?

Looks like I'll try 10.10 a little longer and see what happens, which is a shame as I REALLY like the Unity desktop... is there anyway to get the real Unity in 10.10 - I didn't look around much but could only find the Netbook version which seems different - or maybe I was just in 2D mode?

Anyway, good luck to the chaps above me!

*_Super last edit~~_*
So 10.10 froze, opened my case and had a feel of the heat sinks quickly, Graphics card one actually hurt to touch instantly. Installed nvclock and turned up my fan speed, graphics card is now stone cold and pc has been running for an hour and forty minutes.. will have to do some tests~
Mildly annoying that it is just heat, but hey-ho what are you going to do?

ps. not heat. but now it lasts a few hours

---

### Post by Grams79 on 2011-08-22
I've been having the same issues with 11.04 too.
I have killed Unity as much as I can to get back to Gnome.
But my windows seem to lock up for 30 seconds at times.
It doesn't matter what program it is also.
The OS still runs in the back ground just find at times... other times it locks up too.
I thought my hardware was failing.... but I just rebuilt from ground up starting with the bois.
No change and I'm starting to really hate 11.04.

Can someone please find us a solution?!??![-o<

My personal theory is the culprit is Unity.
Which was the dumbest thing that Ubuntu has done in years.

---

### Post by Script Warlock on 2011-08-22
you can still login to classic gnome no effects and sort the machine. first things first update and check any drivers available for "additional hardware". after updating and upgrading was done. check the log file(System -> Administration -> Log File Viewer) viewer for possible system errors. hunt down  dmesg, syslog, kernel and boot and post here the error results using "wrap tags(quote)"..

---

### Post by Ambivalent on 2011-08-22
I get a similar issue that never happened until this last version of Ubuntu. I'll be using firefox most of the time when it happens. I thought it was flash related but I disabled hardware acceleration and it had no effect.

I will get my display flicker a few times and then it appears to be frozen. If I let it sit for a bit it will sometime come back to life. Sometimes I can ctrl-alt-F1 to a prompt and restartd gdm and other times I cannot. Latest nVidia drivers available through software update.

A little frustrated. I've never had issues like this until the latest release. Like Unity so I don't want to downgrade. If that's the only option I'll go back to Windows7 instead...

---

### Post by doublemcz on 2011-08-24
I have the same issue as the guy in this thread. Freezing comes up time to time. Where I should start...?

---

### Post by doublemcz on 2011-08-30
Is anybody able to help me? :(

---

### Post by newcscsl on 2011-09-02
this problem has been happening to me too. I am going  to resize the swap space (4GM memory and 512MB swap doesn't make sense) to 8G. I'll let you know if this works.

---

### Post by bluizzo on 2011-09-03
ive been having the same issue as well, but usually when i boot on. im running a acer aspire 5253-bz602 w/ amd duel core 1.6Mhz E-350 processor and 4gb of ram

---

### Post by TSO54321 on 2011-09-04
Up until recently I have been having these same freezing issues, where the system totally locks up. No keyboard or mouse response, and this would happen once every few hours. So this morning I unchecked the box in power settings, for turning off the hard drive to save power. And so far it's not frozen on me all day.

---

### Post by gordintoronto on 2011-09-04
> **TSO54321 said:**
> Up until recently I have been having these same freezing issues, where the system totally locks up. No keyboard or mouse response, and this would happen once every few hours. So this morning I unchecked the box in power settings, for turning off the hard drive to save power. And so far it's not frozen on me all day.

Please, can you describe your computer? Brand/model, CPU, laptop/desktop, video adapter?

---

### Post by TSO54321 on 2011-09-05
> **gordintoronto said:**
> Please, can you describe your computer? Brand/model, CPU, laptop/desktop, video adapter?

Sure. Its a Dell Studio 1558 Laptop. Intel Core i5 processor, 4GB DDR3 RAM, 500GB 5400rpm hard drive, and Radeon HD4570 graphics.

---

### Post by doublemcz on 2011-09-06
Does anybody solved this issue? 

Now I am getting next issue next to random freezing.

OS frezzes during starting up the Kopete client.

---

### Post by bokgeneraal on 2011-09-06
I don't know if this is useful advice. But sometimes the problem is proprietary drivers not working properly for your computer yet.  When  you do a fresh install of Ubuntu I suggest you not to install the proprietary drivers unless a large number of users have reported that  they work for Ubuntu. 
To help you with resetting your display manager after it froze do the following :
1. open a virtual console -> ctrl+alt+F(4,5,6)
2. login
3. reset the display manager -> sudo /etc/init.d/gdm restart or sudo /etc/init.d/kdm restart   (depending on whether you are running kubuntu or ubuntu )

---

### Post by doublemcz on 2011-09-07
> **bokgeneraal said:**
> I don't know if this is useful advice. But sometimes the problem is proprietary drivers not working properly for your computer yet.  When  you do a fresh install of Ubuntu I suggest you not to install the proprietary drivers unless a large number of users have reported that  they work for Ubuntu. 
To help you with resetting your display manager after it froze do the following :
1. open a virtual console -> ctrl+alt+F(4,5,6)
2. login
3. reset the display manager -> sudo /etc/init.d/gdm restart or sudo /etc/init.d/kdm restart   (depending on whether you are running kubuntu or ubuntu )

May be it helps, but It is not fine to go to the console after each start-up OS and restart the display driver.

I hope there is right way how to solve this issue.

---

### Post by ladydeth666 on 2011-09-11
I am having the same lock up issue, but mine only locks up when my system is not being used....like after being away for a few hours.

I thought it was Firefox, so I kill firefox before walking away.  Still getting lockups.

I dont allow the screen saver to come on, and I am not allowing my harddrives to go to sleep.

I am using Gnome Classic, with a few Compiz settings, like Wobbly Windows.
Unity was blamed for alot of issues, so I disabled it first.

I only allow my monitors to go to sleep.

I have an ATI HD 5870, with an Asus mobo, and Quad core AMD X4.  I also have 4g of Crucial's Ballistix Tracer DDR3 1333.

I update 11.04 regularly, but have left my ATI Catalyst at an older version.
I will update ATI and see what happens.

---

### Post by skipi-gz on 2011-09-12
I have had the same problems. 10.10 was working fine on my machine until i made a clean install of 11.04. initially i blamed unity for the problem but currently im using ubuntu media edition which doesnt have the unity interface and i am STILL getting the problem. even kubuntu is freezing up!

just throwing it out there, but could it possibly be the kernel? i just found this link now, i hope it can help
[http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0)
The reason i think it may be the kernel is because it freezes when i use it on a newer machine, but seems to work fine on an older machine.

---

### Post by skipi-gz on 2011-09-12
ok so more research tells me that it is a kernel problem. the fix is apparently kernel linux 2.6.39. i followed the instructions from this link:
[http://www.ubuntu-corner.com/2011/06/upgrade-linux-kernel-in-ubuntu-11-04-to-2-6-39-0/](http://www.ubuntu-corner.com/2011/06/upgrade-linux-kernel-in-ubuntu-11-04-to-2-6-39-0/)
but for some reason i dont see the correct available kernel when doing step (2) which means i cant carry on to step (3). i also tried installing a deb from [http://ubuntuguide.net/how-to-install-linux-kernel-2-6-39-rc4-in-ubuntu-11-04-natty](http://ubuntuguide.net/how-to-install-linux-kernel-2-6-39-rc4-in-ubuntu-11-04-natty) but i dont know if its running XD. the system monitor says that im still using 2.6.38. 

as i said im not 100% sure its a kernel problem, but other sites say its a kernel problem.

---

### Post by nitecrawler30 on 2012-02-04
Hello, I recently did the same I downloaded the newest Ubuntu 11.10 from the site.  Then I installed it ontop of Windows Vista.

I was having it freeze up on me all the time and I could use the mouse but couldn't click or do anything else.. Keyboard wasn't working. 

Then I rebooted and figured ok there has to be a setting before logging in.  Well there is.  When you get to the log in screen you will see your user name.  Across your name to the right is a little sprocket click on that And it gives you 2 options Ubuntu and Ubuntu 2D.  Click on the 2D.

I did that and never had another issue again.  So try that.. It's the fix for me.

Thank you

Shane

---

