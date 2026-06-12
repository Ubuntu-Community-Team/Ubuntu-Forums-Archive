---
title: "Computer freezing up"
date: 2010-03-30
forum: General Help
---

### Post by Chuck_N on 2010-03-30
compaq presario SR1503WM;  9.10 Ubuntu Karmic Koala

This computer freezes, requiring power-off, somewhere between 2 seconds 
and 2 hours after boot-up, most every time I use it. Sometimes I've had to
power-down perhaps six times in 10 minutes.  

When it freezes I have a movable mouse-pointer that can select nothing. Right-
click does not operate.

I don't seem able to isolate a single cause. I ran a RAM check with no errors
showing. Matters not which version of Ubuntu I choose when booting. I've 
replaced mouse and keyboard. Only running 256 meg of ram and do plan to
add more soon. 

Any ideas?

Thanks, Chuck

---

### Post by Chuck_N on 2010-03-30
This computer has two drives. If I hit esc when booting, and ask to boot from the second drive, I'm in Win2K. I've tried that for a few hours and it has not frozen so far.  Therefore, the problem should be with Ubuntu, or with Ubuntu's relationship to this computer, an older Compaq Presario SR1503WM. 

I was using an older monitor, previously. Recently I bought a 20" Dell . I've had the freezing-up problem under both, in Ubuntu, but not with Win2K.

---

### Post by azagaros on 2010-03-30
First, if you have the mouse moving, the computer isn't locked up.  The user interface most likely didn't initialize properly.

The other issue, does a different mouse cause the same problems?

---

### Post by Chuck_N on 2010-03-30
same problem after changing keyboards and after changing mouse.

---

### Post by HermanAB on 2010-03-30
Howdy,

Do yu have a Nvidia card?  If so, change to the VESA driver and see whether the problem goes away.

Otherwise, change the PSU and get a UPS.

---

### Post by azagaros on 2010-03-30
The suggestion is try a different distribution of Linux.  I don't think it is Linux itself.  It might be something that Ubuntu is loading, and the only thing to do is isolate which exact software is doing it specifically.  Does Kbunto do the same thing? It has a different software set.

---

### Post by Chuck_N on 2010-03-30
thou speakest above my head.
I have over two decades of Windows, and a few LONG weeks of Ubuntu experience.
And hardware is not my forte', either.

---

### Post by Chuck_N on 2010-03-30
this is my first Linux OS,  9.10 Ubuntu KKoala

---

### Post by Chuck_N on 2010-03-30
"Hardware drivers" tells me I have no proprietary drivers.
How do I find out if I have an NVIDIA card?

---

### Post by azagaros on 2010-03-30
I have been using Windows for 2 decades too.  A spattering of Linux distributions.

The current box I have Ubuntu 9.10, which has too much stuff cached for 512mb.  This is something wouldn't be so bad if I could change it a few things.

Fedora's Distribution would not load on this box, it would lock up shortly after startup like you suggest and it was associated to the video system.

I am betting you have something similar happening.

---

### Post by Chuck_N on 2010-03-30
> **azagaros said:**
> The suggestion is try a different distribution of Linux.  I don't think it is Linux itself.  It might be something that Ubuntu is loading, and the only thing to do is isolate which exact software is doing it specifically.  Does Kbunto do the same thing? It has a different software set.

what would I have to do to try Kbuntu?

---

### Post by 98cwitr on 2010-03-30
Either nvidia or ATI drivers could be the cause...I had the same problem with ATI drivers on the old lady's laptop. I reverted to 9.04 and would like to know a solution as well.

---

### Post by Chuck_N on 2010-03-30
> **98cwitr said:**
> Either nvidia or ATI drivers could be the cause...I had the same problem with ATI drivers on the old lady's laptop. I reverted to 9.04 and would like to know a solution as well.

okay, so what would I do?

---

### Post by Chuck_N on 2010-03-30
I have a Drivers and Documentation CD that came with the Dell monitor.
Have not used it.  Tried to "replace driver" pointing to the CD,
but it said  "no driver found".   I assume I am getting little out of this monitor
now.  I'm on 1600X900.  It looks okay, but could be better.

---

### Post by Chuck_N on 2010-04-01
> **azagaros said:**
> The suggestion is try a different distribution of Linux.  I don't think it is Linux itself.  It might be something that Ubuntu is loading, and the only thing to do is isolate which exact software is doing it specifically.  Does Kbunto do the same thing? It has a different software set.


SO...... how could I go about trying Kbuntu?

I'm still freezing up, maybe once every 15 minutes on average. I cannot see anything in common causing it; sometimes 10 seconds, sometimes an hour or two. Sometimes in an application; sometimes on the desktop.  Changed keyboard, mouse, and monitor.

---

### Post by yetiman64 on 2010-04-01
1. Any drivers on a cd will be for Windows not Linux, Linux supplies its own modules (in win called drivers)

2. If you have no restricted drivers showing in Hardware Drivers, then you are more than likely to be using an ATI video card. Short of downloading and installing from the AMD site and doing a manual install (If they are available, it is Medium to Advanced User stuff). 
I would recommend staying as is re drivers. The FOSS (Free and Open Source Software) drivers for ATI cards/chipsets currently in your machine are apparently maturing OK (as far as Ubuntu devellopment is concerned) even if still not as good as NVIDIA (at this stage NVIDIA has better linux support). 
This lack of "good" drivers for ATI cards has appeared since 9.10, and is more related to the hardware manufacturer than it is to Ubuntu, Kubuntu or Xubuntu -hence changing to these probably won't make much difference - though I've never used K or X Ubuntu). BTW I have an Acer Laptop with X1600 ATI vid and saw the dropback in vid and "seizures" when changing from 9.04 to 9.10. 
You've noted how Windows is ok, that's because that's where ATI focus their development and sales etc. -the majority of the market. So its lucky you can go to either Windows or Linux. If you're patient with this situation the drivers (I think they are updated automatically in Linux) should improve over time.

3. When your display manager "seizes", please don't hard power down with the power button. Under some circumstances this can cause filesystem corruption. I'll link you to another thread where I've given directions for restarting the graphical display manager (gdm). Which when it happens, all you'll have is a movable cursor and your desktop and menus etc. as a pretty useless background pictue.

[http://ubuntuforums.org/showthread.php?t=1443039](http://ubuntuforums.org/showthread.php?t=1443039)

I don't know of any solution to this problem but to wait for current drivers to be improved.

Comments/corrections anyone?-to the above

IMO since you have both Windows and Linux, enjoy them both and keep an eye on the situation, it should improve.

Nev

Edit: Just noted the 256 MB RAM you're using, your plan to upgrade is a very good idea. I suspect doing so will improve your situation. (I'd recommend 1GB if your machine can be updated that much)

---

### Post by egalvan on 2010-04-01
> **Chuck_N said:**
> compaq presario SR1503WM;  9.10 Ubuntu Karmic Koala

This computer freezes, requiring power-off,

How long do you wait to qualify "freezing"? 
One second?
One minute?
One hour?

Please give us a time frame.

Also, is there ANY indication of activity while the computer is "frozen",
 such as lights flickering or the fan changing speeds, or hard-drive activity?

> 
When it freezes I have a movable mouse-pointer that can select nothing.
right-click does not operate.

Modern computers move the mouse in hardware.
The software (OS, etc) gets the mouse info from the hardware,
hence a moving mouse in not an indicator of a "frozen" system.

Button clicks are software, so a frozen OS/software can show as "no buttons"

>  **Only running 256 meg **of ram [B]and do plan to
add more soon.[/B] 

As soon as possible, if not sooner :D

Seriously, 256M RAM is extremely border-line for a GUI-heavy OS,
and running your video at 1600X900 is really stressing it.

Try running 'top' in a terminal (or better 'htop'),
maybe you can see what sets it off...


Another option is to install Puppy, and run that for a day or so to test the hardware.
It can run from CD, and it only needs 256M to load & run from RAM,
so it is a good test of hardware..
but the fact that Win2k runs well is a decent test,
although Windows is much more tolerant of faulty hardware than Linux.
(n.b. "tolerant" as in "let's ignore the problem",
 not "tolerant"  as in "can still run well even with bad hardware")

And Win2k runs well in 256M because it came from the old text-based DOS environment.

---

### Post by yetiman64 on 2010-04-01
Chuck,
 I just checked the HP support site and it does link to ATI's site for Windows drivers. Your video settings in your current configuration are very high indeed (as noted by egalvan) and will contribute to the problem hugely. Maybe you could consider upgrading from integrated graghics to a dedicated video card, if possible, for this machine as well as some RAM. Even a very low end cheap video card nowdays would give a significant boost  to both systems.

Is your Windows system XP as is indicated by the HP site. If so note that XP did away with the underlying DOS environment by integrating it into Windows itself (that is it did away with the ability to boot to a DOS screen at startup, but you can access a command prompt from in the GUI). I've 16 years experience with Windows, from the 3.11 days to Vista now (not worried about 7 now I'm in Ubuntu, & have been so since Gutsy Gibbon 7.10).

I'm running much higher specs on my Acer laptop, Intel T2500 2GHz dual core (32bit) processor, 2GB RAM, 667MHz FSB, X1600 ATI vid (512MB). And yet noticed the same lockups you describe, but nowhere near the severity you are having, when switching to Karmic. Hence I checked around at the time as to why and will wait till things improve.

I'll summarize with "Low RAM + High vid resolution on old (possibly very low video RAM) integrated graphics + ATI driver issues after Ubuntu 9.04" _most likely explain the situation you're describing. Correct me if any of the summary is wrong re your hardware.

Cheers Nev

---

### Post by Chuck_N on 2010-04-01
[QUOTE=egalvan;9059025]How long do you wait to qualify "freezing"? 
One second?
One minute?
One hour?

[COLOR=Red]When I see that mouseclicks and keyboard do nothing, I sometimes go have lunch and come back to see if it has freed up. Usually when I see I have mousepointer and nothing else, waiting more than 20 seconds is non-productive; it's froze.[/COLOR]

Please give us a time frame.

Also, is there ANY indication of activity while the computer is "frozen",
 such as lights flickering or the fan changing speeds, or hard-drive activity?

[COLOR=Red]no lights; no fan; nobody home
harddrive light bleeps lightly, once a second or so.....
[/COLOR]

---

### Post by Chuck_N on 2010-04-01
> **yetiman64 said:**
> Chuck,
 I just checked the HP support site and it does link to ATI's site for Windows drivers. Your video settings in your current configuration are very high indeed (as noted by egalvan) and will contribute to the problem hugely. Maybe you could consider upgrading from integrated graghics to a dedicated video card, if possible, for this machine as well as some RAM. Even a very low end cheap video card nowdays would give a significant boost  to both systems.

Cheers Nev[COLOR=Red]

I'll go for RAM plus video card.  Is my video card choice dependent only upon my hardware, or do I need to research also regarding Ubuntu?[/COLOR]

---

### Post by Chuck_N on 2010-04-01
> **yetiman64 said:**
> Chuck,

Is your Windows system XP as is indicated by the HP site. If so note that XP did away with the underlying DOS environment by integrating it into Windows itself (that is it did away with the ability to boot to a DOS screen at startup, but you can access a command prompt from in the GUI). I've 16 years experience with Windows, from the 3.11 days to Vista now (not worried about 7 now I'm in Ubuntu, & have been so since Gutsy Gibbon 7.10).

Cheers Nev

[COLOR=Red]I acquired this Compaq SR1503WM with a blown harddrive. Had access to some used drives. Put in 2 40-megs (one for windows 2K). When I get this operating, I'll put in a third drive, maybe larger, for backups and data.
I know win2K is at the end of it's useful life; just using it as a bridge to  transition to Ubuntu. [/COLOR]

---

### Post by yetiman64 on 2010-04-01
Chek with HP or good computer tech about type and maximum possible size of RAM as is older machine, also about vid, as could be AGP. You might have to look around a bit for your hardware, do more research. Try to get NVidia (Linux support is better at the moment) if possible and if it suits your machine (good tech could sort it).

[COLOR=Blue]<SNIP>[/COLOR]If blown HDD then I suspect your machine was originally XP even with the low specs but don't know for sure. (I've seen similar machines with it on), Ubuntu i suspect is perfectly fine, but your system is very low specs, and 9.10 is getting into higher end OS (nowhere near as bad as Vista though for needing resources).

I'll say even though I don't mind Vista, I by far enjoy and feel much safer using Ubuntu (and it is much easier to maintain and update etc).

Obviously every system (or even distros within Linux) have their pros and cons. I've tried out about 4 linuxes and found Ubuntu to be most novice friendly.

Hope you enjoy it,

Cheers,  Nev.

BTW You mentioned getting a book and learning linux the other day. You may want to check out this link, thats if you haven't already found it on this forum.

[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)

---

### Post by cascade9 on 2010-04-01
> **Chuck_N said:**
> [COLOR=Red]no lights; no fan; nobody home
harddrive light bleeps lightly, once a second or so.....
[/COLOR]

That sounds like its an overheating problem...but I'm just guessing, its harder to troubleshoot problems over the internet than it is when I'm in the room with the computer. ;) 

> **Chuck_N said:**
> [COLOR=Red]

I'll go for RAM plus video card. Is my video card choice dependent only upon my hardware, or do I need to research also regarding Ubuntu?[/COLOR]

Yes, the choices are very hardware dependant. No matter what you do, you are never going to get an AGP video card going on a system with no AGP slot, etc. 

Linux likes some things more than others (eg- its much happier with nVidia or ATI video cards than  it is with VIA). 

> **yetiman64 said:**
> [COLOR=Blue]Edit : Should be ok on net if you are carefull not to put in any personal details / financial details etc. Win 2k lost MS support a long time ago ie is already well past its end of life. Just be very careful.

[/COLOR][COLOR=Blue]Take care not to use win2k on Internet nowdays, [COLOR=Red]at all[/COLOR], as very out of date and not updatable or securable at all.[/COLOR] If blown HDD then I suspect your machine was originally XP even with the low specs but don't know for sure. (I've seen similar machines with it on), Ubuntu i suspect is perfectly fine, but your system is very low specs, and 9.10 is getting into higher end OS (nowhere near as bad as Vista though for needing resources).


Ummm...no, windows 2000 is still in support from microsoft-

