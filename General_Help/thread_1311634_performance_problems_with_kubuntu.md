---
title: "performance problems with kubuntu"
date: 2009-11-02
forum: General Help
---

### Post by alfonz19 on 2009-11-02
Hi, I'm just looking for replacement for my old kde 3.X and just tried all three distributions (everyone is terribly slow compared to 3.X). But KDE version looks ok, and I'm used to it. Everything works ok, even menu is fast, but launching apps is UNBELIAVABELY SLOW. Even after prelinking libraries. Then I ran top.

What the hell is this? Ok, I've got 5 years old athlon 3000+ 64bit BUT why plasma-desktop is PERMANENTLY consuming from AT LEAST 48.9 % to 90% of cpu even if I explicitely turned off all desktop effect. And just to be sure system is behaving super-slow his buddy Xorg helps him with another "at-least" 30-60%, with occasional aid of some another process which just don't want to stand in back with his cpu peak. This CPU is not fast, but not slow. What interresting action is Kmix performing to apologize 5% of cpu load, when NO MUSIC is playing, no window of kmix is visible neither its icon!!!??

Can somebody tell me this is "something wrong" (what, what) and not just new nice feature?

EDIT: just to be sure you're not get confused by anything which is not actually problem: 
Installed from alternative cd. System was acting slow from start, not just after I "corrected" settings. System has not-bad-5-years-old-graphics-card. Good enough for CS or another point&click applications :) So, I expect, EXPECT, it's good enough for icons on desktop too. Hardware drivers installed. Restarted. Every single setting in "hey-look-its-so-nice" menu deactivated, then don't-use-desktop-effect checkbox checked. Every mention about animaniton turned to fastest or something similar. OpenGL switched to something I do not know but which sounded faster. .xsessionerrors almost empty with anything unusual.
so? What's this all about?  Is KDE 4.3 desktop icons truly more cpu intensive than, say, physical model in cs-source??? Or, let me think, than 720p HD movie !!!?

EDIT 2 (in reply to stdPikachu): my machine is single core 64 bit, os version is 32bit, does not suffer from any memory problems (1gb total, after start half is gone - ok, slight problem then :) , but this amount is not increasing), no hdd problems.

---

### Post by stdPikachu on 2009-11-03
Same problem here, although not as severe. plasma-desktop routinely spikes up to 100% CPU usage on one core and sucks up a huge amount of memory - currently 737MB (and I thought explorer.exe was bad). Desktop effects have been turned off from the get go and only the default plasma doohickeys are turned on (apart from the network management one, that's off as I don't use it).

kmix also showing a CPU load of 2-5%.

Is there any way to get a sane trace/dump/log of what plasma is doing?

64bit install from the alternate RC disc on a dual core intel.

---

### Post by alfonz19 on 2009-11-03
> and I thought explorer.exe was bad sadly, you're right. I do not understand why gnome, kde, etc started competing with M$ in niceness of GUI. What's so bad about continuing winning in usefullness? I definetely quit windows and moved to ubuntu when there was latest version 7. Can anybody tell me ONE significant (or even insignificant) improvement except eye-candies in any environment since that version to explain me surprisingly growing hw requirements and slowing down reaction times?

---

### Post by nerdy_kid on 2009-11-03
ouch

im using KDE, i have noticed that Xorg eats CPU big time with desktop effects off, at least when watching videos.  Kwin always uses ~3%, but so does compiz.  No clue with plasma-desktop, it happens now and then to me; I just kill it and restart it.

---

### Post by alfonz19 on 2009-11-03
ok, I'll try kill him and see what happens :)

I've noticed interresting facts. In my hunt for usable OS I currently have got installed these OSes:

on PC A: xubuntu 9.10, ubuntu 9.10, kubuntu 9.10 and kubuntu 8.04 (with kde 3)

on PC B: kubuntu 9.04 ubuntu 9.10, xubuntu 9.10

some surprising facts:
A is about 1/5 more "stronger" than B, and has non-integrated graphic card while B does not.

A with kde 3 is fastest and it's not even close, when comparing to anything else. BUT, its quite weird, but it is slower with any other OS when compared to B computer with ubuntu 9.10 booted. On A is ubuntu noticebly slower then xubuntu, while on B it's ubuntu A LOT faster then xubuntu. 

it's quite confusing. Suppose I buy a new pc. What os should I install??? :)

---

### Post by nerdy_kid on 2009-11-03
i agree with the fact that it is confusing, i am lost!

When ever I am installing ubuntu for someone else, I have to decide; jaunty or karmic?  So far ive stuck with jaunty, i personally dont mind karmic, but i feel safer with jaunty.

---

