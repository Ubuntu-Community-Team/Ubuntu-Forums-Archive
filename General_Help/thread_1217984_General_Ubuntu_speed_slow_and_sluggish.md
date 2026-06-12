---
title: "General Ubuntu speed: slow and sluggish"
date: 2009-07-20
forum: General Help
---

### Post by jdenhaan on 2009-07-20
Hi folks,

First of all, I'd like to make it absolutely clear I'm not trying to start a flame war here, but I've faced a problem that is so general of nature that I really don't know where to put it but here and how to put it like this.

I've been using Ubuntu on a number of laptops for the past two or three years now, and have alwasy been very happy with it. I mainly do a lot of web developing, and use my station for nothing more than browsing and e-mailing. For web design I use both WinXP in VirtualBox and for gaming I have a dual boot WinXP. Untill now, this situation has worked to my satisfaction.

A recent project forced me to do a lot of testing in IE8 (in my dual boot WinXP), and I came to realize how slow and sluggish Ubuntu feels to me. Working with the desktop, browsing in Firefox; it is all much faster in WinXP than in Ubuntu. Entering text into a textarea in Firefox is so slow it is nearly impossible to type a text more than a few lines (with delays of sometimes seconds between characters). But also just dragging windows around on the desktop... it runs just so much smoother on WinXP than on my laptop.

Now, I've been a big fan of Ubuntu for quite some years, so I know the Ubuntu team prides itself on presenting a faster and more useable OS. Unfortunately, due to reasons I cannot understand, my user experience has been dented.

There are a few things I've figured out about this. First of all, I have a Dell Latitude E5500 laptop that uses Intel Mobile graphics - I seem to remember Intel cards have always been a bit troublesome. I'm using some Compiz desktop effects, mainly because turning them off doesn't improve performance. Also, the slow textarea input in Firefox is something a lot of other people face, without a solution to be found.

Now, I understand a bit about video card drivers and how they can slow the whole deskop down, and I understand a combination of factors can cause trouble on something small like entering text into a textarea within a browser, but all together I cannot do anything else but conclude that running WinXP with IE8 makes more sense for daily tasks.

As I said: I don't want to start a flame war. But I do prefer Ubuntu for my daily stuff, and would not like to switch to Windows if I can help it. But I really think something is wrong with my installation, because it isn't as fast as it should be.

What can I do? :(

Jeroen

Dell Latitude E5500
Dual boot Ubuntu/WinXP
Ubuntu Jaunty

---

### Post by beren.olvar on 2009-07-20
I know the main issue is the general sluggishness of the system, but as you focus a lot in the browsing, maybe you could try testing the performance of other browsers in windows and ubuntu, maybe that is a particular problem of your firefox build and can be solved as easy as changing the browser. If you really love some particular addon, you could try swiftfox for example. 

I cant tell about the rest, my experience has been completly different.
Hope at least your browsing improves ^^

---

### Post by Rawblues on 2009-07-20
Can't provide an answer to this one, but can tell you that on my dual boot system with XP Pro and Ubuntu, Ubuntu is MUCH faster at pretty well everything, including Firefox. 

You must have some quite specific configuration problem. On my system, XP Pro and Ubunto are configured in roughly equal sized partitions of >200Gb. I have not loaded any third-party drivers.

---

### Post by jdenhaan on 2009-07-20
@beren.olvar
Thanks for replying so swiftly. Indeed, the whole system just feel sluggish... the fact that turning of all desktop effects improves nothing, has to mean something. But switching to a different browser is not an option, as I use addons like Firebug quite a lot. I'll give Swiftfox a try though, maybe that works better for me. Just to be complete: I've installed FF 3.5 from the backports, and that did nothing to improve the speed. Thanks again, for helping, I appreciate every hint or tip.

@Rawblues
That's exactly what I would expect: Ubuntu to be (slightly) faster at desktop work like browsing etc., but the opposite is true. On drivers: I have upgraded Intrepid to Jaunty upon release of the latter, and the only proprietary driver the system uses is that for the Broadcom STA wireless driver. In previous installations, I seem to remember that also Intel video drivers were listed in the Hardware Drivers, but that is no longer the case. That makes me wonder...

---

### Post by komputes on 2009-07-20
> **jdenhaan said:**
> 
What can I do? :(


I would recommend the following to test if you get better performance:

1) Turn off compiz
2) Install flashblock extention in firefox or completely remove the plash plugin package
3) Test the following browsers: Epiphany Webkit (much faster) and firefox-3.5 (speed improvements)