[http://support.microsoft.com/ph/1131](http://support.microsoft.com/ph/1131)

Yeah, it ends soon. (I would bet that support gets extended even further, but I've been wrong on that before) But its still supported. With a 3rd party firewall (not that there is an offical firewall for 2K, not that it maters much because the windows XP firewall is fatally flawed IMO) and a 3rd party browser (firefox or opera are the biggest) is should be fine on the internet.  

BTW, yes, it was originally a WinXP box (see specs linked below) 
 
> **yetiman64 said:**
> Chek with HP or good computer tech about type and maximum possible size of RAM as is older machine, also about vid, as could be AGP. You might have to look around a bit for your hardware, do more research. Try to get NVidia (Linux support is better at the moment) if possible and if it suits your machine (good tech could sort it). 

That machine? 2GB max RAM- 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00387081&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775#](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00387081&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775#)

No AGP or PCIe, you are stuck with PCI video cards (more expensive than AGP or PCIe, sorry to say).

---

### Post by yetiman64 on 2010-04-01
@cascade9  Thanks, I was led to believe MS only supported current + 1 past OS. Thought w2k dropped of the map in 2008. Will check out the link though. Nev

Chuck, Cascade9 is right on the PCI vid card slot only, but also note to upgrade memory requires replacing the DIMM module,

QUOTE:
Maximum allowed2.0 GB (2 X 1 GB) [COLOR=Blue]requires the replacement of the installed 256 MB DIMM[/COLOR]

To upgrade this machine is starting to look an expensive exercise with the above + PCI vid required. Something to think about here.

Nev

---

### Post by cascade9 on 2010-04-01
I think that is the way that microsoft is moving (apart from the way that there are 'server' OSes...while based on previously released versions). But for a while, they were supporting a lot more the 2 OS- early 2002, there was support for DOS 6.xx, Win95, 98, 98SE, ME, NT4, Win2k, and WinXP (and possibly NT3.51 as well). ;) 

If you want the 'full' 2GB, you will need to replace teh current 256MB stick. But that is a single stick, and you have 2 RAM slots, so you could put in another 128MB, 256MB, 512MB or 1GB stick without replacing the current stick. 

You wont need a video card. Personally, I'm all for them, but as long as you dont want to play games the onboard video should work fine ;) But a even PCI card will run much better at higher resoltions.

BTW, even with 256MB, you should be able to run ubuntu, but its not very nice unless you do the 'alternate install'.....which can be a bit much for a beginner IMO.

---

### Post by yetiman64 on 2010-04-01
@cascade  The 64MB integrated graphics on that machine (with the way ATI support for Linux is Nowadays-being not so good) running 9.10 Karmic with only 256MB RAM doesn't sound too good to me. What is your opinion of that combination with regard to the constant locking up Chuck is reporting.
On swithing to Karmic on a laptop with ATI x1600 (512MB), Intel T2500 duo 2GHz proc. and 2GB of RAM, I suffered a few months of regular lockups (about 4 or 5 a week, but it seems to have settled a lot now with only an occasional hit). I don't think I can even remember locking up under Jaunty though. What is your opinion here do you think it may be related to an ATI + hardware specs.
BTW. I quickly learnt to restart gdm from a tty screen pretty quick to save having to hard power-off. :)   Nev

---

### Post by cascade9 on 2010-04-01
There is no ATI graphics on that computer (as far as I can tell anyway)- its using intergrated Intel 845 video. 

Yes, I agree, 256MB minus something for onbaord video is not good. (Hopefully not 64MB, but I cant recall how much memory you need to run bigger resolutions). 

As for the lockups- I think that at least some of them are related to overheating. I'm guesing that it what the beeping is, its a BIOS beep of 'oh, noes, I is to hot!'. If I'm right, the other 'lockups' are actually just the computer going into 'slow treacle mode'- possibly from thermal throttling. 

I'm pretty ceratin is it hardware related- if Chuck_N is running 256MB minus 64MB for graphics, that is only 192MB- Ubuntu doesnt idle that far below 192MB in almost all cases. If you do anything with that setup, it will start hitting the swap drive pretty heavily, and then its also running onboard video (totally CPU controlled), using onboard sound (more CPU control) and network (even more CPU control). So the system is falling over itself, trying to write to the HDD from RAM, and back again, while also running whatever programs that are open and control the sound, network and video (which is at the end of its ability to output IIRC).  

That is a lot of CPU load. :| 

Of course, I could be wrong....and it is also more than possible that whatever killed the HDD that used to be in the system has 'hurt' something else in the hardware. I've seen that happen before... 

BTW, a neat old trick to see if the system is having overheating problems is to remove the side panel, setup a desktop fan blowing into the case, set it at 'hurricane' (or the highest setting) and then try using the computer. It wont always work, but its not a bad test.

---

### Post by Chuck_N on 2010-04-01
> **cascade9 said:**
> There is no ATI graphics on that computer (as far as I can tell anyway)- its using intergrated Intel 845 video. 

BTW, a neat old trick to see if the system is having overheating problems is to remove the side panel, setup a desktop fan blowing into the case, set it at 'hurricane' (or the highest setting) and then try using the computer. It wont always work, but its not a bad test.



my side panel has been off for weeks. Lubed one fan; they both run fine.
Computer hangs up often immediately after bootup; no heat. Almost every time I boot and go directly to FFox, it hangs while loading FFox, just before the whiteout screen. If I bootup and play a game for 5 minutes, then go to FFox, I'll usually get into FFox okay.    -Chuck

---

### Post by Chuck_N on 2010-04-01
> **yetiman64 said:**
> @cascade9
 Thanks, I was led to believe MS only supported current + 1 past OS. Thought w2k dropped of the map in 2008. Will check out the link though. Nev

Nev

I believe they dropped support for Win2K  just in the last few days.  I don't plan to leave it on for long. It was just convenient for now.  Once I get happy with Ubuntu, I'll reformat the second drive and probably add a third. (they're small old drives, but fit my budget)
  I maybe said this b4; I've never frozen in windows, but I'm not there often.  I'll try to boot there occasionally to see if it won't freeze. Would be disconcerting to find that Win2K can use my low RAM, but not Ubuntu. But that is a possibility; I shouldn't be running with such low RAM.
 -chuck

---

### Post by yetiman64 on 2010-04-01
Chuck, Sorry but it appears I've taken a wrong turn earlier when I saw those ATI links on the HP site (They could've been for a different model).

It now appears that cascade9 is right & I can now only find Intel drivers for your model. What I'd suggest is to physically identify the chip on the M/Bd and check for any identification to be absolutely sure of the hardware before making a decision.

If there are no signs of fan problems then this is a bit strange (overheating would definetly contribute to something like this). I'd consider if there are any other harware faults before forking out money on upgrades.

As cascade9 implied earlier its difficult to tell over the internet for hardware. I'd have someone check all the hardware out now, considering the blown HDD you mentioned (ie. carefully consider cascade9's comments of the last post).

Thanks again **cascade9**

Nev

---

### Post by cascade9 on 2010-04-01
No problems yetiman64 ;) 

> **Chuck_N said:**
> my side panel has been off for weeks. Lubed one fan; they both run fine.
Computer hangs up often immediately after bootup; no heat. Almost every time I boot and go directly to FFox, it hangs while loading FFox, just before the whiteout screen. If I bootup and play a game for 5 minutes, then go to FFox, I'll usually get into FFox okay.    -Chuck

Hmm...to be honest, overheating would explain some of your issues..but it really shouldnt happen in the situation you just posted. 

Honestly, I have no idea of your dl limits, so this might be right out. Ignore this if its unworkable for you. 

I'd try dling a different linux distro. Preferably one that isnt debian based. Not saying that there is anythign wrong with ubuntu, or debain either (I'm a heavy debian user) but its possible that something that isnt playing well with ubuntu will be fine with a different distro. After all, windows works, at least OK, so IMO somethign else should as well. 

Id try puppy linux myself. LiveCD, so you dont have to install it (be warned, it will run more slowly from CD). Not that big a dl as well. 

[http://puppylinux.org](http://puppylinux.org)

[http://distrowatch.com/table.php?distribution=puppy](http://distrowatch.com/table.php?distribution=puppy)

---

### Post by yetiman64 on 2010-04-01
Chuck, 
I tend to agree that if you're game to try Puppy or another much smaller distro off CD. It would be a good way to check the hardware, even if you don't install to the HDD. If that fails, then remember how an earlier poster mentioned w2k being DOS based, is probably why you still have Windows access (even with potentially damaged hardware). It'd be an interesting test.

Nev

---

### Post by Chuck_N on 2010-04-01
> **yetiman64 said:**
> Chuck, 
I tend to agree that if you're game to try Puppy or another much smaller distro off CD. It would be a good way to check the hardware, even if you don't install to the HDD. If that fails, then remember how an earlier poster mentioned w2k being DOS based, is probably why you still have Windows access (even with potentially damaged hardware). It'd be an interesting test.

Nev

okay, I'll try Puppy......
anyone ready to take me by the hand?
I'll go find out what Puppy is and would like to try it this evening.

I booted to windows a while ago, ran a few graphics games; no problems 
in a half-hour or so. Did a few GOOGLE searches; all okay.
-chuck

---

### Post by cascade9 on 2010-04-01
Puppy is pretty easy to run- just put it into your CD/DVD drive, make sure that you are set to boot from CD/DVD drive, and then answer a few questions. Not that hard unless I'm confusing it with something else (which I'm pretty sure I'm not). 

If you have any issue, I'm sure somebody here will help you. 

By the way, when ou go to quit out of puppy, it will give you the option to save your current sesion- you dotn have to do that. It will run fine as a LiveCD, its just faster to boot up, and saves your configuration if you do save its config file. 

Also, its made to run on small RAM systems- so if you do like it, you could think about installing it. It ran really well on my (much slower) pentuim 3 system when I had 256MB of RAM.

---

### Post by Chuck_N on 2010-04-01
> **yetiman64 said:**
> Chuck, 
I tend to agree that if you're game to try Puppy or another much smaller distro off CD. It would be a good way to check the hardware, even if you don't install to the HDD. If that fails, then remember how an earlier poster mentioned w2k being DOS based, is probably why you still have Windows access (even with potentially damaged hardware). It'd be an interesting test.
Nev

okay, I download puppy, then burn an ISO onto a CD,using Graveman I assume,  then reboot the PC and off we go.....    yes?

---

### Post by yetiman64 on 2010-04-01
@cascade9  Could you give Chuck a hand with this please.  I'm doing a dual boot repair at the moment. Thanks Nev.

---

### Post by Chuck_N on 2010-04-01
> **cascade9 said:**
> 

By the way, when ou go to quit out of puppy, it will give you the option to save your current session- you dotn have to do that. It will run fine as a LiveCD, its just faster to boot up, and saves your configuration if you do save its config file. 

.

yes, I was just reading on that; don't save because consecutive boots will get screwed up. 

Do I use Graveman to burn the ISO or is there a better/easier way ?
-chuck

---

### Post by cascade9 on 2010-04-01
Yep,it should be that easy. ;) 

Hopefully it doesnt ask you questions you cant answer easily....dont forget, because its a liveCD, you cant really do much wrong. :)  

BTW, I'm sort of sorry to suggest puppy in some ways, it would be much easier to just go 'do xyz and then your problem is fixed'.....but in my expereince sometiems is easier to try to take a different way around what looks like hardware problems. If you approach them head on, a lot of times you just get a headache. 

Example- between when I posted 1st and now, I've thought of another thing that could be causing the problem- dodgy HDD that ubuntu is installed on. No idea if that is right, or not, but it could be......and if you are sitting around sweating and swearing at computers, its not fun. Easier to do it a different way.

---

### Post by Chuck_N on 2010-04-01
> **cascade9 said:**
> Yep,it should be that easy. ;) 

Hopefully it doesnt ask you questions you cant answer easily....dont forget, because its a liveCD, you cant really do much wrong. :)  


.

okay, if I build ISOPuppy and boot from it, will I be able to go to UbuntuForum, and continue discussion?

---

### Post by cascade9 on 2010-04-01
Yes, you should be able to. 

I think I had to poke the network manager to get puppy to connect to the internet last time I used it- I'm not sure because I tried about 4 different liveCDs around then (testing hardware LOL)

---

### Post by Chuck_N on 2010-04-01
> **cascade9 said:**
> Yes, you should be able to. 

I think I had to poke the network manager to get puppy to connect to the internet last time I used it- I'm not sure because I tried about 4 different liveCDs around then (testing hardware LOL)

