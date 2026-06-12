---
title: "Ubuntu 11.10 freezing problem found in NVidia"
date: 2011-10-28
forum: General Help
---

### Post by HappyLinux on 2011-10-28
OK, I know the subject for this thread is a little vague but this is important for everyone to know.

Oh yes, I don't know if this has been mentioned in this forum yet, so I'm writing it anyway.

Due to my recent and almost continuous problems with Xubuntu 11.10 since day one, I've been thinking about switching to another distro, or moving down (or is it up) too Xubuntu 11.04.

There have been threads of people trying to find out solutions to their Ubuntu/Xubuntu etc distro from freezing up.

I was just looking through Linux Mint forums to find out how to install NVidia drivers in Mint 11 when I came across people having the same freezing problem.

Several people have discovered that teh cause is recent NVidia drivers and x.org.

Come to think on it. I had a problem setting my screens resolution and refresh rate through nvidia, so had to manually override x.org.

So folks, I wouldn't be surprised if this gets straightened out at some point.

---

### Post by akoskm on 2011-10-28
Could you post us your configuration?
Is it possible that you have nvidia card with optimus technology?

---

### Post by HappyLinux on 2011-10-29
Sure.

Asus P7P55LX
Intel i7 quad-core (can't remember the speed)
4GB RAM
nVidia GTS450 1GB
not sure on the HDD

---

### Post by BigBadJohn28 on 2011-10-31
I too have had the same problem with 11.10 freezing randomly, but I've found that moving the setting on the login screen to 2D mode is fixing the problem..for me anyway.. all I'm running is 11.10 the 32 bit version on a 2010 Acer Aspire One netbook that has 84.5 GB of disk space, with the  Intel Atom CPU N450 @ 1.66GHz x 2 processor, 991.5 MiB of Memory, with the Intel® IGD x86/MMX/SSE2 graphics card. The hardrive is split into two partitions one is Ubuntu 11.10  32 bit, which has 70% of the space, and the Windows 7 that came installed on the netbook barely has enough space to run properly but not get in my way.. I've seen on other forums that it doesn't matter if the version is 32 bit or 64 bit they both have freezing problems.  As for downgrading to 11.04.. bad idea.. but it's doable .. a pain in the butt.. because to get the 11.04 version like you had it before the upgrade to 11.10 you'll need to uninstall it completely and re-install the 10.10 version then upgrade if you want back to 11.04.. but I recommend if you DO uninstall and re-install the 10.10 version not to upgrade until they've worked the bugs out in 11.10.. or come out with the newest version above that.. BUT.. by the time you do all that the problem will have a patch/debug fix available and you would've wasted your time.. but that's just me.. :cool:

---

### Post by Kheops_74 on 2011-10-31
Seem to have the same problem. I will try the 2d setup.

Do you know where this problem come from? nVidia driver, X server, etc?

---

### Post by HappyLinux on 2011-11-01
For starters, I haven't a clue about this 2D setting with Xubuntu. Secondly, I haven't a clue if it's NVidia or X. The recent NVidia drivers release notes say that they've sorted out several X.org glitches, and there have been several X.org updates as well.

For a time, I thought the fault had been rectified, but then a couple of days ago my computer froze up. In another thread, it was suggested you do the following;

Ctrl+Alt+F1
Login
sudo killall -KILL compiz
Ctrl+Alt-F7

I tried that, but I couldn't use my keyboard. I could only move my mouse. So, I was forced to hit the reset button.

As for falling back to 11.04, I always do clean installs. I don't upgrade to newer distro releases. Besides, I'm still considering Linux Mint.

---

### Post by [Neurotic] on 2011-11-21
Count me in as a +1 here.

Shocked at how often 11.10 just freezes totally. I can't even get to a TTY to try and recover. Whole thing is dead.

Seems to be whenever I move windows is when it crashes.

Is there a bug on this somewhere I can follow?

---

### Post by [Neurotic] on 2011-11-22
So opened up to proposed updates, and got the update to the nvidia driver 285.05.09, but I'm still getting total system lock ups, I can't even SSH into the computer once it's locked up.

Anyone experimented with downgrading the driver?

---

### Post by [Neurotic] on 2011-11-23
Just had a quick question for you all -

How many of you with freezing problems are running more than 1 monitor?

Thinking back to when I first install 11.10, I was only using 1 monitor, and didn't have much in the way of freezes. Wondering if it's a multi-monitor thing?

---

### Post by efflandt on 2011-11-23
I recently developed the screen freeze with my GT 430 in 64-bit Win7 and 64-bit Maverick (10.10) and 11.10 (installed from scratch a couple of weeks ago).  Everything boots from 11.10's grub on sdb.

It started in Win7 with a 270 something driver that had worked fine for about a year and continued after update to most recent 285 driver.  I removed all nvidia drivers and Win7 automatically installed a 267 driver.  But I have not booted Win7 since then, so not sure if that resolved it.

The freeze happened much less frequently in Linux, and since it happened in both 10.10 and 11.10 (and Win7) I thought I might have a hardware problem,  So I removed and reseated my video card Monday and had no more freezes (through updates Tuesday morning) until just after I logged in this evening (Wednesday).

When it freezes usually the mouse cursor still moves fine, but there is no response to clicks, scroll wheel, or keyboard (no going to console).  But sometimes the cursor freezes or is very laggy when it happens.  It might happen right after login, or not until many hours later.

And even when the screen is not frozen, if I go to the text console, I cannot get back to X, I totally lose all video signal and have to do a hard shutdown.

I am using **nvidia-current** which **dpkg-query -l nvidia*** shows is still 280.13 drivers.  When I earlier tried nvidia-current-updates (which was also 280.13) I could not wake from suspend, so I do not suspend at all.

PS: One other problem I have been having is that everything displays up to the grub menu, but somewhere between the purple screen and login screen, I sometimes totally lose video signal.  That had not happened since I reinstalled nvidia-current Monday, but happened this morning (Thursday). After a hard shutdown, 2nd boot worked.

---

### Post by [Neurotic] on 2011-12-04
I've just switched back to nouveau for now. It was either that or start rolling back through nvidia drivers to find a stable one...

---

### Post by HappyLinux on 2012-01-05
I've recently switched to LinuxMint and no longer get the freezing problems. Then again, I'm not using the most recent version of NVidia drivers. I'm using the most recent that Mint chooses to install.

Oh yes, to a previous post in this thread. I'm using a single monitor. I've never had a dual-monitor setup.

So with this, I haven't a clue if this freezing situation remains under Ubuntu.

---

### Post by AhronZombi on 2012-04-23
I find it ridiculous that this problem still exists. Wont anyone help us? Maybe at least give us a fix by backporting Xorg and nvidia drivers to the ones before the problem started. This is so frustrating.

---

### Post by thegoonden on 2012-04-24
No help, but some more info.......

It is definitely related to:
Newer Nvidia drivers
3d desktop usage


I have tried both Unity and KDE, and both go utterly bananas (technical term that) when 3d is enabled. In KDE I can hot-key my machine from running to wrecked and back with alt-shift-F12.

Now....here's the thing......This is on a newly upgraded 12.04 Beta system....during previous updates/upgrades I'd managed to hang on to the NVIDIA 173 drivers, and everything had always been quite happy (although I don't normally leave 3d on in KDE, since my video card is an 8800GTS with about a billion hours on it, and it's SUPPOSED to be having a gentle retirement in the linux machine).


So.....my next mission....try to ram NV173 drivers down the throat of 12.04 (they do load on kernel 3.0 since that was what my 11.10 system was using.....still with the older drivers).

I will post back when I get round to this, to see let you know if it causes more grief than it fixes or not.

---

### Post by rk0r on 2012-04-24
Hi 

I get the freeze problem also with Ubuntu 12.04lts, it was more so with unity. But i done a Gnome 3 update and now run that, its only occurred about 3 times so far over a good few weeks of use. 

I am starting to think that the Nvidia drivers and the Unity/Gnome have some issues with their 3D rendering..

Would like to know if there is a fix to this .. i imagine that in the next major update these issues will be addressed.


On a seperate note : do you experience issues with runing nexuiz on high graphics detail?

:mad:

---

### Post by HappyLinux on 2012-04-27
Wow, I'm surprised this thread is still running.

I'm running Mint 12, which is based on Ubuntu 11.10. For a while, I had the freezing problem, but no more. There have been a few major changes. I'm running the most recent nVidia drivers, 295.40 from the x-swat repository, and I've also switched my desktop environment from GNOME to Cinnamon.

In addition, there have been a great many general system updates. Whether the problem was fixed in the nVidia drivers, or there was a compatibility problem with GNOME 3, or something in one of the general system updates, or it could have been several updates, I know not.

Now I don't have the freezing problem, but I do have a logging out problem which I created another thread for.

---