#Epiphany - Webkit
#deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main
#deb-src [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main

#Mozilla Daily
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main

4) Download htop and and run it in a terminal, taking a look at it every once in a while to see if any one process spikes or hogs resources.

---

### Post by jdenhaan on 2009-07-20
On Swiftfox: doens't help, unfortunately. Maybe it is slightly faster in usual tasks, but when typing in textboxes, the same problem occurs. To be more exact on that specific issue: the box I'm typing in now (on ubuntuforums) has no delay whatsoever, and works like a charm. But some textareas (on my own site, but also in Wordpress admin and Twitter) have a delay of milliseconds to seconds when entering text or backspacing... FF 3.5 doesn't solve this, Swiftfox neither.

---

### Post by jdenhaan on 2009-07-20
@komputes
I've just installed and tried Epiphany, but the same problem arises (slow input in textareas). Maybe this is related not to Firefox, but to the sluggishness of Ubuntu alltogether?

I've also tried turning of Compiz, but that doesn't help in overall speed (or the textarea problem). It does give some ugly trails when moving windows around (the contents of the windows get distorted when dragging them around, but it turns back to normal when I stop dragging). All and all, not a real improvement.

The distortion of the windows might suggest a problem with my video card drivers, right? Any suggestions, anyone, on what to do? I remember Intel video drivers have always been troublesome, but I was hoping things might have been sorted out by now.

I'll take a look at htop and see if spikes occur, thanks for that suggestion.

---

### Post by jdenhaan on 2009-07-20
Okay, htop give some (to me) strange results... but I'm not technical enough to assess if there is a problem or not (and I wouldn't know how to handle it either ;)

I have two programs running (FF and terminal), and htop has two processes fighting over first place in CPU% use:

/usr/X11R6/binn/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

and

/usr/lib/firefox-3.0.11/firefox

I'm not sure what the first one does, but I've seen it move between 1% and 65%. Dragging the FF window around makes it go to 35-40%. Firefox itself uses between 1-40%, even when doing nothing.

These values seem rather high to me, but perhaps this is always the case...

---

### Post by derrickadean on 2009-07-20
i have the same problem with the sluggishness and when i first star up i get some era messages saying there was problems starting
ofalld:gnome indicator applet
oafll:gonome-fastuserswitchapplet
and until the messages go away i cant do anything

---

### Post by jdenhaan on 2009-07-20
No errors when I start up... that might give a clue, but all seems to go perfectly, except for speed when working.

---

### Post by MikeSD on 2009-07-20
Heh, I just have posted a topic about a same issue today [here]("http://ubuntuforums.org/showthread.php?t=1218066") :)

Just one thing I can add to make you happier - Have you ever tried Vista ?
Well Ubuntu is faster!

---

### Post by kelvin spratt on 2009-07-20
jdenhaan
The problems you describe sound like graphics card to me Intel can cause lots of problems 
not only in Ubuntu but once set up correctly they work really well.

---

### Post by 3rdalbum on 2009-07-20
> **jdenhaan said:**
> @Rawblues
That's exactly what I would expect: Ubuntu to be (slightly) faster at desktop work like browsing etc., but the opposite is true.

If you think about it, your experience makes sense.

Everyone knows that Windows XP is faster than Vista. Windows 98 is faster than XP. Windows 3.1 is faster than 98.