everything I'm finding assumes I'm downloading to windows.
do I download the same 4.3.1 , like here:
[http://www.puppylinux.com/download/](http://www.puppylinux.com/download/)

to use Graveman in Ubuntu to burn the ISO ?

I'll be offline for an hour or two.

---

### Post by Chuck_N on 2010-04-01
okay, I have  pup-431.iso  in my Downloads folder.
Now, I think, I am supposed to use WINMD5Sum to verify the download.
I see a text file at the download site referring to WINMD5.
No idea how to do that, although I did it when I built my Ubuntu disk  That
seems like years ago, but really not much over a month.

Then I used K3b to build the Ubuntu disk. I assume I'll do that here, too.

As you can see, I was taking notes along the way.  But I need some help.
In the meantime, I'll go read up on Puppy.
-Chuck

---

### Post by cascade9 on 2010-04-02
Doh....sorry about that, was unexpectedly called away from the internet. 

Anyway, you can check the MD5 checksum. Its never a bad idea...though to be honest with .iso's I mostly don't bother, I only do it when I have problems. 

BTW, I just checked with my (older) version of puppy- to get the internet working I needed to 'Menu-> Setup-> Network Wizard'. Hopefully its as easy with the newer puppy. I'd try seamonkey (or whatever browser comes with the version of puppy you have) before poking at network settings, it might connect automatically these days, or with your setup.

---

### Post by Chuck_N on 2010-04-02
I too have lots of other things to accomplish, so will be working on this periodically.

I've thought this through a bit.  When I built my Ubuntu(download ISO, checksum, K3b CD-create, I was on my old laptop. I'd prefer to try this within Ubuntu, now, here.  But most of the info I'm finding on the web gives instructions relating to Windows download/checksum/create CD.
Can we get the job done here, within Ubuntu? I should think so.....

Looks like this source  [http://www.minihowto.org/k3b_howto/k3b%20cd%20dvd%20burning%20minihowto.html]("http://www.minihowto.org/k3b_howto/k3b%20cd%20dvd%20burning%20minihowto.html")
should walk me through k3b and checksum to create cd from my present ubuntu environment.  I'll try it.

---

### Post by cascade9 on 2010-04-02
That k3b page is right. ;)  

Btw, you dont have to dl the md5 checksum- firefox will open it, if  you want just check from between the firefox window and K3b. 

Hmm, maybe I should send a suggestion to the K3B developers about MD5 checksumming. It would be handy. I had better have a poke around with K3B 1st, I would feel really silly if there is a way to check the MD5 in K3B without doing it manually. LOL

---

### Post by yetiman64 on 2010-04-02
@cascade9 Whenever I dwnld an iso. I open the md5 online with ffox, copy and paste it into a text file on my desktop.

Then goto the terminal and run

```
md5sum ~/Desktop/<filename>
```Note I dwnld all files to my desktop.

Then copy and paste the terminal output to the text file directly under the 1st.
If the 2 are identical then the dwnld is perfect and can be right clicked on and burnt (Brasero in Ubuntu or whatever is the default burner elsewhere.)  Hopes this helps.

Edit: I realize this is manual way and Just noted the end of 
> MD5 in K3B without doing it manually. LOL
But it is good to learn how system commands do things even for new users.  Nev

---

### Post by egalvan on 2010-04-02
> **cascade9 said:**
> 
I'd try dling a different linux distro. Preferably one that isnt debian based. 
. After all, windows works, at least OK, so IMO somethign else should as well.

Yeah, Microsoft isn't all that great at finding hardware faults.


> 
Id try puppy linux myself. LiveCD, so you dont have to install it (be warned, it will run more slowly from CD). Not that big a dl as well. 


Puppy loads totally in RAM if it finds at least 256M free...
but the video will obviously take some of that...

I run puppy all the time on older machines, with only 256M sticks...
it simply flies.

Another mini-distro that I use all the time for actually setting up machines is PartedMagic LiveCD.
Very small download, and runs well in 256M
(I am on a subscription donation plan)

[http://partedmagic.com/](http://partedmagic.com/)


And for the smallest download of them all try...

Tinycore Linux
[http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)

it's at 11Meg for now.... yes, ELEVEN MEGABYTES.

Try it, it's astonishing.

as for a good ISO burner under Windows, you simply cannot go wrong with imgburn.
(I donated to this author)

[http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by egalvan on 2010-04-02
> **Chuck_N said:**
> [QUOTE=egalvan;9059025]

Also, is there ANY indication of activity while the computer is "frozen",
 such as lights flickering or the fan changing speeds, or hard-drive activity?

[COLOR=Red]no lights; no fan; nobody home
**harddrive light bleeps lightly, once a second or so.....**
[/COLOR]

OK, just caught this while trying to play catch-up...

If the HD light is blinking, it is doing SOMEthing with the drive I/O...

How big is the swap partition?

Honestly, I'm suspecting more and more that this is memory starvation...

PLEASE, run top (or better, htop) and post the results 
(screen-shot)

---

### Post by Chuck_N on 2010-04-02
> **egalvan said:**
> [QUOTE=Chuck_N;9059991

If the HD light is blinking, it is doing SOMEthing with the drive I/O...

How big is the swap partition?

Honestly, I'm suspecting more and more that this is memory starvation...

PLEASE, run top (or better, htop) and post the results 
(screen-shot)



1) I am a Ubuntu novice;  top?  htop?  screen-shot?   I'll look for htop in Apps, and assume screen-shots can be done somewhere; some utility
2) this is a 6-wk old  Ubuntu setup;  I have no idea what the swap            partition size is, or if one was set up. or where to check it, yet.
3) fixing memory starvation may be easier than the PUPPY route; I will
    pursue this now and get back to PUPPY later.
4) sure glad I'm retired; I don't know how I ever found time to work.

---

### Post by Chuck_N on 2010-04-02
[SIZE=4]okay, I am trying to learn....
I'm following instructions at  [http://www.howtogeek.com/howto/ubuntu/using-htop-to-monitor-system-processes-on-linux/](http://www.howtogeek.com/howto/ubuntu/using-htop-to-monitor-system-processes-on-linux/)
I did   alt-f2   xterm     sudo apt-get install htop   and got an install report;[/SIZE]
 

 [SIZE=4]I'm typing this in WRITER and saving after each change, in case I get a freezeup.[/SIZE]
 [SIZE=4]Well, that's cute; Writer just closed. I had to recover this document.[/SIZE]
 

 [SIZE=4]Instructions say I can type htop at a terminal to launch it; I just noticed that it is a new entry under  Applications/ system tools   also.  Okay, I ran it.  I see it is not a static report; it is dynamic; updating continually.  [/SIZE] 
 

 [SIZE=4]Okay, at this point Writer closed again. I recovered this file.[/SIZE]
 

 [SIZE=4]I just did some GOOGLing and found a way to get a screenshot;  applications/ accessories/ take screen shot.  I'll go back and try that.  Don't know what to do with it after I shoot it though; I'll assume I can paste it here:[/SIZE]
 

 [SIZE=4]writer closed again; I recovered[/SIZE]
 

 [SIZE=4]I copied to clipboard; here it is:    nope, it would not paste  nor  paste special[/SIZE]
 

 [SIZE=4]I saved the screenshot  png image   on the desktop.  I'll copy all this to the forum and see if I can attach the  PNG image there.....[/SIZE]
 

 [SIZE=4]oh great I got to the forum; tried to paste this document in, and Ffox closed. Sure glad I'm keeping my text here in Writer.[/SIZE]
 

 [SIZE=4]Darn, now I had a freeze.  Rebooted, recovered this Writer document. 
[/SIZE]


[SIZE=4]okay, back in forum; pasted this document. found attachments; opened the attachment window[/SIZE]
[SIZE=4](whoops, what is it I'm supposed to call a window now, a frame?).....  at any rate if I take my cursor off that window, it goes behind the forum window, I can retrieve it by clicking on the Manage Attachments on the task bar; troublesome. I think I got it done; I'll send it now   Let me know what this shows, or if I need to do something to make the report better.....
[/SIZE]


[SIZE=4]
[/SIZE]

---

### Post by Chuck_N on 2010-04-02
Hope I'm not swamping you with information.

I have a file FotkyJ04.pps   on the desktop. Properties indicate 38K.

if I doubleclick, nothing happens.
if I rightclick, choose open with OOPresentation, nothing happens.
if I open OOPresentation, choose  Open desktop/FotkyJ04.pps .....
    nothing happens.

  I know I viewed it recently. I think it was a WWII presentation.

---

### Post by Chuck_N on 2010-04-03
okay, I had a thought:  let's get up and running with Yahoo in FFox, then start Opera (I've never run them both at the same time b4) and generate another Htop.  On starting Opera, it froze the system and generated onscreen vertical black and red bars.  

So I rebooted, started Opera first, then FFox and got it running okay. Generated a Htop which is attached.     -Chuck

---

### Post by Chuck_N on 2010-04-03
I started Presentation
then tried to open fotkJ01.pps again
it still did not open
then I ran Htop
sorted by Virt column
and took a new screenshot (attached)

I have some idea what we're doing here,
but have not enough background to interpret this data
or plan an attack.

---

### Post by Chuck_N on 2010-04-03
downloaded a different .pps   asked for it to run.
Presentation opened, showed only the first slide
blew up
froze.

---

### Post by Chuck_N on 2010-04-03
[COLOR=Red]> **egalvan said:**
> 

Seriously, 256M RAM is extremely border-line for a GUI-heavy OS,
and running your video at 1600X900 is really stressing it.

[/COLOR]   

should I try dropping down my video resolution? 
 I am thinking now how running Opera yesterday brought a vertically-striped screen, 
which makes it sound like video troubles.

I have a Dell Drivers and Documentation disk which I have not used at all.

When I alternate-boot to windows, I have terrible resolution; should I install the monitor in windows? Could 
it help in Ubuntu, if I did? I doubt it.

Unfortunately, I do not remember if I was having freezing problems when I was using
my wife's old flatscreen, temporarily, b4 this Dell screen arrived.

-Chuck

---

### Post by Chuck_N on 2010-04-03
I opened Presentation.  It wanted to do a recover.  It recovered the
PPS file that blew up yesterday (and gave vertical red-black bars).
This time the file ran.  On completion, I got an error window which said the file will be recovered.  I said okay. Presentation then shut down.
Restarted Presentation. Asked for the file again. Presentation started recovery routine. The file then ran and shut down okay.

---

### Post by Chuck_N on 2010-04-03
I have a folder of JPGs. Rightclick on one, choose Open With F-Spot. A small window opens. Then a larger one, identifying the F-Spot program. Then everything goes away.
 Or I go to Applications/Graphics/F-SpotPhotoManager the same thing happens: small window, big window, gone.

I guess what I'm seeing is most all of my applications blow up; especially if they have much to do with graphics.

---

### Post by Chuck_N on 2010-04-03
okay, I backed off my resolution two levels, to 1024X768.
Everything is bigger and fuzzier but not bad.
Downloaded a picture 1600X1200 and it opened beautifully in
Viewer and also in F-Spot. Remember, F-Spot would not even run b4.

We're on to something here......  maybe I DO need to install this monitor.
I would prefer to get back to 1024X768. This seems harder on my eyes.

EEEK...........  I changed the resolution back to 1600X1200 and now I can open that same picture
in  GIMP Image Editor  and with  ImageViewer  and, would you believe also with F-Stop.  I did
it four times just to confirm it was not a fluke.  Now what..........?

Downloaded another 1600X1200 pic and F-Spot opens it just fine.  Weird thing I notice now,
on the desktop the first pic no longer has a miniature pic showing; it says JPG instead. 
I opened and closed it a couple times and it's staying that way.   Note: the pic returned some time later.

I now have 4 windows open in FFox, Nibbles, F-Spot, GIMP Image Viewer all running at the same time.
No troubles. I ran another Htop but can't do an attachment in an edit.  will send in new message.
Lots of weird stuff.

---

### Post by Chuck_N on 2010-04-04
here it is

---

### Post by Chuck_N on 2010-04-04
jeez, I still had all that stuff running
plus terminal and screencopy

and then asked for a Presentation file to run

it tried, couldn't make it. But no freeze.

I closed terminal and screencopy.

then ran the Presentation with no problem.

For whatever reason, the system seems so much more stable these
past few hours......

---

### Post by Chuck_N on 2010-04-04
Happy Easter.

got up this morning, booted, and smugly went direct to FireFox
(I thought all my problems had disappeared)
and ran fine for an hour...........

then a freeze, out of nowhere. Harddrive light blinking lightly every
couple seconds, just like b4,

rebooted, tried FireFox.  Froze before first whitepage. Like b4.

rebooted, tried again.  Got in.

Sure was operating fine for a few hours.

---

### Post by Chuck_N on 2010-04-06
I'll be out of town wed. the 7th through Sunday. I hope to get back
to this problem computer Monday the 12th and get to work on resolving
these issues.  I hope I have some response from Egalvan by that time.

---

### Post by cascade9 on 2010-04-06
1600x1200 realy makes the video on intel 845 chipsets crawl in my expereince. That will be adding to your CPU usage, and could be part of what is causing your machine to freeze. 

Swap use is way higher than I like, but I'd like to see what Egalvan says. 

BTW, part of why I suggest puppy (any liveCD distro that is pretty light would do) is because there is always the chance that your HDD is whats freezing, and your computer is trying to write to swap and unable to. Using something that runs totally off RAM would mean that is just not possible.

---

### Post by Chuck_N on 2010-04-06
[COLOR=Red]> **cascade9 said:**
> 1600x1200 realy makes the video on intel 845 chipsets crawl in my expereince. That will be adding to your CPU usage, and could be part of what is causing your machine to freeze. 

Swap use is way higher than I like, but I'd like to see what Egalvan says. 

BTW, part of why I suggest puppy (any liveCD distro that is pretty light would do) is because there is always the chance that your HDD is whats freezing, and your computer is trying to write to swap and unable to. Using something that runs totally off RAM would mean that is just not possible.[/COLOR]  

hi cascade,
thanx for your observations. I will pursue the PUPPY possibility soon as I get back in town.   -Chuck

---

### Post by egalvan on 2010-04-07
Sorry for the delays in my posts, I go to the firehouse every third day...

> **cascade9 said:**
> **1600x1200 realy makes the video on intel 845 chipsets crawl in my expereince**. That will be adding to your CPU usage, and could be part of what is causing your machine to freeze.

Yep, I think that that super-high resolution is stealing too much RAM and cpu cycles...

> Swap use is way higher than I like, but I'd like to see what Egalvan says. 

Again, I agree 100%. I don't know what kind of cpu he's running, or what kind of chip-set... some of those can be a potently slow combo..
RAM and disk I/O is shared, and that is S-L-O-W.


> BTW, part of why I suggest puppy (any liveCD distro that is pretty light would do) is because **there is always the chance that your HDD is whats freezing, and your computer is trying to write to swap and unable to.** Using something that runs totally off RAM would mean that is just not possible.

And a third time, 100% agreement. Same reason I have...
Using a RAM-resident distro will isolate the drive I/O issues from the RAM issues..

And again, 256M RAM is awfully small for a modern GUI-centric distro...

And an older drive is probably 4200RPM (or less), and it's seek times are probably on the low side.

Just to be mean...
I wonder what Vista would do on this machine :lolflag:

---

### Post by cascade9 on 2010-04-07
Just out of intrest, the hardware is this from what I can find- 

Celeron 340 (2.93Ghz), 256MB DDR1, Intel 845 chipset and video, 80GB 7200RPM. Though Chuck_N said there are 2 drives, and I haev no idea what the 2nd drive is, or what OS is on what drive. 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00387081&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00387081&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775)

As for vista- it would throw its little arms up and say 'I'm not installing on THAT" I think- notenough RAM,and the video doesnt support DX9.

---

### Post by egalvan on 2010-04-08
> **cascade9 said:**
> Just out of intrest, the hardware is this from what I can find- 

Celeron 340 (2.93Ghz),
 256MB DDR1,
 Intel 845 chipset and video,
 80GB 7200RPM. 

That Celeron D Prescott-256 is fairly low-end...

---------
Celeron D (Prescott)

    * » Netburst microarchitecture
    * » Budget desktop CPU
    * » Up to 3.46 GHz
    * » 533 MHz FSB
    * » 256 KB L2 cache
    * » 64-bit
    * » Execute Disable bit
    * » SSE3

Socket 478
Socket 775
--------------

This is what he should try for...

Prescott
    * » 0.09 micron
    * » Up to 2 MB L2 cache
    * » 64-bit processing
    * » Execute Disable bit
    * » SSE3
    * » Virtualization
**[COLOR="Red"]Pentium 4[/COLOR]**
Celeron D
Mobile Pentium 4

Lots of those P-4 2GHz-3GHz with 1Meg Cache floating on eBay, 
and dirt cheap, too.
I've bought some (2.8GHz) for $20 shipped.

Here is a sampling of current eBay stuff

