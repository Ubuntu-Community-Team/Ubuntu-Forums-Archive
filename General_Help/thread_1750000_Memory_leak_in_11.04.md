---
title: "Memory leak in 11.04?"
date: 2011-05-05
forum: General Help
---

### Post by timgood on 2011-05-05
Is there a memory leak in Natty? After a few hours my system slows down and becomes unresponsive. The drop down menus on the panel and system tray become slow or stop working. This happens in both Unity and Classic. A reboot solves the problem, temporarily. Anyone else experiencing this?

---

### Post by 3rdalbum on 2011-05-05
What happens if you press Alt-Printscreen-K? This should kill the X server and all X programs, and deliver you back to the login screen. Does this keyboard combination work, and does the login screen come up, when you're having the problem?

---

### Post by TenPlus1 on 2011-05-05
So far everything seems to be working fine here, I have my system on for days at a time but I have removed pulseaudio and zeitgeist and tweaked things a tad...

---

### Post by timgood on 2011-05-05
> **3rdalbum said:**
> What happens if you press Alt-Printscreen-K? This should kill the X server and all X programs, and deliver you back to the login screen. Does this keyboard combination work, and does the login screen come up, when you're having the problem?

Hmmm - I'll give this a try when it happens again and let you know. Thanks for the response.

---

### Post by tangofox on 2011-05-06
Hi there,

I noticed the same exact thing happening when I migrated from 10.10 to 11.04. Memory consumption shot through the roof, and I'm not talking about buffers or cache.

Once memory is allocated, it only releases a small amount once the application/process terminates. I can't find the source of this in top, as the processes consuming the most memory don't add up to what free -m tells me.

This is happening both in Unity and in Ubuntu Classic sessions. I plan on burning a LiveCD and trying it out this weekend. Neiter Xubuntu 11.04 (without Gnome services started at system start) nor Kubuntu 11.04 LiveCD seem to have this problem.

---

### Post by Aenima99x on 2011-05-06
YES! There's a horrible memory leak in Compiz and there's an open [Bug Report on Launchpad]("https://bugs.launchpad.net/unity/+bug/720446"). A temporary workaround until it's fixed is to ALT-F2, then type unity. It will put the compiz memory usage back to normal, but keep in mind it will slowly keep rising so you may have to do this a few times a day.

---

### Post by TheSuperSteve on 2011-05-06
Just chiming in to say it happens to me as well. I switched to Ubuntu Classic desktop and it doesnt seem so bad. Memory usage becomes ridiculous while using the Unity desktop though.

---

### Post by sxe4ever on 2011-05-10
I'm having a similar issue. It seems that memory usage continuously increases the longer that I'm using it. If I leave my computer on, but idle for extended periods of times (multiple hours) and come back to it, after I login the computer is completely unresponsive except for mouse movement, but I'm not able to type in any kind of keyboard commands and also not able to see any icons or anything.

I'm going to try the Unity thing periodically and see how that works. It seems that Ubuntu would catch something like this before releasing this version....

---

### Post by timgood on 2011-05-10
> **sxe4ever said:**
> I'm having a similar issue. It seems that memory usage continuously increases the longer that I'm using it. If I leave my computer on, but idle for extended periods of times (multiple hours) and come back to it, after I login the computer is completely unresponsive except for mouse movement, but I'm not able to type in any kind of keyboard commands and also not able to see any icons or anything.

I'm going to try the Unity thing periodically and see how that works. It seems that Ubuntu would catch something like this before releasing this version....

Yes, this is making 11.04 unusable for me. I'm going to install a new kernel as outlined [here]("http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0") to see if it makes any difference. If not I will have to revert to 10.10.

---

### Post by arbrandes on 2011-05-10
Folks, try disabling indicator-multiload, that seems to be the most common cause of the memory leak.