So why wouldn't XP, a very old and obsolete operating system, be faster than the latest Ubuntu? In fact I think it's amazing that the latest Ubuntu *does* go faster than XP for some people.

---

### Post by jdenhaan on 2009-07-20
> Just one thing I can add to make you happier - Have you ever tried Vista ?
@MikeSD: I've tried Vista, and so yes: your remark makes me a bit happier ;)

> The problems you describe sound like graphics card to me Intel can cause lots of problems not only in Ubuntu but once set up correctly they work really well.
@kelvin spratt: I think you might be right, but setting them up correctly... how to do that? In the past, getting Intel drivers to work took some effort, but then they worked. In Jaunty, Ubuntu never asked me to do anything, it just worked out of the box. Therefor, I didn't expect to have to tamper with the video drivers again. Any suggestions as to where to start tuning the Intel drivers?

> So why wouldn't XP, a very old and obsolete operating system, be faster than the latest Ubuntu? In fact I think it's amazing that the latest Ubuntu *does* go faster than XP for some people.
@3rdalbum: I understand what you mean. But shouldn't Ubuntu at least run smoothly on a (not low-level) laptop like mine? So what are you saying? Should I downgrade to an older version of Ubuntu, just because the latest version requires top-notch (non-laptop) systems? That sounds a bit odd to me. I always thought Ubuntu was a good choice for laptops as it would run faster than Windows. XP is, imo, not 'very old and obsolete' btw.

---

### Post by MikeSD on 2009-07-20
> **3rdalbum said:**
> If you think about it, your experience makes sense.

Everyone knows that Windows XP is faster than Vista. Windows 98 is faster than XP. Windows 3.1 is faster than 98.

So why wouldn't XP, a very old and obsolete operating system, be faster than the latest Ubuntu? In fact I think it's amazing that the latest Ubuntu *does* go faster than XP for some people.

I get your idea, but if I have all stuff like visual effects and all other services which are not needed disabled, then why Firefox feels running slower on Ubuntu compared to XP on same hardware?

By the way Ubuntu us using less RAM than XP still that firefox is slower on it :)

---