[http://cgi.ebay.com/Intel-Pentium-4-2-8GHZ-1MB-533-SL7PK-Socket-478_W0QQitemZ180470636395QQcmdZViewItemQQptZCPUs?hash=item2a04e35f6b](http://cgi.ebay.com/Intel-Pentium-4-2-8GHZ-1MB-533-SL7PK-Socket-478_W0QQitemZ180470636395QQcmdZViewItemQQptZCPUs?hash=item2a04e35f6b)

[http://cgi.ebay.com/Intel-Pentium-4-2-80GHZ-512KB-800-SL6WJ-Socket-478_W0QQitemZ180455337065QQcmdZViewItemQQptZCPUs?hash=item2a03f9ec69](http://cgi.ebay.com/Intel-Pentium-4-2-80GHZ-512KB-800-SL6WJ-Socket-478_W0QQitemZ180455337065QQcmdZViewItemQQptZCPUs?hash=item2a03f9ec69)

[http://cgi.ebay.com/Intel-Pentium-4-2-8GHZ-1M-800-SL79K-Socket-478_W0QQitemZ170454560456QQcmdZViewItemQQptZCPUs?hash=item27afe22ec8](http://cgi.ebay.com/Intel-Pentium-4-2-8GHZ-1M-800-SL79K-Socket-478_W0QQitemZ170454560456QQcmdZViewItemQQptZCPUs?hash=item27afe22ec8)

The first is if your mobo does not like 800Mhz bus chips...
I would be surprised if this were true...
(maybe I should find out what the supported bus speeds are??)

The  second is better, and third is the best deal.

The 2Meg Cache ones aren't too bad in price, usually up around $35-$50.

These CPU upgrades will speed up the machine very well.
**NOT** as well as a RAM bump to at least 512M,
better to 1GB



> 
Though Chuck_N said there are 2 drives,
 I haev no idea what the 2nd drive is,
 or what OS is on what drive. 

As for vista- it would throw its little arms up and say 'I'm not installing on THAT" I think- notenough RAM,and the video doesnt support DX9.

---

### Post by cascade9 on 2010-04-10
> **egalvan said:**
> The first is if your mobo does not like 800Mhz bus chips...
I would be surprised if this were true...
(maybe I should find out what the supported bus speeds are??)

These CPU upgrades will speed up the machine very well.
**NOT** as well as a RAM bump to at least 512M,
better to 1GB

Intel 845 chipsets never support 800Mhz FSB. 865/875 chipsets were the 1st Intel chipsets to do that. 

I wouldn't even think about upgrading the CPU in that machine until after a RAM upgrade.....and even then I probbaly wouldnt. Maybe, just maybe, if the crashing/freezing problem was dianosed or fixed I would consider it, but I'd be more likely to get a video card 1st to be honest. 

Celeron 340 is hardly 'high end' but they are still pretty fast, its the RAM and lackluster intel video that is really holding that machine back.

---

### Post by egalvan on 2010-04-11
> **cascade9 said:**
> Intel 845 chipsets never support 800Mhz FSB. 865/875 chipsets were the 1st Intel chipsets to do that. 

I wouldn't even think about upgrading the CPU in that machine until after a RAM upgrade.....and even then I probbaly wouldnt. , but I'd be more likely to get a video card 1st to be honest. 

**Celeron 340** is hardly 'high end' but **they are still pretty fast**, its the RAM and lackluster intel video that is really holding that machine back.

That first CPU I linked to is...

Intel Pentium 4 2.8GHZ / 1MB / 533 SL7PK Socket 478

The cache is probably eight ( 8 ) times bigger, and the Celeron is much less efficient in the register/memory controller departments also...
Overall, many improvements in the `quickness` side of things...

He WILL feel a difference...
And for $15, it´s rather cheap.

**But** as I stated, and others, including you,,,
more RAM will give a bigger boost.

A better video card will also give a good boost.


And finally...
Yeah, that Celeron **is fast**, but **it´s not very quick**...
That P4 is** not as fast**, but´s **it´s light-years quicker.**

---

### Post by linux_tech on 2010-04-11
> **Chuck_N said:**
> "Hardware drivers" tells me I have no proprietary drivers.
How do I find out if I have an NVIDIA card?
In terminal typing  

lspci | grep VGA

-  this will give you the video card info

System>Administration>Hardware drivers will show you the driver version

---

### Post by cascade9 on 2010-04-12
> **egalvan said:**
> And finally...
Yeah, that Celeron **is fast**, but **it´s not very quick**...
That P4 is** not as fast**, but´s **it´s light-years quicker.**

Faster? Agreed. 'Light-years faster'? LOL, no. 

Cache is 4 times bigger (256k celeron, 1024k P4) and from what I know they are the same basic desgin so the register and memory is pretty much the same. 

Not a bad upgrade, I admit, but without extra RAM is still going to be slow. 

I was never a fan of the P4s myself, and the celerons even less so.

---

### Post by egalvan on 2010-04-12
> **cascade9 said:**
> Faster? Agreed. 'Light-years **faster**'? LOL, no. 

Faster? No, I said **QUICKER**


> Cache is 4 times bigger (256k celeron, 1024k P4) and from what I know they are the same basic desgin so the register and memory is pretty much the same. 

Oops, got the wrong family... yep, it has a 256K cache...
as to *they are the same basic desgin so the register and memory is pretty much the same*
nope, the Celeron is much less effiecient...
Much cheaper for Intel to fab.

> Not a bad upgrade, I admit, but without extra RAM is still going to be slow. 

Yep, it will stil be slow, but it will feel quicker...
That CPU will let him wring out the most from that platform.

> I was never a fan of the P4s myself, and the celerons even less so.

The Prescott P4 was a decent architecture.
Especially the Mobile cousins.
I`ve got a rare P4-M with 4M cache on an IBM ThinkPad 41P.
Yes, it´s MUCH quicker than the 128K cache Celeron the original owner had swapped out before selling it to me.

I have never liked the Celeron, or the Duron, or any artificially throttled piece of hardware...
remember the 386X/486X, or the Celeron 300?

---

### Post by cascade9 on 2010-04-13
> **egalvan said:**
> Faster? No, I said **QUICKER**

:| LOL

> **egalvan said:**
> Oops, got the wrong family... yep, it has a 256K cache...
as to *they are the same basic desgin so the register and memory is pretty much the same*
nope, the Celeron is much less effiecient...
Much cheaper for Intel to fab.

Cheaper because they ripped the cache out of it (easier to make, less errors, more CPUs per wafer) but as far as I know they use the same registers, etc, on them. 

> **egalvan said:**
> 
Yep, it will stil be slow, but it will feel quicker...
That CPU will let him wring out the most from that platform.

After going to 512MB+, it might be...but IMO that system is severly RAM short, and from my expereince I'd rather have a slower CPU with enough RAM than a faster CPU strangled by RAM shortages. 

> **egalvan said:**
> 
The Prescott P4 was a decent architecture.
Especially the Mobile cousins.
I`ve got a rare P4-M with 4M cache on an IBM ThinkPad 41P.
Yes, it´s MUCH quicker than the 128K cache Celeron the original owner had swapped out before selling it to me.

P4-M with 4MB? Never heard of such a beast. All the P4-Ms I've ever seen were 512k/1024k cache. Thats all I can find with Intel as well... 

[http://processorfinder.intel.com/List.aspx?ParentRadio=All&ProcFam=826&SearchKey=](http://processorfinder.intel.com/List.aspx?ParentRadio=All&ProcFam=826&SearchKey=)

Even the P-M (which was a rejigged P3 with P4 FSB, SSE2 and a few otehr core improvments) only went to 2MB as faras I know. 

If you've got a link to info on this CPU, I'd like to see it. A P4-M, or P-M with 4MB should be a rocketship :) 

> **egalvan said:**
> 
I have never liked the Celeron, or the Duron, or any artificially throttled piece of hardware...
remember the 386X/486X, or the Celeron 300?

I think you mean 386/486SX (which were quite different, only really connected because they were both cut-down versions....IIRC the 486SX was a DX chip with the pin linking to the FPU cut off! LMAO). 

I've used celeron 300a CPUs, they actually werent that bad. I know of several that lived in dual CPU systems and they went pretty well actually...better than if you spent the same amount of money on a P2-300 ;)

---

### Post by egalvan on 2010-04-14
> **cascade9 said:**
> :| LOL

 but as far as I know they use the same registers, etc, on them.
 

Nope, on the P4 (and earlier) family, the Celerons were different platforms.

>  After going to 512MB+, it might be...but **IMO that system is severly RAM short,** 

to which I have heartily agreed, which is why I attempt to max out RAM on my machines, and suggest to others as a good start...

BUT swapping out Celerons (or Durons/(older)Semprons) is also a very high priority for me.
Those are just crippled platforms.
And a true P4 will wring out the max on the machine, no matter HOW much RAM...or how little... it will get the most use of *what is there*...
but the more RAM, the better it will be used...
To which we have agreed...


>   and from my expereince I'd rather have a slower CPU with enough RAM than a faster CPU strangled by RAM shortages.  

again, agreed. I feel the same...
but in this case, the CPU upgrade can be dirt cheap,
and he may ( or may not ) find the RAM to be pricier...
Old/obsolete RAM prices to be be crap shoots...

"It's old and rare, so it's worth a lot"
"It's obsolete, so let's toss it"

I've heard, and seen the prices, for both sides :)

>  P4-M with 4MB? Never heard of such a beast. All the P4-Ms I've ever seen were 512k/1024k cache. Thats all I can find with Intel as well...  

Very rare beasts, and to the Thinkpad 60P contingent, it was considered the ultimate upgrade...
[/quote] 

>  Even the P-M (which was a rejigged P3 with P4 FSB, SSE2 and a few otehr core improvments) only went to 2MB as faras I know. 

The P-M was much more than a "rejiggered" P3, it was a whole new family, MUCH more efficient in terms of speed, cache, and TDP (heat)


>  If you've got a link to info on this CPU, I'd like to see it. A P4-M, or P-M with 4MB should be a rocketship :)  

It's been a couple of years since I stopped using my TP-60P, and I haven't visited the forums in a coon's age... I'll see what I can dig up.

And yes, they *were* rocket-ships, with prices to match :)
At the time that a TP-60/60P could command $600-$700 in "As-New" condition, those 4M cache chips would bring $350-$400.
Mighty steep up-grade :)
Bang-for-the-buck, it was better to max out your RAM to 4GB.

> I think you mean 386/486SX (which were quite different, only really connected because they were both cut-down versions....IIRC the 486SX was a DX chip with the pin linking to the FPU cut off! LMAO).  

Actually, I meant the 386**SX**486SX, sorry.
The SX meant that it had no functioning FPU.
The DX were higher-clocked versions, of which AMD had a better version.

> I've used celeron **300[COLOR="Red"]a[/COLOR]** CPUs, they actually werent that bad. I know of several that lived in dual CPU systems and they went pretty well actually...better than if you spent the same amount of money on a P2-300 ;)

Which is why I mentioned the **Celeron 300**  (notice no  **[COLOR="Red"]a[/COLOR]**).

That was a Celeron with NO CACHE.. it was an absolute dog...
The P-2 blew it out of the water, even though the P-2 was in some ways inferior.

Then there was the "B-line-cut" trick to getting that 300a to over-clock.
Certain Slot-1 300a's could have one of the pins cut, which would allow it to over-clock with very high reliability...

The 300a cache ran at core speed, on-wafer, but was smaller.
The P-2 had more cache, but it ran at half core speed, and was off-wafer.

Yeah, the "power-users" of the day dreamed of **dual 300a's** o-c'd,
running on a dual-cpu aBit board...
The clock speeds were in the 400-600Mhz range...
real "super-computer" stuff... :)

the later 300's all had cache, but were much more limited in o-c ability.

------------------------

I guess what I am trying to say is; if he can upgrade the RAM to 512M for $15, then yes, it's $15 better spent....
his machine will feel far quicker, much more responsive, 
due to much less time paging to the hard drive.

*But* he may find that RAM to be dearer than that...
it's a crap-shoot, as I said... luck of the draw.

He'll have to go snipe hunting :P

So for the $15, that Celeron-to-P4 is a good bargain... it will max out the *use* of the 256M he does have, as the CPU is more efficient, and quicker.
And I grant that the difference will *not* be as dramatic as the RAM upgrade.

---

### Post by egalvan on 2010-04-14
So where's Chuck_N???

His week's "vacation" from us is up.

I hope we haven't scared him off :lolflag:

---

### Post by cascade9 on 2010-04-15
Were Chunk_N is?.....I dont know. Hopefully he comes back. 

Chunk_N, if you your around...dont worry about me and egalvan talking hardware. I cant be sure about egalvan, but I personally love to talk hardware (I'm guessing egalvan does as well). We'll go back to trying to help if you reappear! :) 

> **egalvan said:**
> Nope, on the P4 (and earlier) family, the Celerons were different platforms.

 We may just have to disagree on that, and just agree on the whole 'crippled chips = lame'

to which I have heartily agreed, which is why I attempt to max out RAM on my machines, and suggest to others as a good start...

BUT swapping out Celerons (or Durons/(older)Semprons) is also a very high priority for me.
Those are just crippled platforms.
And a true P4 will wring out the max on the machine, no matter HOW much RAM...or how little... it will get the most use of *what is there*...
but the more RAM, the better it will be used...
To which we have agreed... 

Same platform, just they cut the cache from everything I've ever seen (and that was to get more dies per-wafer and so they had some cheaper chips to compete with AMD in particular, and cyrix to begin with). 

There was a celeron variant for several of the P3s (and most of the P4s). The original 'covington' (266, 300) and then the 'mendicino' (300a to 533) celerons were just from the same 'p6' family, they were different designs- in some ways the mendicino was a prelude to the 'coppermine' p3s, as they had the on-die cache. 

I tend to do the same, if I can, swap out celerys, etc, to the non-crippled models. Sometimes I have no choice but to use them though... 
 
> **egalvan said:**
> 
again, agreed. I feel the same...
but in this case, the CPU upgrade can be dirt cheap,
and he may ( or may not ) find the RAM to be pricier...
Old/obsolete RAM prices to be be crap shoots...

"It's old and rare, so it's worth a lot"
"It's obsolete, so let's toss it"

I've heard, and seen the prices, for both sides :)  

Same here. RAM prices can be...funny at times. 
Reminds me, I really should try to sell off the 128MB ECC EDO I have sittign around here, UI'm never going to use it and I might get some decent price for it. 

> **egalvan said:**
>  

Its possible that they were never 'offical' chips, but sold engineerign samples. I've seen a Athlon XP 'mustang' (1MB cache) that was never offically sold. 
 
[QUOTE=egalvan;9124164]
The P-M was much more than a "rejiggered" P3, it was a whole new family, MUCH more efficient in terms of speed, cache, and TDP (heat)

'Rejiged' might have been pushing it, I agree. Maybe 'major upgraded' or 'based on the p3, not the P4' would be closer to the truth. They were much better chips than the P3s (not that the P3s were bad) and had a lot of improvements. 