### Post by stdPikachu on 2009-11-03
From the looks of reports across the net and (especailly) at the KDE bugtraq this is a reasonably widespread issue - some posts say buggy plasmids* are to blame (not applicable in this case as I'm just using the defaults), others say plasma is bugged and that restarting it is the only options (works for about five minutes then CPU and mem are gobbled again), other stay restart hal/udev and your problems will go away (again, doesn't work for me).

No solutions or workarounds immediately visible. Anyone here tried running an strace? Not quite sure how to go about it with an "embedded" app like plasma but happy to give it a whirl.

* Pun intended. Even moderate use will turn you into a psychotic lunatic :)

---

### Post by alfonz19 on 2009-11-03
sorry, I'm not your men :) I do not have any unix-debugging knowledge. But like you, I would be very pleased if problems fade away, since as I said kde was my favorite distro.

I like (and if there's time I used it) one programming related (mostly, but generally also) rule. If it's not working, it's tricky & buggy & overally complicated and it's benefits are questionable then throw it away since rewriting from scratch is faster and can result in totally different and overally better solution.

Let's look at kde 4.X environment without mercy. It's buggy, on my pc unusable. What's it's benefit over 3.X variant? Is it fact, that I can place unneeded crap on different parts of desktop instead of having responsive pc? Sounds like throw-away time to me, since original strategy was bad. KDE etc. should try to improve its efficiency as a tool for launching wanted apps and allow working with them easier not trying to become replacement for sex :)

---

### Post by captaincrook on 2009-11-04
Plasma-desktop and Xorg are both chewing memory like beavers on wood. Combined memory usage hovers around 400MB which is tooooo high.

---

### Post by nerdy_kid on 2009-11-09
i also noticed plasma and xorg eating RAM.  have no idea why....i dont have many plasmoids running (6, not counting the default panel)  nor do i use activities (too buggy).  I do have 4 desktops but im sure they arnt using 300 mb of ram lol (and yes, they all are empty)

right now my system is using .68gb of RAM with all libraries loaded -- qt 3.5, kde 4, GNOME, GTK

:confused:

---

### Post by nerdy_kid on 2009-11-09
I do have to say that KDE 4 started out as Linux's version of (the infamous) Windows Vista, but it has gotten WAY better really fast -- i tryed 4.0 out and it was unusable!  I think they are doing a great job; cant wait till 4.4!

---

### Post by alfonz19 on 2009-11-10
yep. 

But The question is: what distro is meant to be used for work? Gnome-slow, xfce-less_slow_but_slow, KDE 3-acceptable_but..., KDE4-unusable. 

Call me old-fashioned but I expect slower reaction time from significantly faster computer not same or worse just because of newer version of OS. (I would kept installed kde 3 if it still be supported). And there is ABSOLUTELY NO new functionality in all named WM in last 3 years. Who cares about simplified chatting or possibility of movable crap? If there CAN be three different WM for eye masturbation, why there can't be one for work?

And it's not problem of ubuntu distributions since another vendors are using these crappy window managers as well.

So, what do you advice as a good windows manager? And by good wm I mean unbelievable fast, easy, simple, intelligent, making-work easier and trying to automate routine user work. Is there one?

---

### Post by nerdy_kid on 2009-11-10
i dont think it is kwins fault that the pc is eating ram/cpu etc.  kwin is getting better, but i would recommend compiz who want seamless prettyness :D

just a wild thought, does the RAM eating happen only after you hibernate???


and KDE 3.5 is still around, you can download a version of karmic for kde 3.5 at [www.kubuntu.com](www.kubuntu.com)

---

### Post by nerdy_kid on 2009-11-10
> **alfonz19 said:**
> yep. 

But The question is: what distro is meant to be used for work? Gnome-slow, xfce-less_slow_but_slow, KDE 3-acceptable_but..., KDE4-unusable. 

Call me old-fashioned but I expect slower reaction time from significantly faster computer not same or worse just because of newer version of OS. (I would kept installed kde 3 if it still be supported). And there is ABSOLUTELY NO new functionality in all named WM in last 3 years. Who cares about simplified chatting or possibility of movable crap? If there CAN be three different WM for eye masturbation, why there can't be one for work?

And it's not problem of ubuntu distributions since another vendors are using these crappy window managers as well.

So, what do you advice as a good windows manager? And by good wm I mean unbelievable fast, easy, simple, intelligent, making-work easier and trying to automate routine user work. Is there one?



re-reading your post, sounds like you want linux on a 350Mhz pc :P
id go with SliTaz or Damn Small Linux.  (actually id buy a new PC!)
or you could go command line...thats the fastest!!!:lolflag:

---