### Post by p0cky84 on 2009-07-20
> **jdenhaan said:**
> What can I do? :(
Get archlinux.

---

### Post by jdenhaan on 2009-07-20
> **p0cky84 said:**
> Get archlinux.
Thanks, you're a great help. If I'll do any switching, I'm leaning to WinXP right now :(

---

### Post by p0cky84 on 2009-07-20
> **jdenhaan said:**
> >>I'm leaning to WinXP right now :(

Sadface :(

---

### Post by komputes on 2009-07-20
Do you still have sluggish behavior if you create a new user and log out and back in using the new user?

---

### Post by jdenhaan on 2009-07-21
> **komputes said:**
> Do you still have sluggish behavior if you create a new user and log out and back in using the new user?
Yes, I created a test user, logged out and in as the new user, but even on that 'default' user the problem occurs. Thunderbird for example, when minimizing and maximizing again builds op just a bit too slow for comfort (all parts of the window are built so slow I can tell the order in which it's done).

Don't get me wrong: it's not taking seconds, but it is taking milliseconds and those milliseconds start to get to me in a while.

Also, logged in as the test user, text input in form fields is extremely slow on some sites. I'm going to try some things to see if this is not just a javascript/html/css problem or something, as it occurs on the same places over and over again, but not in others...

---

### Post by 3rdalbum on 2009-07-21
> **jdenhaan said:**
> @3rdalbum: I understand what you mean. But shouldn't Ubuntu at least run smoothly on a (not low-level) laptop like mine? So what are you saying?

I'm saying that it's possible that Ubuntu isn't running slowly - it's just running slower than an ancient operating system :-)

---

### Post by The Cog on 2009-07-21
I think you have something strange going on, but I don't know what. I just sat here and watched top or a minute or so (on a Latitude E5500) and the CPU averaged 1-2%, touching 5% once for some reason. I don't see the sluggishness you talk about.

I am using compiz effects, and sometimes they are a little sluggish, but I put that down to having a smallish video buffer. I don't have any noticeable delay typing into textboxes though.

Maybe a rogue forefox plugin?

---

### Post by jdenhaan on 2009-07-21
Concerning the slow text input in FF on my own site: I figured it out. Could have thought of it sooner, but a running jQuery ticker tape cause the delay in typing. Even a slideshow kind of thing, switching every few seconds, delayed typing for a second when it did it's switching. So, on my own site, I fixed it (by removing the offending scripts), but unfortunately things like WP admin keep causing trouble. I'll try and disable some FF plugins, see if that helps (read somewhere that Firebug is a good place to start in case of slowdowns).

> I just sat here and watched top or a minute or so (on a Latitude E5500) and the CPU averaged 1-2%, touching 5% once for some reason. I don't see the sluggishness you talk about.
Running htop, with or without FF, while doing nothing but stare at the screen, mine goes between 5% and 15%. Not sure where to look (it lists 2 cpu's at the top), but still, values like those shouldn't cause trouble, right?

Well, at least the text input thing is sorted out. Probably a javascript/Firefox/Firefox plugin problem; I can live with that. I guess I'll blame the sluggishness of the desktop to poor video card drivers and learn to live with it.

Just a question for future reference: if I was to buy another laptop, and I wanted to make sure video wouldn't trouble me again, what cards/brands should I rule out to begin with? Intel, obviously, any others?

---

### Post by rustyjames on 2009-07-21
close but differet:

i have an amd quadcore with ati onboard graphics and 8gb of mem.
i have 9.04 and run xp in virtualbox.
at times i can click on a link in firefox - then fire up virtualbox xp, open firefox there (or ie) and get that web site still faster than native.

any insights as to why are welcome...

---

### Post by Sörnäinen on 2009-08-28
Hello, I want to join in: Same problem here. 
Ubuntu generally is HEAVILY sluggish, opening windows takes a lot of time, with Win XP the Notebook runs MUCH faster and smoother. Text in FireFox is an issue, too.

It's about all those everyday tasks - the work with Ubuntu reminds me of working with the Apple Powerbook G4, which is simply sluggish with the newer Mac OS X versions. 

I will stick to Ubuntu anyway - but the fact that the battery lifetime is REALLY low compared to XP and the PC is extremely sluggis gives me the feeling that there is something going on that obviously only happens to a few users. 

I remember when installing Ubuntu on the eeePC, it worked wonderful. So I am really surprised and would be happy about some hints...

---

### Post by C14 on 2009-09-13
same problem here, but with a desktop-pc without intel graphics.
My specs: 
P4 2.4GHz
512MB RAM
GeForce 4200 Ti

---

### Post by Hallvor on 2009-09-13
> **p0cky84 said:**
> Get archlinux.

I was wondering how long it would take before that one came.

---

### Post by Hallvor on 2009-09-13
> **C14 said:**
> same problem here, but with a desktop-pc without intel graphics.
My specs: 
P4 2.4GHz
512MB RAM
GeForce 4200 Ti

I think Xubuntu would run a lot better than vanilla Ubuntu with those specs. But even Xubuntu isn`t that light.

---

### Post by relay_man on 2009-09-13
Can you post your processes again with htop.
I'd not worry about about Firefox for now.
I'm concerned with the usr/X11 R6 stuff.

---

### Post by relay_man on 2009-09-13
Hang on...
this may be a known bug.

Look here:
[https://lists.launchpad.net/ubuntu-x-swat/msg08251.html](https://lists.launchpad.net/ubuntu-x-swat/msg08251.html)

---

### Post by relay_man on 2009-09-13
I've been doing a little more research.
X may be tying things up.
Do you have the latest video drivers installed for your laptop?

---

### Post by Sörnäinen on 2009-09-13
> **relay_man said:**
> I've been doing a little more research.
X may be tying things up.
Do you have the latest video drivers installed for your laptop?

Probably your posting was not meant for me, but i will do some research on that issue once i have a little time. Well possible that's the reason.

---

### Post by P4man on 2009-09-13
Im curious, does this sluggishness also occur in a live cd session (other than stuff starting up slowly from a cd obviously) ?

I'd be inclined to blame the onboard intel video drivers, even if what you're seeing doesnt seem directly related to graphics performance. I believe there are some fundamentally new intel drivers in the upcoming karmic, if you feel like trying it out, perhaps it could shed some light on your issues.

---

### Post by Sörnäinen on 2009-09-13
> **P4man said:**
> Im curious, does this sluggishness also occur in a live cd session (other than stuff starting up slowly from a cd obviously) ?

I'd be inclined to blame the onboard intel video drivers, even if what you're seeing doesnt seem directly related to graphics performance. I believe there are some fundamentally new intel drivers in the upcoming karmic, if you feel like trying it out, perhaps it could shed some light on your issues.

I like to hear that. I really like it. 
Since i really have the same feeling - that it might be the Intel Onboard Graphic of my Notebook. Since it uses the RAM, it may very well slow down other processes (I am not an expert, as probably obvious, but it seems logical to me). 

I am very much looking forward to the next version on that rate. :)

---

### Post by relay_man on 2009-09-13
I may be chasing my own tail here, but it might prove to be a good learning experience, so...
Sornainan, if you have time could you post the contents of your file:
 
/etc/X11/xorg.conf

P4man

I'm just learning about X, In my xorg.conf file I found this:

# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

If the config settings that follow these commented lines are in error, would running the command above update the .conf file to the latest settings?

---

### Post by P4man on 2009-09-13
> **relay_man said:**
> 

If the config settings that follow these commented lines are in error, would running the command above update the .conf file to the latest settings?

It would reset them to pretty much default settings. As I understand it, most of the configuration settings that used to be in xorg.conf, are now handled by X and the videodriver automatically, unless you specify "overrides" in xorg.conf.

But its unlikely a wrong configuration in xorg.conf would result in the sort of slow downs the OP is seeing (unless a wrong or no driver would be specified); usually its just stuff relating to the monitor, resolution, mouse or touchpad that you'd put in there. 

I agree however, its quite possible either the videodriver or X itself is to blame. Its not like it never had any bugs with high cpu usage or memory leakage. A more likely helpful solution in that case is to up- or downgrade X and/or videodrivers.

---

### Post by relay_man on 2009-09-16
Thanks very much.

---

### Post by ram2500 on 2009-09-16
I have Ubuntu (and Fedora) installed on computers with specs as good as 3 GB RAM and Athlon x2 @ 2.4 GHz all the way to a humble Pentium III Gateway with 512MB. Of course, the Pentium III is not lightning fast, but considering it has Fedora 6 and all, it worked great--better than XP, which  is what it originally had (then, it originally had 2000, I think. It now sits in a closet as it's lived its useful life and died of motherboard failure.) I'm sure the slowdown isn't because of hardware, as most users have pretty decent hardware, even above and beyond (I know that a dual-core Athlon is more than I need!). I've heard from various sources, and then again on this thread, that drivers are the main culprit. 

Posting processes is a good idea! Just run top and paste the results...those who have slowdowns can find out what might be the culprit, and if you don't know how to read the process list, then you'll get help.

---

### Post by relay_man on 2009-09-16
I've been researching some of the complaints of "Ubuntu slow with FF".
I'm hoping this will help.


[http://kb.mozillazine.org/Reducing_memory_usage_(Firefox](http://kb.mozillazine.org/Reducing_memory_usage_(Firefox))

and if it doesn't, perhaps this will:

[http://kb.mozillazine.org/Standard_diagnostic_(Firefox](http://kb.mozillazine.org/Standard_diagnostic_(Firefox))

If the information helps you, please post back and let others know.:)

---