> **egalvan said:**
> 

For the 486SX/DX, yes. IIRC the 386SX was a 16bit data bus, where the DX was 32bit. I could be wrong on that, I havent used, or even seen, a 386 for many years ow.. 

[QUOTE=egalvan;9124164]
Which is why I mentioned the **Celeron 300**  (notice no  **[COLOR=Red]a[/COLOR]**).

That was a Celeron with NO CACHE.. it was an absolute dog...
The P-2 blew it out of the water, even though the P-2 was in some ways inferior.

Then there was the "B-line-cut" trick to getting that 300a to over-clock.
Certain Slot-1 300a's could have one of the pins cut, which would allow it to over-clock with very high reliability...

The 300a cache ran at core speed, on-wafer, but was smaller.
The P-2 had more cache, but it ran at half core speed, and was off-wafer.

Yeah, the "power-users" of the day dreamed of **dual 300a's** o-c'd,
running on a dual-cpu aBit board...
The clock speeds were in the 400-600Mhz range...
real "super-computer" stuff... :)

the later 300's all had cache, but were much more limited in o-c ability.

Opps, sorry about that, I just assumed that you meant the 300a's. Most people I see talking about 300s mean 300a's, and a lot of  people forget (or nevwer even knew) that there was a '300'. They were never as common as the 266 (which, as an aside, I still have about 5 heatsinks from...they make good passive HDD coolers). 

Agreed, the 266/300s were really, really bad. I know 2 people who got badly burnt by them, one person traded in his 233MMX for a 'faster' 266 and was very upset that it was slower than the machine he replaced, and actually went back to the store to try to return it, and get his old machine back..they insisted that it was faster, and that he actually needed to 'upgrade' to winME to 'make use of the more powerful chip'. (yes, they sold hima  266 in early 2000...must have been old stock or something). I now build his machines for him because of that, so I cant really say it worked out badly for me. 

[QUOTE=egalvan;9124164
I guess what I am trying to say is; if he can upgrade the RAM to 512M for $15, then yes, it's $15 better spent....
his machine will feel far quicker, much more responsive, 
due to much less time paging to the hard drive.

*But* he may find that RAM to be dearer than that...
it's a crap-shoot, as I said... luck of the draw.

He'll have to go snipe hunting :P

So for the $15, that Celeron-to-P4 is a good bargain... it will max out the *use* of the 256M he does have, as the CPU is more efficient, and quicker.
And I grant that the difference will *not* be as dramatic as the RAM upgrade.[/QUOTE]

I've got plently of DDR1 hanging around. Last check I had about 4.5GBs of the stuff (1x1GB, 5x512MB, 4x256MB) If Chuck_N cant find some cheap RAM, somehwere.....I'd send him some. 

BTW, dont get me wrong, I'd wouldnt suggest (in most cases) that a celeron to 'full' chip (be it P3, P4, or Core2) is a bad idea.

---

### Post by Chuck_N on 2010-04-19
[COLOR=Red][QUOTE=cascade9;9125212]Were Chunk_N is?.....I dont know. Hopefully he comes back. 

Chunk_N, if you your around...dont worry about me and egalvan talking hardware. I cant be sure about egalvan, but I personally love to talk hardware (I'm guessing egalvan does as well). We'll go back to trying to help if you reappear! :)[/COLOR]  

 
sorry guys, my one trip turned into two. just got home and I see I have a lot of reading to do to get caught up.  No, I haven't given up, and I'm glad to see you haven't either.  I'll not have much time for a few days now either; have to take my wife to the doctor and quite possibly some surgery soon. But I'll get back to this soon.  The RAM will be installed soon too.
[COLOR=RoyalBlue]
HOWEVER, I just got a new insight. I don't think the computer is freezing; I think it's just the mouse.  For weeks, whenever the mouse froze and I saw no harddrive activity, I assumed the computer was froze. So I'd power-off.  Today it froze once, and I noticed that I could page-down and -up and read my document. And when I unplugged the USB Basic Optical Mouse, and plugged it back in, I'm off and running 
[/COLOR][COLOR=RoyalBlue][COLOR=Black]Nah, that wasn't right. I need to get back into this again. Yes, the mouse froze last night. That was a related, but different problem. Actually, I think, the first time that had happened.  
 Got up this morning, ran a while, and then the same old problem came back. Mouse moved fine, but nothing could be done. No rightclicks, no leftclicks, etc. I should have disconnected/reconnected the mouse then. But I rebooted. Could be I just think the screen is frozen, but the mouse is not doing anything except moving. I'll try next time....[/COLOR][/COLOR]
[COLOR=RoyalBlue] 
[COLOR=Black]


[/COLOR][/COLOR]

---

### Post by cascade9 on 2010-04-20
> **Chuck_N said:**
> sorry guys, my one trip turned into two. just got home and I see I have a lot of reading to do to get caught up.  No, I haven't given up, and I'm glad to see you haven't either.  I'll not have much time for a few days now either; have to take my wife to the doctor and quite possibly some surgery soon. But I'll get back to this soon.  The RAM will be installed soon too.

Ouch. :( Good luck with the doctor stuff. ;)  

Got RAM? That will make a big difference. :) 

> **Chuck_N said:**
> 
HOWEVER, I just got a new insight. I don't think the computer is freezing; I think it's just the mouse.  For weeks, whenever the mouse froze and I saw no harddrive activity, I assumed the computer was froze. So I'd power-off.  Today it froze once, and I noticed that I could page-down and -up and read my document. And when I unplugged the USB Basic Optical Mouse, and plugged it back in, I'm off and running again.
   I have tried 2 or 3 different mice, a different keyboard too, but never INSTALLED a mouse; just plugged them in. Could be that's my main problem. How do I INSTALL it?

Thatcould very well explain everything. Hardware, sometimes it is like that....

You dont really need to install mice, keyboards, etc., just plug them in and go (BTW- hotpulgging USB is OK, but you shouldnt do it with PS2) Changing the keyboard layout is the closest thing to installing with linux.

---

### Post by Chuck_N on 2010-04-29
very busy otherwise, but I got back to this for a while.........

ordered 512 meg ram from Crucial. Replaced 256 meg with the 512. WOW..... what a difference.  Everything noticeably faster. To suggest that 256 is a minimum configuration is like suggesting that one purchase a car with one seat, no windows, top speed of 45 and which tips often in curves.
Not a good way to go.

Anyways, it ran for an hour or two with no freezing problems. I thought "whoopee, all is now fine."  Then it froze, as before. I can see no pattern to the freezing. It has since frozen on  bootup, occasionally, as b4. 

So I added the 256 back in, and will run with 768, looking for freeze-up cause.  At this point I suspect either video (I'll install a video card soon), or my operating system, or the processor (which I assume would be a dead-end for this computer).   

Any suggestions?

thanks, chuck

---

### Post by cascade9 on 2010-05-01
so, you tried unplugging the mouse and pluging it back in again, and control from the keyboard? If that failed....then yes, its not just the mouse thats causing the freezes. 

Sometimes I wish that when there was a hardware problem, it would just be one thing, not half a dozen. Oity that the hardware tneds not to agree with me. Makes troubleshooting much harder. :(

---

### Post by Chuck_N on 2010-05-01
hi,
yes, I guess you guys DID get off on the hardware angle for a while   8-)

I acquired this computer with a blown HD.  A techy friend gave me a few old HDs. We installed two, the primary with Ubuntu, the secondary with an old Win2K. If I hit ESC when booting, I can get to the Windows boot.

Both harddrives are fairly small,  40 gig. ATA WDC

---

### Post by Chuck_N on 2010-05-01
Chuck,
 I just checked the HP support site and it does link to ATI's site for Windows drivers. Your video settings in your current configuration are very high indeed (as noted by egalvan) and will contribute to the problem hugely. Maybe you could consider upgrading from integrated graghics to a dedicated video card, if possible, for this machine as well as some RAM. Even a very low end cheap video card nowdays would give a significant boost  to both systems.
[COLOR=Red]
sorry, out of town for a while. hard to get back into the middle of this.
I added 512 meg RAM. That helped much for speed but did not eliminate freezing; however, I freeze much less often now. [/COLOR]

Is your Windows system XP as is indicated by the HP site.[COLOR=Red] No, I have two 40-meg drives; the primary boot drive is Ubuntu, the secondary is Win2K. [/COLOR]  If so note that XP did away with the underlying DOS environment by integrating it into Windows itself (that is it did away with the ability to boot to a DOS screen at startup, but you can access a command prompt from in the GUI). I've 16 years experience with Windows, from the 3.11 days to Vista now (not worried about 7 now I'm in Ubuntu, & have been so since Gutsy Gibbon 7.10).

I'm running much higher specs on my Acer laptop, Intel T2500 2GHz dual core (32bit) processor, 2GB RAM, 667MHz FSB, X1600 ATI vid (512MB). And yet noticed the same lockups you describe, but nowhere near the severity you are having, when switching to Karmic. Hence I checked around at the time as to why and will wait till things improve.

[COLOR=Red]I'm awaiting a (free) video card from my son. However, do you have any suggested inexpensive card I should buy, should this free one not come through?[/COLOR]
I'll summarize with "Low RAM + High vid resolution on old (possibly very low video RAM) integrated graphics + ATI driver issues after Ubuntu 9.04" _most likely explain the situation you're describing. Correct me if any of the summary is wrong re your hardware.

Cheers Nev[/QUOTE]

---

### Post by cascade9 on 2010-05-15
Any progress Chuck_N?

---

### Post by Chuck_N on 2010-05-15
well, yes and no.........

I tripled RAM by buying and adding 500GIG to the 250 I had been using.
This made the computer much more responsive, faster, and cut the freezeups down to maybe 1/3 of previous occurences. But still a problem.

Upgraded from 9.04KK up to 10.04 Lucid Lynx. Took a couple hours to get KK updated (which troubles me, I thought that was accomplished as necessary)  I think that update went error-free. But the upgrade to 10.04 was harrowing; took hours, had some areas of question. Now I get error lists at various times (bootup,shutdown for sure) , cookies don't seem to work although I've checked and expanded the settings, so I need to sign into YMail and this Forum and GMail each new bootup. 

I think maybe I should REinstall 10.04. What do you think? 

Freezeups still happen in much the same way, although less often.  In addition, I sometimes get complete blackout freezeups, followed by a small video pattern that makes me think that the video card improvement may help.  Did not get the hand-me-down video card so I'll need to shop for one.

---

### Post by cascade9 on 2010-05-15
Hmmm...I agree, I think a video card could help a lot. I'm sure I've seen thing on this forum about the intel 845 chipset video (which is what your computer is using with no video card) having issues with newer ubuntus (and having issues with linux in general) but I'm not 100% on that. 

Reinstalling 10.04 might not be a bad idea. It migth be easier to do it when (if) you get a video card, but that shouldnt matter to much. 

No idea on the cookies problem..probably another reason to try a reinstall. 

At least its crashing less than it was...going from 256MB of RAM to 768MB has helped that at least. Bonus that its made your computer a lot faster :)

---

### Post by Efaustus9 on 2010-05-15
I am having the same problem as Chuck_N's original post except that I am using 10.04. If I boot ubuntu normally the system will freeze up with in a couple seconds to a couple minutes after I sign in. The only way to get a usable system is to boot ubuntu into recovery mode then select to run with low graphic settings. I have an acer travelmate 3200 with a Radeon mobility 9700 video card. I am using open radeon drivers. Is there a way to trouble shoot and resolve what is causing graphical the issue.

---

### Post by Chuck_N on 2010-05-15
Now I'm going from bad to worse. I can boot to windows and get to the internet.
I'm in Windows now, sending this.

However, if I do a normal boot, to Ubuntu, and select FF or Opera, I get
"Could not Locate Remote Server". 
It suggests I uncheck "Work Offline". I do and this still gets me nowhere.

I went to System/Admin/Network Connections and all of the tabs were empty.
In the WIRED tab, I clicked on ADD and a new  WiredConnection1  was established,
and,after reboot,  is still there, but still does nothing. 

I have a cable connecting me to the modem, haven't tried to install wireless yet.
This has been sufficient for months, and as I said, still works for Windows.

I think I should go ahead and ReInstall 10.04LL. I upgraded without an install disk. 
No idea how to REinstall.  Any suggestions on how I do this?

-Chuck_N

---

### Post by Efaustus9 on 2010-05-15
It seems 10.04 has a bug when it comes to recognizing radeon rv350 video cards. After spending a little while on google I think I figured out the solution. 

First part was the 30th post by Leonidas Spyropoulos here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561789)

who suggested that adding to the radeon.conf file;
 options radeon agpmode=-1
 options radeon modeset=1

will resolve the bug 10.04 has with rv350 videocards. However I couldn't find the radeon.conf file, it didnt seem kms had generated one.