(This doesn't mean that indicator-multiload is the culprit, it seems that it is just triggering a leak in Unity itself).

---

### Post by sxe4ever on 2011-05-10
> **arbrandes said:**
> Folks, try disabling indicator-multiload, that seems to be the most common cause of the memory leak.

(This doesn't mean that indicator-multiload is the culprit, it seems that it is just triggering a leak in Unity itself).

I'm at work right now, but I will once I'm home. I know that I was having this issue before I installed multiload, and it's actually the reason that I installed it to begin with.

---

### Post by mc4man on 2011-05-10
There are numerous leaks in natty, most of them very small but there can be a cumulative affect.
 Currently there is a compiz leak that is a per use of the dash or places and the elements within (searching, scrolling ect.), usually a few MB on first use of an element, then 1-2MB per use after that.

Opening launcher quicklists when there is more than 2  quicklist option can, *but not always),  also have a per use increase. (1MB or less

Compiz is not the only one- nautilus, Xorg and many others also have leaks

The current multiload indicator should not be used in unity - it has a constant leak of some real significance - 1MB+ per min.

The odds of all these leaks being fixed in natty are not good.

---

### Post by sxe4ever on 2011-05-11
> **mc4man said:**
> The odds of all these leaks being fixed in natty are not good.

You don't think that they're all going to be fixed at all?

---

### Post by mc4man on 2011-05-11
> **sxe4ever said:**
> You don't think that they're all going to be fixed at all?

No, I said I don't think that ALL of them will be fixed in natty.
As it stands now on my more modern hardware (3,4 GB ram) this  really isn't a big issue at all unless I was staying online for weeks at a time.
On an older p4 w/ 1GB it's still quite manageable and if need be a simple log out/in will free up a fair amount of the accumulated RSS mem. (I rarely need to during the course of a single day

As far as the worst current -the multiload indicator, whether that needs to be fixed on the indicator end or on the unity/compiz side I don't know, personally don't use other than to test

There should be some updates in the near future, unity has a ..12 version now (no real improvement in this regard), hopefully the unity ..14 and an updated compiz can improve on the dash, places, ect, issue

---

### Post by Aenima99x on 2011-05-11
> **mc4man said:**
> 
As far as the worst current -the multiload indicator, whether that needs to be fixed on the indicator end or on the unity/compiz side I don't know, personally don't use other than to test
There's a bug open specifically for it [here]("https://bugs.launchpad.net/indicator-multiload/+bug/779717")

---

### Post by mc4man on 2011-05-11
> **Aenima99x said:**
> There's a bug open specifically for it [here]("https://bugs.launchpad.net/indicator-multiload/+bug/779717")
I know - I filed it to get it out of this one (for the moment
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/720446](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/720446)

---

### Post by tangofox on 2011-05-13
> **mc4man said:**
> No, I said I don't think that ALL of them will be fixed in natty.
As it stands now on my more modern hardware (3,4 GB ram) this  really isn't a big issue at all unless I was staying online for weeks at a time.
On an older p4 w/ 1GB it's still quite manageable and if need be a simple log out/in will free up a fair amount of the accumulated RSS mem. (I rarely need to during the course of a single day

As far as the worst current -the multiload indicator, whether that needs to be fixed on the indicator end or on the unity/compiz side I don't know, personally don't use other than to test

There should be some updates in the near future, unity has a ..12 version now (no real improvement in this regard), hopefully the unity ..14 and an updated compiz can improve on the dash, places, ect, issue

  Hopefully there will be a fix for most of the leaks in the very near future. There are memory leaks everywhere with this release. All I need to do to balloon memory usage up to 2-3GB is open firefox, gedit and a terminal.  This might work for apps like those, however, for memory intensive programs, graphics etc. this really doesn't work. And frequently logging in/out isn't a practical solution. Although I have been doing this myself as well once things got too bogged down.

---

### Post by sxe4ever on 2011-05-15
Uninstalling the Multiload Indicator made Ubuntu usable for me again, apparently this what was causing the majority of my problems.

---

### Post by timgood on 2011-05-17
I've given up on Natty and re-installed 10.10 - and it was like coming home. Everything works, Skype back to normal, no slow downs or freezes. Don't know why I ever left. Perhaps 11.10, but Natty Dread is a no go for me.

---

### Post by xeddog on 2011-05-17
I have messed around with upgrading an old P4 1GB machine for several days.  The upgrade from Lucid to Maverick was perfect, but the upgrade from Maverick to Nasty was NASTY.  So I did a clean install.

After the clean install the machine seemed to run fine for 3 or 4 days (just during the day only and shutdown overnight) so I decided to move my applications on to it.  That was done yesterday morning and it ran fine all day long.  

This morning I applied 34 updates and now the machine is almost useless.  After booting up, I have maybe 3 or 4 mouse clicks before it slows down to a halt.  Eventually, even the cursor disappears.  The only thing I can see is the HD activity light will quickly blink about every 2-3 seconds.  Classic mode, and Classic with no effects doesn't help.  I'm not sure if todays updates are the cause, but that is when I first had the trouble.

Wayne

Edit:  I just booted into recovery mode and am running the machine in "FailsafeX" mode.  Seems to be clicking right along with no problems at all.  System monitor does not show any increase in memory usage in the 30 minutes or so that it has been running.

---

### Post by crlcan81 on 2011-06-01
I've seen a compiz rise every time I open a new window/menu, or it's been setting till it's taking up 5.17% of my RAM, 3.87 Gigs of 4.0 DDR3 SD 133Mhz x10s with a Nvidia GTS 250 1.0 Gig VRAM Dual DVI. Only let the system run for three or four days at max, thanks to switching to Windows for some of my games.

---

### Post by lgfunited on 2011-06-04
[QUOTE=

This morning I applied 34 updates and now the machine is almost useless.  After booting up, I have maybe 3 or 4 mouse clicks before it slows down to a halt.  Eventually, even the cursor disappears.  The only thing I can see is the HD activity light will quickly blink about every 2-3 seconds.  Classic mode, and Classic with no effects doesn't help.  I'm not sure if todays updates are the cause, but that is when I first had the trouble.

Wayne

Edit:  I just booted into recovery mode and am running the machine in "FailsafeX" mode.  Seems to be clicking right along with no problems at all.  System monitor does not show any increase in memory usage in the 30 minutes or so that it has been running.[/QUOTE]

I had a similar problem wherein memory started leaking very quickly after the first batch of updates.  I updated to the latest kernel (.39) and turned off compiz (sudo apt-get install unity-2d) and smooth sailing so far.

---

### Post by jfrorie on 2011-09-27
I was curious if anyone had any success with their memory issues?  It appears natty has a constellation of issues.  The biggest culprits appear to be e-calendar-factory and compiz.  

And this just isn't on older hardware.  I've got an 8GB i7 and this morning I came into e-calendar-factory hogging 4.7GB.  Seriously?  Overnight?  I'm having to do daily, sometime twice daily reboots due to this problem.

I just ripped off evolution to see if that will kill e-calendar once and for all.  Not sure what it took with it, but it's got to go.  I have to work.

Jim

---

### Post by elj4176 on 2011-10-07
I am seeing evolution balloon to just under 2 GB of ram overnight. I only have 2 GB of ram in this machine so that is not good.

Any fixes for this? Other than removing evolution? 

I just updated to 11.04 figuring all the bugs would be worked out by now. I also switched immediately to ubuntu classic.

---

### Post by jfrorie on 2011-10-07
> **elj4176 said:**
> I am seeing evolution balloon to just under 2 GB of ram overnight. I only have 2 GB of ram in this machine so that is not good.

Any fixes for this? Other than removing evolution? 

I just updated to 11.04 figuring all the bugs would be worked out by now. I also switched immediately to ubuntu classic.


11.04 seems to be better.  I did pull evolution in favor of Thunderbird and lightning, which BTW is much less buggy.

Java and compiz are still hogging resources.  This is getting to be ridiculous. I feel like I'm playing digital whack-a-mole.

---

