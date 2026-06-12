---
title: "How do I remove wireless drivers in Maverick?"
date: 2011-04-23
forum: General Help
---

### Post by james_mcl on 2011-04-23
I'm reaching the point where, with Hardy nearing the end of its lifespan, unless the repeating keyboard bug that's been afflicting all my attempts to upgrade (it's very like what's described at [http://ajaxxx.livejournal.com/62378.html](http://ajaxxx.livejournal.com/62378.html) and [https://bugzilla.kernel.org/show_bug.cgi?id=9147](https://bugzilla.kernel.org/show_bug.cgi?id=9147)) is cured in Natty, I'll have to get a new computer.

I can't remember whether Intrepid was the first distro in which fiddling around with ndiswrapper wasn't necessary to get the BCM4318 to work; however as that's the only thing I can think of which might be a common thread linking the post-Hardy installs, I'm trying to completely uninstall all the wireless firmware and drivers in Maverick.

I'm guessing I'll need to go to Synaptic and uninstall b43-fwcutter and bcmwl-modaliases, but does anyone else know of anything I might need to do?

(I've got an Ethernet cable, so connectivity won't be an issue.)

Thanks,

James McLaughlin.

---

### Post by james_mcl on 2011-04-23
Just edited the original post - insofar as there's a difference, it's both firmware and drivers I'm looking to remove.

---

### Post by ClientAlive on 2011-04-23
> **james_mcl said:**
> Just edited the original post - insofar as there's a difference, it's both firmware and drivers I'm looking to remove.

I'm not sure I understand your question or the problem you are having. I'm a newbie to this and not sure how much I can help but I see that the wireless card you mentioned looks like the same one I have. Mine is . . .

```
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

I am running 11.04 and getting my wireless working was a bit of a challenge. If that is what you are asking about (I'm not sure) I can offer the link to the thread where my wireless issue was solved. The hard part was figuring it out the first time. It would be easy to repeat now.

HTH

Sorry if I'm off base here.
:)

---

### Post by KegHead on 2011-04-23
Hi!

Just add additional drivers via administration.(10.10)

That's all I did.

KegHead

---

### Post by james_mcl on 2011-04-24
ClientAlive - I'm sorry, but you've completely misunderstood my question. I'm trying to completely remove everything related to wireless functionality from Maverick - if this has any effect on the bug I've been experiencing, I'll be using an Ethernet cable instead from then on.

KegHead - I'm trying to remove the wireless drivers and firmware, not add new ones.

(I suspect the wireless drivers, fwcutter, etc of causing the keyboard bug because the distro in which it started - Intrepid - MAY also have been the first one where I didn't use Ndiswrapper for wireless. I'm trying to investigate this further.)

---

### Post by ClientAlive on 2011-04-24
> **james_mcl said:**
> ClientAlive - I'm sorry, but you've completely misunderstood my question. I'm trying to completely remove everything related to wireless functionality from Maverick - if this has any effect on the bug I've been experiencing, I'll be using an Ethernet cable instead from then on.

KegHead - I'm trying to remove the wireless drivers and firmware, not add new ones.

(I suspect the wireless drivers, fwcutter, etc of causing the keyboard bug because the distro in which it started - Intrepid - MAY also have been the first one where I didn't use Ndiswrapper for wireless. I'm trying to investigate this further.)


james_mcl, have you seen a bug report or something else that leads you to believe this driver is the problem? I suppose it is possible that it's not a driver being installed but a driver or some dependency that is missing that is causing the problem.

If you can describe the problem in detail I'm willing to research it and see what I find. You might be able to keep your wireless and be rid of the problem.

If you are certain this is what you need to do then the following describes the process. At the very least you could troubleshoot by this. If the problem persists come back and let us know. We'll help.

You can find some of these things through Synaptic package manager. For instance - if you know you have b43-fwcutter installed you can type b43 into the search field in Synaptic and a small list of items to do with b43 will come up. b43-fwcutter will be one of them and you will be able to see from the list whether it is an installed item or not. If the box to the left of the item is solid and green it is installed. There is also a filter entitled "Installed" in the left hand pane. If you click it it will show only the items in the list that are installed (if any).

Right click on the item of your choice from the list and you will be given a drop down menu with available options listed. If it's an item that is installed you will have options like: "mark for reinstallation", "mark for removal", "mark for complete removal" and a couple others. When you make a selection from that list it will mark the item for that action. Then, to carry the action out, you need to click the "Apply" button which is located to the left of the filter field.

I'm sure there is a code that can be put into the terminal that will tell you the installed drivers on your machine but I don't know what it is. I think that even though there may be many drivers that come with the operating system, they are not all being used. I think it is just the one or ones that are installed that are used on the system. I'm getting into deep water here at my level of understanding though (limited). Someone check me on this part please.


HTH

Jake

Oh! By the way! Check out [www.googlubuntu.com](www.googlubuntu.com) it is a google for ubuntu and you can use it to find all kinds of stuff specific to Ubuntu.
-----------------------

Update: I just did a search on googlubuntu and I see a lot of results talking about bluetooth and wireless keyboads in them. Are you using a wireless or bluetooth keyboard?

---

### Post by james_mcl on 2011-04-25
> **ClientAlive said:**
> james_mcl, have you seen a bug report or something else that leads you to believe this driver is the problem?
I have no hard evidence as to what could be the cause of this bug. All I know is that it has occurred in every distro later than Hardy I've installed on my Compaq Presario.

The only difference I can think of between Hardy and the later distros that I might be able to do something about is that after a certain point, instead of needing ndiswrapper, wireless drivers were handled differently. (I'm not sure what that certain point is - I'm rather clutching at straws here.)

Though it's clutching at straws, I'm naturally eager to at least experiment with this and see what happens. I'm encouraged in this by the fact that in the comments for Launchpad bug 124406 somebody did try this and it resolved the problem.

> 
I suppose it is possible that it's not a driver being installed but a driver or some dependency that is missing that is causing the problem.

If you can describe the problem in detail I'm willing to research it and see what I find. You might be able to keep your wireless and be rid of the problem.

I can describe the problem - but I've been following pretty much all the research that's been done into this and a fix looks extremely unlikely. I'll describe the problem first and then describe the related bug reports and blog postings.

Every so often, while I'm typing - I could be typing something in gedit, or in Firefox's address bar, or anywhere else - the system will act as if one of the buttons I have pressed is being held down. In the least severe case, this results in a character being endlesslyyyyyyyyyyyy repeated. In the worst case, if the key was Delete or Enter, the consequences can be unpredictable and catastrophic.

Closing the application in which this is happening, or switching to a new tab, simply causes the bug to affect whichever other application is now "at the front".

Whether this can be stopped seems to vary - when I booted into Maverick yesterday, no other key presses were recognised while this was going on. I think I managed to get it to stop by closing all other applications - it's the first time I remember it doing so.

(Not surprisingly, I'm typing this while booted into Hardy!)

I've spent a while trying to research this and the prognosis is not good; especially as it seems to indicate that several different bugs have caused the same symptom going back several years:

[https://bugzilla.kernel.org/show_bug.cgi?id=9147](https://bugzilla.kernel.org/show_bug.cgi?id=9147) describes a bug with identical symptoms. However, this also causes the following messages to appear in dmesg:

atkbd.c: Unknown key released (translated set 2, code 0xe0 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e060 <keycode>' to make it known.

which does not happen in my case.

It's not clear what's causing it, and a fix hasn't been found despite its being reported in 2007.

Another run in with the repeating keyboard is described in:
[http://ubuntuforums.org/showthread.php?t=1048476](http://ubuntuforums.org/showthread.php?t=1048476)

I can certainly empathise with pmcginley - who was also able to point to a dual-boot system in which the problem affected one OS but not the other. I tried everything suggested in that thread, but to no avail.

(hmmm... can't remember if I tried the external keyboard - I'll get one out and have a go.)

On the other hand, pmcginley's problem also affected Hardy. Various other people affected by the bug posted, quite a few non-Ubuntu distros were mentioned, and no solution was ever found.
(pmcginley states that it mysteriously fixed itself in the end. It hasn't for me, however.)

[https://bugzilla.kernel.org/show_bug.cgi?id=9448](https://bugzilla.kernel.org/show_bug.cgi?id=9448) also describes this problem.
(Despite the claim that high system load exacerbates the problem, in my experience they're unrelated.)
It mentions Feisty Fawn and Gutsy Gibbon installs being affected.

(I did once encounter the bug in Gutsy, when I was backing up data before upgrading my Gutsy-Hardy dual-boot to Hardy-Intrepid. Just once, after months of completely stable operation.)

In [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/124406?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/124406?comments=all)
Theodore Book mentions having tried removing the Broadcom firmware and moving over to ndiswrapper on this thread. For him, though not everyone, it solved the problem.

Or at least, it did up until last May, when according to [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194214](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194214) it affected his Lucid install.

The bug report contains the following, very pessimistic, comments from developers:

"Having not heard back from the original bug reporter Guy Gur-Ari, I'm going to close this bug as it's growing wildly out of control and hard to follow from a developers point of view. There are comments all over the place indicating this is fixed with Jaunty, while others mention it's a regression with Jaunty, or some say this is an issue on some hardware and not others"

and

"Please be aware that Leann closed this bug because I suggested to him doing so in IRC. He is absolutely right, the bug has come into such a state that is really impossible to fix. There are several similar, yet different issues that have been lumped together here by now.

This does not mean the underlying issue(s) (one should assume there are many among the ones reported here) will not get fixed, to the contrary. Divide and conquer. Let people report their problems individually until we find the root cause(s). The alternative is a tangled mess and 0 progress. The problems that have the same root cause can then be consolidated as duplicates. But let's keep them separate until then."

There are several duplicate bug reports, which I won't try to exhaustively list. However, we now come to

[http://ajaxxx.livejournal.com/62378.html](http://ajaxxx.livejournal.com/62378.html)

This is a blog posting by Adam Jackson, in which an underlying factor relating to several, probably the majority, of these problems was uncovered and described. Unfortunately, what it comes down to is "the use of signals instead of threads always leads to a race condition in X which can cause this.", and it sounds as if tearing up X to replace this with a threaded architecture would require a massive developmental effort and simply isn't going to happen.

(Note that in the thread mentioning bug 9147, people have stated that they do not believe that it's a contributing factor there.)

> 
If you are certain this is what you need to do then the following describes the process.


I've snipped this bit because I did already know that I could uninstall b43-fwcutter and the like that way - I'm primarily interested in finding out if there's anything else I need to do as well as going into Synaptic.

> 
Oh! By the way! Check out [www.googlubuntu.com](www.googlubuntu.com) it is a google for ubuntu and you can use it to find all kinds of stuff specific to Ubuntu.

Thanks for the hint, I'll give it a go!

> 
Update: I just did a search on googlubuntu and I see a lot of results talking about bluetooth and wireless keyboads in them. Are you using a wireless or bluetooth keyboard?

No, it's just the keyboard built in to the laptop.

---

### Post by ClientAlive on 2011-04-25
Sorry about going mia for a bit there james_mcl. I started a new job today and was attending to that.

Seems like you've really done your homework. What you describe seems very odd. Of course, the first thing that comes to my mind is faulty hardware. It's the only common link that would make sense under the circumstances. But you say people with varying hardware have experienced this. Hmm . . .  Then what about environmental conditions? Overheating or trauma? Character encoding?

I Just logged back on here a few minutes ago but this does seem sort of fascinating - in an odd way. I'd like to check some things out. If I find anything out that might be useful I'll let you know. It sure would be nice to have some details about your system though. Can you give us some details? Year, make model, hardware, etc?

Thanks
Jake
------------------------------------------------------
Well. The problem is - how do you diagnose something like this? As you mentioned, conditions seem to vary so much. As I read about this, a whole lot of ideas come to mind; that, if I were in front of your computer (or if it was my computer - if you want to look at it that way) I would look into. I'm not really sure how to help in a situation like this. I'm sure there is a lot you have looked into. I came across a thread from 2000; that, if it's describing the same problem, sounds like something like this was affecting Windows machines. What the OP suggests is something fundamental that is tied to how computers work.

This is the link to that article:  [http://www.ntcompatible.com/Fix_for_Sticky_Keys_Tested_and_Proven_t8816.html](http://www.ntcompatible.com/Fix_for_Sticky_Keys_Tested_and_Proven_t8816.html)

All the guy does to describe it is call it the "sticky keys" problem". Very odd. I'm sorry I'm not more knowledgeable. If what they are talking about in the post linked above is the same thing I would find that very intriguing. That would mean that it is something fundamental (if it isn't tied to any particular o/s).

Do you think it could even be faulty keyboards? I mean, they use the same generic parts in all kind of different model computers don't they?

I don't know. I've seen this thing associated with X, with the kernel, with the keyboard itself, even with the game, Minecraft! Enough to make a person mad (by that I mean crazy mad, not angry mad).

[http://www.minecraftforum.net/viewtopic.php?f=17&t=145799](http://www.minecraftforum.net/viewtopic.php?f=17&t=145799)

I'll keep looking around, but I don't see how something like this could be solved unless you are sitting in front of the effected computer and know and remember absolutely everything about its history/ use.

---

### Post by james_mcl on 2011-04-26
> 
Seems like you've really done your homework. What you describe seems very odd. Of course, the first thing that comes to my mind is faulty hardware. It's the only common link that would make sense under the circumstances.

I have to disagree. Consider that I have a laptop with a Hardy/Maverick dual boot. The problem affects Maverick but not Hardy. As the underlying hardware remains the same whichever OS I'm booted into, I consider that to be very strong evidence that it's a software problem.

> 
It sure would be nice to have some details about your system though. Can you give us some details? Year, make model, hardware, etc?

Sure thing. It's a Compaq Presario laptop. The full model number is either v5245EU or dv5245EU - it appears to be part of the V5000 family AFAICT. (Compaq's numbering wasn't exactly consistent.)

Date of manufacture - I don't know, probably between 2005 and 2007.

Its CPU is an AMD Turion 64 ML-34 CPU (1.8GHZ, 1 MiB cache).

It has 1 GB of RAM, of which 128MB is used/shared by the graphics (ATi Radeon Xpress 200M - I THINK that's integrated and not a discrete graphics card - could be wrong.)
The RAM is DDR - that is, DDR the first, not DDR2 or 3.

HDD - Size 100MB, PATA (IDE).

The wireless card is a Broadcom BCM4318. Even by Broadcom's standards, its Linux compatibility was dire, and it took a lot of fiddling with ndiswrapper to get it working in the earlier distros.

The touchpad is - I think - made by Synaptics.

> 
This is the link to that article:  [http://www.ntcompatible.com/Fix_for_Sticky_Keys_Tested_and_Proven_t8816.html](http://www.ntcompatible.com/Fix_for_Sticky_Keys_Tested_and_Proven_t8816.html)


That is interesting - it's the first time I've heard of anything like this affecting a version of Windows - or indeed the "machines running faster than PS2 was designed for." theory.

---

### Post by james_mcl on 2011-04-26
A quick update - Theodore Book has been in touch to say that, as far as he remembers, removing the wireless drivers required nothing more than a trip into Synaptic.

In addition, the fix might not have been ineffective in Lucid - it seems he just decided to live with the problem because he'd be getting a new laptop soon.

I'm going to boot into Maverick and remove - I think it was b43-fwcutter and bcmwl-modaliases - well, I'll know when I get into Synaptic, and we'll see what happens.

Thanks for all the help so far!

---

### Post by ClientAlive on 2011-04-26
> **james_mcl said:**
> A quick update - Theodore Book has been in touch to say that, as far as he remembers, removing the wireless drivers required nothing more than a trip into Synaptic.

In addition, the fix might not have been ineffective in Lucid - it seems he just decided to live with the problem because he'd be getting a new laptop soon.

I'm going to boot into Maverick and remove - I think it was b43-fwcutter and bcmwl-modaliases - well, I'll know when I get into Synaptic, and we'll see what happens.

Thanks for all the help so far!


Right on.

Hey, there's also a "kernel-source . . ." something associated with fixing the broadcom 4318 wireless issue. If I remember tight though it might be an alternative route. So maybe it's more of an "either/or" type thing rather than a "both/and" type of thing.

Thanks for the specs. If nothing else, if you get you issue resolved (and I hope you do), this would be an interesting case study. If someone ever really figured this thing out it sounds like it would help a lot of people.

Jake

---

### Post by james_mcl on 2011-04-28
Update:

Tried using the proprietary firmware by activating it in "Additional Drivers". This did not resolve the issue.

Uninstalled b43-fwcutter in Synaptic. Opened terminal.

```
sudo modprobe -r b43 ssb
```

Added b43 and ssb to /etc/modprobe.d/blacklist.conf

Rebooted. Used Ethernet cable to connect to Internet.

Unfortunately, the bug still persists. I guess the next steps are to get a USB hub and keyboard, and to try a full upgrade to Natty.

---

### Post by ClientAlive on 2011-04-28
> **james_mcl said:**
> Update:

Tried using the proprietary firmware by activating it in "Additional Drivers". This did not resolve the issue.

Uninstalled b43-fwcutter in Synaptic. Opened terminal.

```
sudo modprobe -r b43 ssb
```

Added b43 and ssb to /etc/modprobe.d/blacklist.conf

Rebooted. Used Ethernet cable to connect to Internet.

Unfortunately, the bug still persists. I guess the next steps are to get a USB hub and keyboard, and to try a full upgrade to Natty.


Sorry to hear that brother. Hope upgrading will help. Just to be clear on something though - what I was saying about the wireless keyboards is that I was seeing threads where this was causing problems for people, not a solution. They were talking about a bug or problems with them.

Sorry I couldn't help more. It's sad to hear about.

Jake
:(

---