So after a little more searching I found the other part of the puzzle here:
[http://ubuntuforums.org/archive/index.php/t-1305306.html](http://ubuntuforums.org/archive/index.php/t-1305306.html)

the post by rednzl instructed the following

1. Open a terminal and paste this:
sudo gedit /etc/modprobe.d/radeon-kms.conf
2. add these lines to the new file:
##enable KMS Radeon
options radeon modeset=1
3. save and close text editor
4. execute this line in the terminal:
sudo update-initramfs -k `uname -r` -u
5.reboot.

I added "options radeon agpmode=-1" to part 2. of the above as suggested by Leonidas Spyropoulos. I then crossed my fingers and rebooted. Success :D. I have been using ubuntu 10.04 with normal graphic settings on my acer 3200 laptop for about 30 minutes now, so far so good. If you can fix grub this will probably fix your problem as well Chuck_N.

---

### Post by cascade9 on 2010-05-18
Well, I feel like a right dingbat- 

> X freezes (GPU lockups) are being experienced on i845, i855 and other 8xx chips.   

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

I know, that page is for 10.04, but I found one saying the same thing for 9.10. At least I think I did (I was at work, and for stupid reasons I cant save links there)

---

### Post by Chuck_N on 2010-05-28
well, anyone ready to try and help old Chuck_N again?

I used 9.10 successfully for a while, after adding 500meg ram,  with less prevalent freezeups.

Then I got notified I could update 9.10 and upgrade to 10.04 Lucid.  I did, unfortunately.

The upgrade was frought with troubles and what I've had since has been bad.  

Boot drive 1 (10.04) no longer can get to the web.

Alternate boot drive (win2k) worked well for quite a while.

I recently built a new liveCD Lucid and would like to use it to reinstall my boot drive. Not quite sure how
to do it.  I tried a couple days ago, got spooked and aborted it.  Now I can no longer get to Windows. I get a message that I need to fix that drive with a Windows source disk, which I don't have.  Forget that.

How do I go about rebuilding my boot drive 10.04 Lucid using the liveCD ?

---

### Post by Chuck_N on 2010-05-29
okay, I got it done:  a nice install of  10.04 LL from the liveCD.

I've been up for 24 hours, little troubles.  Had to enable video and audio (which was muted)

but overall everything is fine.

---

### Post by Chuck_N on 2010-06-07
xxx

---

### Post by bobnutfield on 2010-06-07
I don't recall reading in this thread that your video chip was ever confirmed and what module the system was loading for it (could have missed it.)  Open a terminal and type:

> lsmod | grep video

This will tell you what module is actually being loaded for your graphics.  If it is in fact an Intel 8xxx chipset, that will be the cause of your issues. There are already a number of threads here about this issue.

---

### Post by Chuck_N on 2010-06-07
thanks for the response Bob

yes, I continue to have a major freezing up problem that I would love to get fixed.
On average, maybe once per hour, randomly.

I found out yesterday that if I go to
System/Preferences/Screensaver,  the second I click on GLSlideShow, I go to blackscreen/freezeup.
Checked it 5 or 6 times.  Maybe this is a usable clue?

I went to 
lsmod   grep   video
and only got
[COLOR=RoyalBlue]video   17375   1   i915
output  1871  1  video[/COLOR]

---

### Post by bobnutfield on 2010-06-08
OK, I suspected that you had Intel graphics from what I was reading.  Go to /etc/defaults/grub.  Look at the line that reads GRUB_CMDLINE_LINUX_DEFAULT="quiet splash".

Now, open a terminal and type:

> sudo gedit /etc/defaults/grub

This will open the file for editing as root.  Add the following to the line noted above:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"

It must look like I have shown above.  Save the changes to the file and close it.
Then in a terminal run:

> sudo update-grub

This will restore kernel modesetting which has recently been removed for this module.  There are many threads about it, it's causing no end of grief to many people with this older chipset.

Now reboot.  Test it for a while and see if you continue to get any more freezes.

---

### Post by Chuck_N on 2010-06-09
thanks Bob, I will step through that.

I see Comp-USA has this video card on sale for $20 after rebate

  EVGA 512-P3-1215-LR GeForce 210 Video Card -  512MB DDR3, PCI-Express 2.0, DVI, HDMI, VGA, Low Profile

How do I go about finding out if  this would be a sensible purchase for my Presario  SR1503WM ?

I think I've researched my own question.............  this computer appears to have 3 PCI slots (one used)
this card is PCI-Express 2.0, therefore it won't fit.

Here is a PCI card :
[http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=4312749&sku=B52-8400&srkey=b528400](http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=4312749&sku=B52-8400&srkey=b528400)
at $40.    How do I verify that it is a good one for this machine for Ubuntu?

update:  poor user ratings on this one.  Need to shop more.......

---

### Post by Chuck_N on 2010-06-09
okay, I got into command mode and typed

                             sudo gedit /etc/defaults/grub     

             (with only that one space included)                 

and got command not found

tried without the  s  on defaults

still   command not found


?????????

---

### Post by WolfRage on 2010-06-09
So if you type "sudo" and hit enter does Ubuntu ask you for your password?
If you type "gedit" into terminal and hit enter does it launch the Gedit text editor?

---

### Post by Louisraritan on 2010-06-09
Hi Chuck.  Here are the specs for pc.  Hope they are correct, I Googled your model: Compaq Presario SR1503WM Desktop PC

Specs:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775")

Appears that you have a proprietary MOBO and the video card is integrated.  

I Googled the problem you describe and came up with a string for a similar problem in windows:

[http://techrepublic.com.com/5208-10879-0.html?forumID=101&threadID=321421&messageID=3207163&tag=content;leftCol]("http://techrepublic.com.com/5208-10879-0.html?forumID=101&threadID=321421&messageID=3207163&tag=content;leftCol")

Know it is windows but the problem is similar, have you upgraded the ram?  Compatible RAM is:

2 x 184-pin DDR DIMM sockets support unbuffered non-ECC 2 GB 333/266 MHz DDR SDRAM memory modules

---

### Post by Chuck_N on 2010-06-09
> **WolfRage said:**
> So if you type "sudo" and hit enter does Ubuntu ask you for your password?
If you type "gedit" into terminal and hit enter does it launch the Gedit text editor?

I type   ctrl  alt  F2
I get a desktop entry prompt
I type  CHUCK
I get a password prompt
I type the password
I get a few lines of info
followed by a prompt
I type  SUDO
I get a few lines of info on the usage of SUDO
If I type  SUDO GEDIT
it asks for PSWD 
after entering the password
I get   WARNING ** cannot open display

---

### Post by Chuck_N on 2010-06-09
some time ago I added a  512 meg  ram 
to the 256 that was in there.  
It improved performance dramatically
and eliminated lots of troubles,
but not the blackout/freezeups which have been present "forever"
 (since I acquired this used machine).

---

### Post by bobnutfield on 2010-06-10
Are you using the command I suggested from a terminal?  Applications>Accessories>Terminal   

This brings up a terminal showing a prompt like:

> user@yourmachine:~$

If you are not seeing that, you are in the wrong place.

---

### Post by Chuck_N on 2010-06-10
[COLOR=Red]> **bobnutfield said:**
> Are you using the command I suggested from a terminal?  Applications>Accessories>Terminal   

This brings up a terminal showing a prompt like:[/COLOR]> **bobnutfield said:**
>  [COLOR=Red]

If you are not seeing that, you are in the wrong place.[/COLOR] 


well, duh, I got  ctrl-alt-F2 out of a book;  if you do it you get a black screen
and login the same way, but when I then do   Sudo Gedit   it doesn't work.
ctrl-alt-F7 then gets you out.

Your way is apparently better.  The white screen is nicer, and more importantly
Sudo Gedit  works.  and  Xing out to quit is nicer.  
Okay, I'll do it that way from now on. I've learned one more lesson.

---

### Post by Chuck_N on 2010-06-10
[COLOR=Red][QUOTE=[/COLOR][COLOR=Red]OK, I suspected  that you had Intel graphics from what I was reading.  Go to  /etc/defaults/grub.  Look at the line that reads  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash".

Now, open a terminal and type:[/COLOR] [COLOR=Red]
[/COLOR]  	[COLOR=Red]Quote:[/COLOR]
 	 	 		[COLOR=Red] 			 				sudo gedit /etc/defaults/grub 			 	[/COLOR] 	 	 
[COLOR=Red]This will open the file for editing as root.  Add the following to  the line noted above:

[/COLOR]   	[COLOR=Red]Quote:[/COLOR]
 	 	 		[COLOR=Red] 			 				GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1" 			 	[/COLOR] 	 	 
[COLOR=Red]It must look like I have shown above.  Save the changes to the  file and close it.
Then in a terminal run:
[/COLOR]  	[COLOR=Red]Quote:[/COLOR]
 	 	 		[COLOR=Red] 			 				sudo update-grub 			 	[/COLOR] 	 	 
[COLOR=Red]This will restore kernel modesetting which has recently been  removed for this module.  There are many threads about it, it's causing  no end of grief to many people with this older chipset.

Now reboot.  Test it for a while and see if you continue to get any more  freezes.[/COLOR] 
 		                   		  		  		 		[COLOR=Red] 			 				__________________
				Bob
___[/QUOTE]


[COLOR=Black]I type   sudo gedit   and I get a gedit screen  named grub  which is empty.[/COLOR]
[/COLOR]

---

### Post by bobnutfield on 2010-06-11
> **Chuck_N said:**
> [COLOR=Red]


[COLOR=Black]I type   sudo gedit   and I get a gedit screen  named grub  which is empty.[/COLOR]
[/COLOR]


OK, Sorry, that was my error.  The correct command is:

```
sudo gedit /etc/default/grub
```

Then follow the instructions I posted before.

---

### Post by Chuck_N on 2010-06-11
okay, we're making progress.  I got the   GRUB  file opened. It's about 30 lines long.



[COLOR=Red] Add the following to  the line noted above:

[/COLOR]       [COLOR=Red]Quote:[/COLOR]
                   [COLOR=Red]                              GRUB_CMDLINE_LINUX_DEFAULT="quiet  splash i915.modeset=1"                  [/COLOR]           
[COLOR=Red]It must look like I have shown above.  Save the  changes to the  file and close it.
Then in a terminal run:
[/COLOR]      [COLOR=Red]Quote:[/COLOR]


There is a line in the file which reads    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Do you want me to REPLACE that line with
[COLOR=Red]GRUB_CMDLINE_LINUX_DEFAULT="quiet  splash i915.modeset=1"                  [/COLOR]           
??????
and then save the file?

---

### Post by 98cwitr on 2010-06-11
> **Chuck_N said:**
> okay, so what would I do?

we I downgraded to 9.04, but 10.04 wasn't out at the time...maybe upgrade your distro? Or update grub

---

### Post by bobnutfield on 2010-06-11
No, don't replace anything.  Just add **i915.modeset=1** just after "quiet splash", but inside the same quotes, so that it looks like this:

> "quiet splash i915.modeset=1"

Change NOTHING else.  Be very careful here and change only what I have suggested.

Once you have made the changes, save the file (just click File>Save.)  Then, in the same terminal after you have closed gedit, type

> sudo update-grub

Then reboot and see how it goes from there.

---

### Post by Chuck_N on 2010-06-11
[COLOR=Magenta]> **bobnutfield said:**
> No, don't replace anything.  Just add **i915.modeset=1** just after "quiet splash", but inside the same quotes, so that it looks like this:
.
[/COLOR]  

okay, it is done.  I will reboot and see if my troubles have gone away.

If they have, I OWE YOU ONE !!!!

I've had this problem for months................

---

### Post by bobnutfield on 2010-06-11
Can't promise, but the regression that occured with the intel graphics drivers have been causing a lot people who have older intel graphics chipsets (82845, 82855, etc.) problems just like yours.  I myself had two laptops with this graphics set and it cured it for me.

Good Luck.

---

### Post by Chuck_N on 2010-06-11
after a fresh boot, I went to
System/Preferences/ScreenSaver
as soon as I select GLSlideShow, the screen goes black and system freezes.
Not that  GLSlideShow is that important.

However, I tried half a dozen other choices, and they are okay.

Time will tell, however, if I get my random freezes,
which is the important thing.

---

### Post by bobnutfield on 2010-06-11
Freezing when trying to run an OpenGL screensaver certainly suggests that you graphics card cannot handle it.  If you continue to get random freezes when NOT doing anything graphics intensive, then it is another hardware issue which could be anything, so I could not diagnose it.  But hopefully, with kernel modesetting you won't get those types of freezes.

---

### Post by Chuck_N on 2010-06-11
[COLOR=Red]> **bobnutfield said:**
> Freezing when trying to run an OpenGL screensaver certainly suggests that you graphics card cannot handle it.  If you continue to get random freezes when NOT doing anything graphics intensive, then it is another hardware issue which could be anything, so I could not diagnose it.  But hopefully, with kernel modesetting you won't get those types of freezes.[/COLOR]


All the screensavers can be selected from the ScreenSavers menu EXCEPT GLSlideshow which blows up immediately on selection, and AntSpotlight which runs for maybe 3 seconds.

Keep your fingers crossed for kernel modesetting to do the trick for my random freezes.

yeah, and just try to type with crossed fingers.

---

### Post by Chuck_N on 2010-06-20
okay, I've been too busy for a week to do much with this....

yes, I still have blackout/freezeups.  They changed some in appearance:  the white bars no longer
blink at screen-top, but they still happen randomly, maybe once an hour  average.  It rarely freezes less than
30 minutes now, whereas it was occasionally freezing within 2 minutes before.

I'm wondering if I should invest in an inexpensive video card, or if I  should scrap the computer altogether.

I solicit advice on cards to consider, or recommendations otherwise................

---

### Post by Chuck_N on 2010-06-28
okay, I downloaded and checked and built and checked a new live/install disk for 10.04
and threw away the first one.  This disk is working 100% and I've installed it on a Dell laptop.
Even GLSlideshow  and  AntSpotlight  work well on the laptop.
only problem I'm now having with it is trying to install the GSky wireless adapter that was
recommended to me for Ubuntu for the desktop.  I will file a separate thread on it.

  I formatted a different drive with 10.04 in the desktop..  Itr runs the same way it did with the first
drive and with 10.04 or the older 9.7 Ubuntu. Namely, it quits every so often, in the same manner.
So I need to know if I should scrap the computer  OR  if it is worth the gamble to put in a video card,
hoping that will fix the blackouts as well as improve the video.  

Suggestions, please...........................

-Chuck

---

### Post by Chuck_N on 2010-06-30
I am considering this purchase
[http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=4312749&sku=B52-8400&srkey=b528400](http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=4312749&sku=B52-8400&srkey=b528400)

for this Compaq Presario SR1503WM

please comment on appropriateness
to replace onboard graphics
and hopefully have no more troubles with blackouts?

How do I find out the procedure for installation and bypassing the onboard graphics?
Does that come with the board?

-Chuck

---

### Post by Chuck_N on 2010-07-22
okay, I got the card. Wouldn't install, figured power supply insufficient. 
bought a larger power supply. still won't install. It goes to pages of kernel panic after the GRUB menu.

I believe I have 2 problems here, although they may be combined as one.
1) Periodically, randomly?, my computer goes to black screen
2) Heavy graphics jobs can cause freezeup, blackscreen.

I recently noticed these phrases blink when freezing to black screen
"hangcheck timer elapsed"  "GPU hung"
I plugged that into GOOGLE and found many sites having info on Ubuntu hangups like mine.  

I'm a novice on this; can anyone try to walk me through this once again.  I'm about to toss this computer in the garbage and start fresh.  f-r-u-s-t-r-a-t-e-d !!!

---

### Post by soldier1st on 2010-07-22
how much memory do you have free? also are you using the swap file heavily. try this topic it did help me [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by RJARRRPCGP on 2010-07-22
Random freezes in the form of a hard lockup are typical of having too high of a GPU overclock.

---

### Post by RJARRRPCGP on 2010-07-22
> **Chuck_N said:**
> downloaded a different .pps   asked for it to run.
Presentation opened, showed only the first slide
blew up
froze.

Sounds like a gross hardware issue. I suspect a real high processor temp, a bad HDD or a bad PSU. 
Especially if the mouse pointer is frozen!

The cause can be bad caps! 

[http://badcaps.net](http://badcaps.net)

-Or-

The video hardware being overclocked too high.

---

### Post by Chuck_N on 2010-07-22
> **soldier1st said:**
> how much memory do you have free? also are you using the swap file heavily. try this topic it did help me [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I have 20 years of Windows experience which I would like to put behind me and be an Ubuntu devotee.  Only a few months around here; no idea how to find how much memory I have free.  I can tell you how to do it in Windows.   8-)
I upgraded memory on this cptr to 512 megs. Please tell me how to get a memory report.

Seems to me the memory upgrade alleviated swap file problems.  That was a couple months back..........

---

### Post by Chuck_N on 2010-07-22
> **RJARRRPCGP said:**
> Random freezes in the form of a hard lockup are typical of having too high of a GPU overclock.

Compaq Presaario  SR 1503 WM  stock.  Not a powerhouse.

---

### Post by Chuck_N on 2010-07-22
> **RJARRRPCGP said:**
> Sounds like a gross hardware issue. I suspect a real high processor temp, a bad HDD or a bad PSU. 
Especially if the mouse pointer is frozen!
The cause can be bad caps! 
[http://badcaps.net](http://badcaps.net)
-Or-
The video hardware being overclocked too high.

stock compaq presario   SR1503 WM
the computer:   [http://reviews.cnet.com/desktops/compaq-presario-sr1503wm-celeron/1707-3118_7-31649594.html](http://reviews.cnet.com/desktops/compaq-presario-sr1503wm-celeron/1707-3118_7-31649594.html)
my motherboard:  [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775)

2 fans working fine.  I've swapped harddrives and symptoms remain.
New PSU, 450. was 350

Actually keyboard usually is active after blackout. Mouse does not show, of course.

---

### Post by Chuck_N on 2010-07-22
> **soldier1st said:**
> how much memory do you have free? also are you using the swap file heavily. try this topic it did help me [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

okay, I did that link.  My cptr is  low ram (512 meg)  and  low  drive (two 40-GIGers).

Beyond that, the link was pretty heavy for me; I could get no direction............

---

### Post by Chuck_N on 2010-07-24
seems to me the   "hangcheck timer elapsed"  "GPU hung" messages are a pretty good clue to what's happening.  But I still have no idea where to go with it.  Anyone out there care to jump in and try to get this problem solved? It's gone on way too long and I'm about ready to scrap the computer. 

Anything else I can try, to get this freezing-up to quit ????

---

### Post by Chuck_N on 2010-07-26
okay, I've given up on the video card and returned it along with the PSU.

Sure would love to get some direction on the blackouts though; I like using this machine for email and internet stuff, but tired of blackouts every hour or so.

---

### Post by Chuck_N on 2010-08-16
I see this thread has had 4,200+ views  which makes me think this is worth pursuing yet.

New observation: while my installed 10.04 Ubuntu (and previous 9.7) continue to freezeup
and require power-off/restart, and using 10.04 CD disk run does the same,  I can use ANTI-X CD disk run and have done so for tens of hours without ever having a freezeup. I am, in fact, using Anti-X right now. So the problem is something inherent with Ubuntu and my Presario SR1503SX, I would say.  

One file, in particular, blows Ubuntu, usually, every 10 to 30 minutes,  or so, whether I use FireFox or Chrome. It is a fairly long text file with embedded pics, which I download daily from Trading Post on the radio, for selling and buying stuff.  It downloads quickly, without problems, into Anti-X's browser.( If Anti-X could be installed, permanently, and had more features, I could just switch to it).

Anyone around to help me with this long-standing problem ?  I sure would like to get this desktop working well in Ubuntu.

-Chuck

---

### Post by Chuck_N on 2010-08-19
Jeez, is there no one available
willing to try to fix this Ubuntu problem ???

The blowups are random, from all I can tell.
Someone previously suggested bad caps (capacitors)
Is there any software to use to check on bad caps ?

-Chuck

---

### Post by Chuck_N on 2010-08-22
I just ran   System Testing  from Administration.
The Video testing is interesting.............
   it cycles through the video modes somewhat successfully
              seemed sorta erratic
   then it flashes and shows   Auto Adjust
   then either goes black or gets stuck.
  It appears similar to the way it always gets stuck.

Maybe my whole problem is with video?

 anyone around here willing to look at my problem ???

---

### Post by BillyBoy0001 on 2010-08-23
I was running 9.04 and until upgrading to 10.04 had no problems with the screen freezing. I run only Ubuntu on this machine, no windoze at all.. Same video, same RAM, same everything yet still freezes???

---

### Post by rtimai on 2010-08-26
Chuck_N,

Firstly, if you do have an nVidia graphics card and are running Karmic 9.10 and haven't upgraded to Lucid 10.4, here is a possibility:  Karmic uses usplash to display the graphic interface for the login prompt, which had some kind of "framebuffer" issue with some nVidia drivers (mine included.) I have an ancient RIVA TNT2 graphics card, and I THINK I was using the "nv" (open source nVidia clone) driver at the time. I had the blank screen "pause" that I think was similar to your description of the hang on login. The fix had something to do with disabling the framebuffer or disabling usplash and allowing the Gnome Display Manager (gdm) to handle the login -- or something like that, I don't remember the details. Here's 'evidence' of what I said, I don't fully understand this stuff. 

[http://www.ubuntugeek.com/ubuntu-10-4-lucid-boot-experience-changing-from-using-usplash-to-plymouth.html](http://www.ubuntugeek.com/ubuntu-10-4-lucid-boot-experience-changing-from-using-usplash-to-plymouth.html)

The ALTERNATE ANSWER is that upgrading to Lucid 10.4 fixes the usplash problem, as Karmic now uses Plymouth to handle the graphic interface for the login. I believe Lucid also replaced the 'nv' driver to 'nouveau,' a better open source nVidia driver. Either the switch to Plymouth or to nouveau in Lucid Lynx eliminated my login hang.

SECONDLY, your questions about getting system information:

> "Hardware drivers" tells me I have no proprietary drivers.
How do I find out if I have an NVIDIA card?

The following are "list hardware abstraction layer" commands... Grep is a text find/manipulation tool. The "|" pipe symbol stands for "feed output to [another_command]" It's located in various places on different keyboards, but you should have it somewhere. 

List my pci devices, but only show lines with the phrase "VGA"
lspci | grep "VGA"

Am I using the nouveau driver for my nVidia graphics card? (If you get a result, the answer is yes. No response is a no.)
lshal | grep "nouveau"

if not, what drivers am I using?
lshal | grep -i "info.linux.driver"


A compilation of command line system information queries:

[http://tombuntu.com/index.php/2010/05/01/setting-up-ubuntu-10-04-lts/](http://tombuntu.com/index.php/2010/05/01/setting-up-ubuntu-10-04-lts/)

I suggest running the 'lspci' command in the windowed Terminal, not in the tty (Ctrl-Alt-F1-F-6) as it prints (displays) a list longer than the screen buffer can handle. The windowed Terminal has a bigger buffer that you can scroll back on.

You also know that for information about using any commandline tool you enter [command] --help, or man [command] (Enter 'q' to quit the manpage.) TIP: Another helpful tool for Windows/MS-DOS refugees is 'apropos.'

Good luck!

---

### Post by Chuck_N on 2010-08-26
Since my computer freezes often, I have pasted your response into Writer, changed to red. Now I can add to this document, as appropriate, and when my computer goes down, which it has once already, when I get up, I can recover the document and type on....      First, the characteristics of the freeze: I have not noticed a cause. It happens more often on graphics intensive and on large files, but sometimes I can use such files for hours. Then sometimes I'll go down 5 times in a hour.  Someone suggested bad capacitors; I have GOOGLEd up info, and not found my motherboard as a candidate.   
 You can read most everything I'm typing here by scanning through the 130 entries of this thread. Plus much more, of course.
 
[COLOR=#ff0000]Firstly, if you do have an nVidia graphics card and are running Karmic 9.10 and haven't upgraded to Lucid 10.4, here is a possibility: Karmic uses usplash to display the graphic interface for the login prompt, which had some kind of "framebuffer" issue with some nVidia drivers (mine included.) I have an ancient RIVA TNT2 graphics card, and I THINK I was using the "nv" (open source nVidia clone) driver at the time. I had the blank screen "pause" that I think was similar to your description of the hang on login. The fix had something to do with disabling the framebuffer or disabling usplash and allowing the Gnome Display Manager (gdm) to handle the login -- or something like that, I don't remember the details. Here's 'evidence' of what I said, I don't fully understand this stuff. 

[/COLOR][http://www.ubuntugeek.com/ubuntu-10-...-plymouth.html](http://www.ubuntugeek.com/ubuntu-10-...-plymouth.html)
 [COLOR=#000000]Computer is  stock compaq presario SR1503 WM
the computer: [/COLOR][http://reviews.cnet.com/desktops/com...-31649594.html]("http://reviews.cnet.com/desktops/compaq-presario-sr1503wm-celeron/1707-3118_7-31649594.html")[COLOR=#000000]
my motherboard: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&lc=en&dlc=en&cc=us&os=228&product=501775](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&lc=en&dlc=en&cc=us&os=228&product=501775)[/COLOR]
 


 [COLOR=#000000]While my installed 10.04 Ubuntu (and previous 9.10) continue to freezeup
and require power-off/restart, and using 10.04 CD disk run does the same, I can use ANTI-X CD disk run and have done so for tens of hours without ever having a freezeup.  So the problem is something inherent with Ubuntu and my Presario SR1503SX, I would say. [/COLOR] 
 [COLOR=#000000]The freezeup always goes roughly the same: black screen, some white-lettered error messages flash on and off (to which I have made reference on previous pages) then it sits there green power light on, no action on the harddrive light. [/COLOR] 
 [COLOR=#000000]I tried to install a video card; could not get it working; sent it back.   Seems to me the "hangcheck timer elapsed" "GPU hung" messages are a pretty good clue to what's happening. But I still have no idea where to go with it. Anyone out there care to jump in and try to get this long-term problem solved? [/COLOR] 
 [COLOR=#ff0000]
The ALTERNATE ANSWER is that upgrading to Lucid 10.4 fixes the usplash problem, as Karmic now uses Plymouth to handle the graphic interface for the login. I believe Lucid also replaced the 'nv' driver to 'nouveau,' a better open source nVidia driver. Either the switch to Plymouth or to nouveau in Lucid Lynx eliminated my login hang.

SECONDLY, your questions about getting system information:[/COLOR]
  [COLOR=#ff0000]Quote:[/COLOR]
                                                      [COLOR=#ff0000]"Hardware drivers" tells me I                 have no proprietary drivers.  [COLOR=#000000]My installed                  (new flat panel) Dell monitor must have a driver , no?   Maybe                 that is where my problems lie? It was perhaps 5 or 6  months ago                 when I bought it, and I recall difficulties getting it up and                 running. I don't know if I had freezeup problems before this                 monitor; I think I did. I'll have to look back through my other                 threads. [/COLOR]
How do I find out if I have an NVIDIA card?                  [COLOR=#000000]That sounds like a silly question: if I                 have onboard graphics, I'd have NO card. Right?[/COLOR][/COLOR]
                             [COLOR=#ff0000]The following are "list hardware abstraction layer" commands... Grep is a text find/manipulation tool. The "|" pipe symbol stands for "feed output to [another_command]"  [/COLOR][COLOR=#000000]I understand piping; I'm an old DOS guy.[/COLOR][COLOR=#ff0000]  It's located in various places on different keyboards, but you should have it somewhere. 

List my pci devices, but only show lines with the phrase "VGA"
lspci | grep "VGA" [/COLOR] 
 [COLOR=#000000]chuck@chuck-desktop:~$ lspci | grep "VGA" [/COLOR]
 [COLOR=#000000]00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)[/COLOR][COLOR=#ff0000]

Am I using the nouveau driver for my nVidia graphics card? (If you get a result, the answer is yes. No response is a no.)
lshal | grep "nouveau"   [/COLOR][COLOR=#000000] no response[/COLOR]
 [COLOR=#000000]chuck@chuck-desktop:~$ lshal | grep "nouveau" [/COLOR]
 [COLOR=#000000]chuck@chuck-desktop:~$  [/COLOR]
 [COLOR=#ff0000]
if not, what drivers am I using?
lshal | grep -i "info.linux.driver"[/COLOR]
 [COLOR=#ff0000]
[/COLOR][COLOR=#000000]chuck@chuck-desktop:~$ lshal | grep -i "info.linux.driver" [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'system'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'system'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'i8042 kbd'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'parport_pc'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'serial'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'rtc_cmos'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'system'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'vga16fb'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'serial8250'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'i8042'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'atkbd'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'Intel ICH'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'ata_piix'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'sr'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'sd'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'sd'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = '8139too'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'ehci_hcd'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'usb'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'hub'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'uhci_hcd'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'usb'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'usb'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'usb-storage'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'sd'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'sd'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'sd'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'sd'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'hub'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'uhci_hcd'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'usb'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'hub'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'uhci_hcd'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'usb'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'usb'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'usbhid'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'hub'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'i915'  (string) [/COLOR]
 [COLOR=#000000]  info.linux.driver = 'agpgart-intel'  (string) [/COLOR]
 [COLOR=#000000]chuck@chuck-desktop:~$  [/COLOR][COLOR=#ff0000]

A compilation of command line system information queries:

[/COLOR][http://tombuntu.com/index.php/2010/0...ntu-10-04-lts/]("http://tombuntu.com/index.php/2010/05/01/setting-up-ubuntu-10-04-lts/")[COLOR=#ff0000]

I suggest running the 'lspci' command in the windowed Terminal, not in the tty (Ctrl-Alt-F1-F-6) as it prints (displays) a list longer than the screen buffer can handle. The windowed Terminal has a bigger buffer that you can scroll back on.[/COLOR][COLOR=#000000]  I don't understand that, but it looks like I only got one line, above, with the  lspci[/COLOR][COLOR=#ff0000]

You also know that for information about using any commandline tool you enter [command] --help, or man [command] (Enter 'q' to quit the manpage.) TIP: Another helpful tool for Windows/MS-DOS refugees is 'apropos.'   hmmmmmmmmm..........[/COLOR]
 [COLOR=#000000]chuck@chuck-desktop:~$ apropos [/COLOR]
 [COLOR=#000000]apropos what? [/COLOR]
 [COLOR=#000000]chuck@chuck-desktop:~$ ^C [/COLOR]
 [COLOR=#000000]chuck@chuck-desktop:~$  [/COLOR]
 


 [COLOR=#000000]I had two more freezeups while developing this document.[/COLOR][COLOR=#ff0000]

Good luck! [/COLOR]

---

### Post by rtimai on 2010-08-26
Chuck,

Apparently you do not have an nVidia graphics card, But you knew that already. However, the last message in the thread I read was your question asking how to find out if you were using an nVidia card, and I didn't see a reply to that, so I tried to answer it.

The lspci and lshal information you posted confirmed that you use an integrated Intel-based video chip, and the vga16fb driver for it. So your problem is NOT anything like mine (e.g. nVidia-related.) Initially, I thought this might have been the case because your symptoms sounded so similar to what I experienced previously, but I no longer believe this is so. 

About the apropos command: 
Enter 'apropos --help' for syntax, 'man apropos' for more detailed information. Apropos has more sophisticated uses (beyond my competence,) but you can use it to discover BASH commands for tasks for which you're not sure what the names are. For instance, you want hardware information. Enter 'apropos hardware information' and you'll get a list of commands that are related to the words 'hardware' and 'information'. Former MS-DOS users can use it to try to find the Linux equivalent of many DOS commands. You don't always get a hit, and you have to use your own good judgement with what you find, but I've found it useful at times. 

Of course, you should check out any command FIRST with the --help option, or read the man(ual) page before attempting to use it. Obviously, you don't want to blindly enter commands the usage for which you don't understand. 

Have you tried upgrading to Lucid Lynx 10.4? This latest release does seem to handle my legacy video system better than Karmic. I mean 10.04, not 10.4.

Good luck...

---

### Post by Chuck_N on 2010-08-27
> **rtimai said:**
> Chuck

Have you tried upgrading to Lucid Lynx 10.4? This latest release does seem to handle my legacy video system better than Karmic.

Good luck...


  I'm already on  10.04.

---

### Post by BillyBoy0001 on 2010-09-10
Chuck,
I do have a Nvidia video card which was also run under 9.04 with no problems. Only since the upgrade to 10.04 did I also have these problems. I can move the mouse all over but can't do anything. Thinking about going back to 9.04. I am running the Ubuntu drivers "version 96" as recommended.
Still no luck.. Something wrong with this version of Ubuntu. I'm not sure what to do as this is the only OS on my computer (No dual boot option here).

---

### Post by Chuck_N on 2010-09-10
much luck.  I've given up on using the Compaq for ubuntu. Too many battles over too long a time.
I will install Windows on it, and see how that goes.....

I'm working with Ubuntu on an old Dell laptop now; working pretty good except for a minor video resolution
problem.

Sure is tough for novices to work into Ubuntu. Forum help is sometimes slow, sometimes inaccurate, but I'm
not complaining, just observing..... I understand this is a labor of love and these helpers are not getting paid for the help they give and the time they put in.

---

### Post by perspectoff on 2010-09-10
> **Chuck_N said:**
> compaq presario SR1503WM;  9.10 Ubuntu Karmic Koala

This computer freezes, requiring power-off, somewhere between 2 seconds 
and 2 hours after boot-up, most every time I use it. Sometimes I've had to
power-down perhaps six times in 10 minutes.  

When it freezes I have a movable mouse-pointer that can select nothing. Right-
click does not operate.

I don't seem able to isolate a single cause. I ran a RAM check with no errors
showing. Matters not which version of Ubuntu I choose when booting. I've 
replaced mouse and keyboard. Only running 256 meg of ram and do plan to
add more soon. 

Any ideas?

Thanks, Chuck

I have the same motherboard with Intel integrated graphics that you do. 

The Presario SR1503WM has an Intel 845GV chipset motherboard (Asus brand) with Integrated Intel (Extreme) graphics.

The problem is with Intel integrated graphics and the Linux kernel. I have had the same problem you describe in every version of Ubuntu since Intrepid (Jaunty, Karmic, and Lucid) and in every distro as well (Fedora, Mandriva, etc.)

Don't listen to the idiots who say "try different distros" or nonsense like that. The solution is to change the i915 (Intel 915 graphics) mode when loading the Linux kernel. This can be done from the Grub bootloader.

Here is the work around I have settled upon to do this:

    * When booting up, choose recovery mode as root (or "root with networking"). This will give the command line (as root user). 

    * Edit the Grub2 configuration file: 

sudo nano /etc/default/grub

        * Change the line: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet"

        to 

GRUB_CMDLINE_LINUX_DEFAULT="quiet i915.modeset=0"

        * Then regenerate the Grub2 configuration file: 

sudo grub-mkconfig --output=/boot/grub/grub.cfg

        When I reboot, my graphics work.


I am typing this to you from my computer on Kubuntu Lucid Lynx from my 845GV motherboard with integrated Intel graphics, BTW.

My solutions are also posted at Ubuntuguide.org ( [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Intel_integrated_graphics_cards](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Intel_integrated_graphics_cards) ) and Kubuntuguide.org ( [http://kubuntuguide.org/Lucid#Intel_integrated_graphics_cards](http://kubuntuguide.org/Lucid#Intel_integrated_graphics_cards) )

---

### Post by Chuck_N on 2010-09-10
you are looking a long ways back in this thread of 138 or so posts over 8 months or so.

Not sure, but I think your suggestion came to me b4 and I did that

          * Change the line:  GRUB_CMDLINE_LINUX_DEFAULT="quiet"

                    to             GRUB_CMDLINE_LINUX_DEFAULT="quiet i915.modeset=0"

I will check through this (and other) threads to see if I can find it.

---

### Post by perspectoff on 2010-09-10
> **Chuck_N said:**
> you are looking a long ways back in this thread of 138 or so posts over 8 months or so.

Not sure, but I think your suggestion came to me b4 and I did that

          * Change the line:  GRUB_CMDLINE_LINUX_DEFAULT="quiet"

                    to             GRUB_CMDLINE_LINUX_DEFAULT="quiet i915.modeset=0"

I will check through this (and other) threads to see if I can find it.

You are sure persistent, I must say!

This problem is repeated many, many times in Ubuntu forums, and the solution is not always that clear.

When you responded to the proposed solution last time, you indicated that /etc/default/grub was blank (which it should not be if you have a fresh installation).

Also, the previous reply a while back had advised using gedit, which is a GUI text editor that cannot be used if graphics do not work correctly. That's why I suggest using nano, which is a text editor that can be used in a command-line environment without graphics (as in the recovery mode).

Lastly, although the previous post a while back suggested a solution nearly identical to mine, other threads in Ubuntu forums have noted that his solution often does not work.

He indicated to use "i915.modeset=1" which did not work for me, either. This is well-discussed elsewhere. When I used "i915.modeset=0", everything worked.

Also, he suggested the command "grub-update" to regenerate the Grub bootloader settings. This command has a few unpredictable side-effects in the version of Grub2 found in Lucid, for example.

Instead of "grub-update", as I mentioned in my post, I recommend using the command "grub-mkconfig --output=/boot/grub/grub.cfg"

Oh, I share your pain, brother. The particular computer with the 845GV motherboard has been a real challenge for me over the years.

That motherboard does not have heat sensors, and the Linux kernel initially used for Karmic had a bootup routine that checked the heat sensor output and returned lots of errors with this particular motherboard. I wrote to the person that maintained the heat sensor checking module, and she said that that motherboard was too old to write new modules.

Later, the kernel was fixed so that the heat sensor checking routine had a better error return, and in later versions of the Linux kernel (as in updated versions of Karmic and then in Lucid) I did not have problems.

Also, the new splashscreen manager used in Lucid, Plymouth, does not work on any of my computers which have either Intel integrated graphics or nVidia graphics. But that problem is manifested merely as about 5 seconds of a black screen, after which bootup proceeds normally (once the mode is fixed, as above).  

Believe me, to get this particular motherboard to work well with Linux taught me a heck of a  lot about the Linux kernel, motherboards, and graphics.

I was motivated, of course, because I have 10 servers running on two computers on the silly things.  Yes, they have Celeron D 32-bit single CPU processors, which seem like dinosaurs these days but are not really that anemic for Linux. I ran them with 512 Mb RAM initially, but since memory upgrades are only about $20, they now have 2 Gb RAM each.

They are now rock stable. 

Yeah, I got them with Windows XP, as I assume you did (since that's what shipped with the Compaq model you indicated). But a hard drive problem fried my Windows installation and Microsoft would not help me repair it (this was years ago) so I have not used Windows on these computers since then (being unwilling to fork out a few hundred dollars to replace Windows just because of a hard drive failure).

BTW I tried Puppy Linux, which as you might now know, has gone to Ubuntu minimal server as its base installation (for its most recent version). I really like Puppy Linux for low resource computers, but yours really isn't a low resource computer. You should do fine with Ubuntu or Kubuntu (or Lubuntu or Puppy, if you prefer) with a little extra RAM.

I am very surprised how long this thread has endured. But, in computing, the difference between a period and a comma, or between a 1 and a 0, can be the difference between a computer running or not running.

---

### Post by Chuck_N on 2010-09-10
I may appear persistent, but I'm retired: long on time and short on money.

However, I can hardly remember all that I went through in this long thread.

I infer from this response that we could in fact possibly get the Compaq going 
by using the  grub-mkconfig  and other things you state therein.

If you think it's worth a shot, I will hook it up again and try....

I had given up, and started using a dell laptop hooked to my monitor   BUT  I'd prefer to have the Compaq desktop working well, and keep the laptop free as a laptop. Let me know; I'm not sure that what you
sent me below, will get me all the way through, and I may require considerable hand-holding again.    8-)

---

### Post by avalokitesvara on 2010-09-10
I used to have the same problem when I was on Karmic. When I upgraded to Lucid the GUI freezing was gone, but something new came. Now, from time to time (similar frequency) computer would switch to black screen / text mode saying something like “checking battery state”, and then the screen would start blinking and showing some wrong colors. The good part is that it did respond to the 3 finger salute (ctrl-alt-del).  The bad part is that tonight it happened while I was running an update. It did happen before, but this time I couldn’t login after it happened. When the login screen pops up the GUI is frozen (the mouse doesn’t move, the keyboard doesn’t work). I couldn’t login in the recovery mode either. Any suggestions of what can I do? I really don’t want to reinstall the system.
   
  Thanks

---

### Post by perspectoff on 2010-09-10
> **Chuck_N said:**
> I may appear persistent, but I'm retired: long on time and short on money.

However, I can hardly remember all that I went through in this long thread.

I infer from this response that we could in fact possibly get the Compaq going 
by using the  grub-mkconfig  and other things you state therein.

If you think it's worth a shot, I will hook it up again and try....

I had given up, and started using a dell laptop hooked to my monitor   BUT  I'd prefer to have the Compaq desktop working well, and keep the laptop free as a laptop. Let me know; I'm not sure that what you
sent me below, will get me all the way through, and I may require considerable hand-holding again.    8-)

Heh. There are two little guides called Ubuntuguide.org and Kubuntuguide.org. If you want to see all the fiddling I have done over the past 3 years, check them out. 

These forums are great, but 70% of the advice is wrong or doesn't work (or is long outdated). (Heck, even some of my advice is outdated). I have found many, many times that I have had to synthesize advice (clues here, clues there) from many different locations to find something that actually works. Many times I have had to dig down personally into the code to find out exactly where the problem was, especially for older, very specialized, or brand-new hardware that aren't commonly used. That is true in every OS (and specialized hardware is nearly impossible to use with Macs).

I own 9 computers in my house alone. At any one time, 1 or two of them have some quirk (be it with Windows, Linux, or Mac). Sometimes I just let them sit a while until someone in the forums comes up with a solution THAT ALMOST WORKS. I then tweak and fiddle a little bit more and then voila! up comes the right solution.

Having said that, all 9 of my computers are currently running Lucid in a stable fashion (for the first time ever). I have had to get rid of Network Manager on some (and on some I use Wicd instead of Network Manager for wireless connections), and some I have had to set up NIC bridging and Internet Connection sharing (for some specialized software I use). 

My primary laptop uses Kubuntu Lucid, and I have not logged in to Windows 7 for 9 months, now. (I keep Windows 7 because one company I consult with has a single Windows-specific program.)

I have never thrown away a computer because they all can be made to run (eventually) using Linux. My oldest computer is from 1999 (not at home, but at work), and it happily runs Puppy Linux. Further, some older computers are great as Linux servers (DNS servers, network proxies and monitors, etc.) which don't need a lot of computing power.

So, if you can't get your Compaq to run, I'll take it! (LOL)

---

### Post by fascina on 2010-10-12
Hi perspectoff,

I see that you were able to install Ubuntu on a Presario SR1503WM, I have tried many things and just cannot get beyond the same error posted at [http://ubuntuforums.org/showthread.php?t=765195&page=3](http://ubuntuforums.org/showthread.php?t=765195&page=3)

You're the only one that has a different perspective.

Could you please help me get past this block?

When I read your post I get stuck on the 1st item:

* When booting up, choose recovery mode as root (or "root with networking"). This will give the command line (as root user). 

How do I get to that part, remember that I haven't installed Ubuntu yet on this system.

My specs are:

Compaq Presario SR1503WM
with 1.5 GB Ram
Intel Celeron 2.93 GHz
32 bit
160 Gb WD hard drive
I disabled the on-board video and installed a NVidia GeForce 8400 GS w/ 512 MB DDR2

BTW I would like to eventually make it a dual boot with Win 7 ultimate.

Thanks for all your help and look forward to working with you to get this done.



> **perspectoff said:**
> I have the same motherboard with Intel integrated graphics that you do. 

The Presario SR1503WM has an Intel 845GV chipset motherboard (Asus brand) with Integrated Intel (Extreme) graphics.

The problem is with Intel integrated graphics and the Linux kernel. I have had the same problem you describe in every version of Ubuntu since Intrepid (Jaunty, Karmic, and Lucid) and in every distro as well (Fedora, Mandriva, etc.)

Don't listen to the idiots who say "try different distros" or nonsense like that. The solution is to change the i915 (Intel 915 graphics) mode when loading the Linux kernel. This can be done from the Grub bootloader.

Here is the work around I have settled upon to do this:

    * When booting up, choose recovery mode as root (or "root with networking"). This will give the command line (as root user). 

    * Edit the Grub2 configuration file: 

sudo nano /etc/default/grub

        * Change the line: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet"

        to 

GRUB_CMDLINE_LINUX_DEFAULT="quiet i915.modeset=0"

        * Then regenerate the Grub2 configuration file: 

sudo grub-mkconfig --output=/boot/grub/grub.cfg

        When I reboot, my graphics work.


I am typing this to you from my computer on Kubuntu Lucid Lynx from my 845GV motherboard with integrated Intel graphics, BTW.

My solutions are also posted at Ubuntuguide.org ( [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Intel_integrated_graphics_cards](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Intel_integrated_graphics_cards) ) and Kubuntuguide.org ( [http://kubuntuguide.org/Lucid#Intel_integrated_graphics_cards](http://kubuntuguide.org/Lucid#Intel_integrated_graphics_cards) )

---

