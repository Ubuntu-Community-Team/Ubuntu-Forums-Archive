---
title: "Software suggestions for..."
date: 2010-07-10
forum: General Help
---

### Post by Jheric on 2010-07-10
I installed Ubuntu on my Macbook a few months ago to see how far I could get in replacing Mac OS for my work environment.

I was greatly satisfied until I hit the following walls and was forced to go back to OS X before I could not fulfill my work duties:

[LIST]
[*]InDesign CS4 - Since CS2 seems to be the only version of the adobe suite that seems stable. CS2 is fine for me... but then I realized that I could not open files created by current gen CS users. Is there a reliable way to get the latest CS working? I only have 2gb ram, so I think a VM is prolly out of the question.
[*]Quicktime Pro - I handle a lot of video and sometimes editors deliver it to me in the wrong codecs... in which case I need to get it over to the correct one (usually WMV9), and I need to do it very quickly. My quicktime pro can convert MP4, FLV, MOV, h.264, and AVIs... which are the most common I have to deal with.
[*]GarageBand - When I'm mobile at conferences, we sometimes need to do on-the-spot live podcasts. Garageband is very easy to setup at a moment's notice and pull off a great podcast recording while streaming skype as well.
[/LIST]

Are these total deal-breakers? Or is there a way I can find suitable solutions in linux?

I suppose, if my only hope is to upgrade to 4gb of ram and use VMware... then I'll have to consider that. But those are the ONLY problems I have, or I'd use Linux full time. Any suggestions are greatly appreciated.

---

### Post by robsoles on 2010-07-11
I have users that get satisfactory performance from VMs set up with 768Mb of RAM on 2Gb hosts.

I don't think these are deal-breakers but I never paid Apple for 'creative' software, just a device or two that I have since shed from my life!

VLC Media Player ***might*** have what you need in streaming capabilities.

VLC ***might*** have what you need in conversion requirements.


InDesign CS4 problem you pose makes me want to ask you: Are you running 64 bit or 32 bit version of which version of Ubuntu? (Mind you: I haven't used InDesign so I'm just guessing you might be having trouble through trying to run a 64 bit install!)

---

### Post by Jheric on 2010-07-11
Well, I've been using 64-bit releases on my computers since Hardy, but I've got 32bit libraries for the things I need it for, like Wine. I wasn't under the impression that there were any reasons to use a 32bit install unless you didn't have a choice.

Photoshop is the only CS software I've successfully installed with Wine... and it's the most crucial. But occasionally, an InDesign, Flash, or Illustrator files come through, as well.

I'm starting to think that the best thing to do though, would be to upgrade my ram to 4gb, and get a go  VM install working the way I want it, as opposed to forcing Wine or other work arounds.

I would see need to solve the encoding/decoding issue, since I'm the only one who does this... but I'm guessing there must be some sort of FFMPEG-based solution I can use...

---

### Post by ov3rcl0ck on 2010-07-11
Heres some solutions:
[LIST=1]
[*]Use Gimp, Sumo Paint,Inkscape or an OpenOffice product to replace InDesign
[*]Run CS2 in wine, many people do
[*]Use FFMPEG to convert videos
[*]Use VLC to stream videos, screencasts, or podcasts
[*]Use VLC to convert if your prefer GUI, or get an FMPEG frontend
[*]Skype works native in Linux, so no issues there
[*]Run things in Wine
[*]Run things in VirtualBox, in fact theres a hack to install OS X on Vbox and QEMU
[*]All else fails, dual boot, I'm currently running a iMac(not a fan..), and I have Linux on a 365GB partition and OS X takes the rest
[/LIST]
FFMEP will convert almost any codec type, and I think theres even extensions to convert proprietary formats.

Theres an open source equivalent for just about every major software product. In fact there are several for many of them. For example Microsoft word you have Abiword, OpenOffice, then you have several closed source yet free services like Google Docs and Zoho, which both run on linux(and in the browser).

I think that in the next year or two they'll start releasing CS on Linux, and many other software products. And hopefully this inspires them to be more open.

---

### Post by Jheric on 2010-07-11
Well... it seems like there are a lot of solutions. It would appear though, that I'm going to be unable to avoid using a VM for somethings.

So... I suppose I'm curious... do you think I'd be better off running a full-screen VM of Ubuntu and running Mac OS native... rather than trying to do the reverse? (or with windows, for that matter)

If my ram is going to be split across two OSes a lot of the time anyway... maybe that's the better solution. I can't think of any linux apps I run that require a native environment. And when I finally deem my linux DE capable of replacing OS X completely, I can just clone it and reformat.

Humm... maybe that's the approach to take.

---

### Post by phantomn on 2010-07-11
For recording media i tend to use Audacity, which has the basic garageband features =]

---

### Post by robsoles on 2010-07-11
> **Jheric said:**
> ...

So... I suppose I'm curious... do you think I'd be better off running a full-screen VM of Ubuntu and running Mac OS native... rather than trying to do the reverse? (or with windows, for that matter)

...

Being that I dislike MAC OS X for the fact that it runs over the top of a perfectly good Linux and (last time I checked) Apple charge you for it, and then that I don't trust Microsoft to be in charge of any of my machines so:

Ubuntu Host running MAC OS X client and Windows XP client (VMs) all using [www.virtualbox.org]("http://www.virtualbox.org")

Like I said before, I have users that get a satisfactory experience using VMs assigned with 768Mb of RAM in hosts that only have 2Gb all up.


Have you tried any of the Windows dependent stuff you want to do in WINE as opposed to a VM? Maybe it is better to run Apple's version of an OS on their hardware - I haven't bought any of their hardware to be that sure really! (re-edited: Sorry, I see you mention use of WINE - have you tried WINE straight from the developers as opposed to Canonical's tested version?)

---

### Post by Jheric on 2010-07-12
Well... Mac OS doesn't run on top of Linux at all, but rather is Unix-based, and heavily departs from a standard Unix OS as well. I don't have a single problem with them charging for it... honestly, I think it's the most capable OS available for desktop professionals. 

I would just rather run Linux because I prefer the control and customizability. I hate the way OS X puts up baby-proofing on nearly every part of the system. It's almost impossible to personalize OS X. I also dislike the elitism of the Apple community.

That's besides the point though.

Wine is confirmed to work with Photoshop, Flash, Illustrator, and Dreamweaver, with the right set up. So we have those available natively.

For those who need more of the suite than that (it's not an issue of replacing them with other software, many of us need to open files from other people that replacements can't open), it will require a 3D accelerated VM for decent performance.

I'm willing to bet that as soon as there is a reliable way to run Adobe CS natively in Linux (whether by wine or something else), I'm guessing that the amount of creative professionals who can exist happily on linux will grow exponentially. FOSS is great... but if you make a living with your computer, you need to be compatible with the people you work with.

Thanks for all your feedback!

---

### Post by robsoles on 2010-07-12
> **Jheric said:**
> Well... Mac OS doesn't run on top of Linux at all, but rather is Unix-based, and heavily departs from a standard Unix OS as well. I don't have a single problem with them charging for it... honestly, I think it's the most capable OS available for desktop professionals. 

I would just rather run Linux because I prefer the control and customizability. I hate the way OS X puts up baby-proofing on nearly every part of the system. It's almost impossible to personalize OS X. I also dislike the elitism of the Apple community.



It's all BSD to me mate. Berkeley Software Distribution - checkout which OSs are built from it... When I tried to research the difference between Linux and Unix most boffins felt that Unix belongs to Mainframes and Linux is for PCs - maybe I didn't try hard enough to find the absolute truth of it all!

---

### Post by Jheric on 2010-07-12
I suppose. It's probably largely a question of semantics. Tho, BSD distros use BSD kernels... and Linux distros use Linux kernels. 

Interestingly though, Arch Linux uses a Linux Kernel but adopts BSD file structures and init system. At the end of the day though, they don't really work all that much different, from a user standpoint. *hides from the BSD nuts*

---

