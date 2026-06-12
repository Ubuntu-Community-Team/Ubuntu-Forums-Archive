---
title: "Umintu - Download / Build?"
date: 2010-11-05
forum: General Help
---

### Post by zen-geek on 2010-11-05
Hi, 
I'm a Mint user who wants to move further upstream. Despite how awesomely easy it is Mint does make some changes to Ubuntu, and I feel like I'm missing out. I want ALL the glory of Ubuntu - But I REALLY like my GUI tools (mint is VERY good when you don't have half an hour to find the right command to do something) and I share this PC with others who also like the Mintiness.

Is there a remix/remaster that has the mint tools or should I just add all the packages separately.

Apart from this is there anything I'm going to miss?
I guess I should read the mint packages and see what else there might be, but if someone's already done it that would be easier.

Also, it's really hard to find remasters, is there a site where people post their work like they do for themes?

---

### Post by coffeecat on 2010-11-05
> **zen-geek said:**
> Apart from this is there anything I'm going to miss?

Restricted multimedia codecs and libdvdcss2 for playing encrypted DVDs come to mind, none of which come in a default Ubuntu installation. But they're easy to install.

Out of interest, what GUI tools does Mint have that Ubuntu doesn't which specifically obviate the need for using the terminal?

---

### Post by zen-geek on 2010-11-05
Thanks for the reply. I've been researching medibuntu and various options for codecs.

I'm not sure if any of the little GUI tools are specific to mint. They just seem to be for tweaking different aspects of the system. I'm taking a new version of ubuntu out for a spin tonight to see if there's any major differences. 

Also [http://ubuntuforums.org/showthread.php?t=1511877&page=1](http://ubuntuforums.org/showthread.php?t=1511877&page=1) and [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1509860](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1509860) give some good info on how to instal mint packages if anyone else is looking. I was searching for the wrong thing, there a BIT more info if you search for "mint tools on ubuntu"

I'll keep you posted if I find any major differences.

---

### Post by coffeecat on 2010-11-05
> **zen-geek said:**
> I've been researching medibuntu and various options for codecs.

Once you've got Medibuntu enabled, quite the easiest way is to install the medibuntu metapackage non-free-codecs. That brings in either w32codecs or w64 codecs plus the Ubuntu repository metapackage ubuntu-restricted-extras which itself pulls in flash, iced-tea plugin for browser java applets, other restricted multimedia stuff, libdvdread4 and MS core fonts. Then, all you have to do is install libdvdcss2, also from Medibuntu, and you're set up on the multimedia front.

---

### Post by zen-geek on 2010-11-05
Awesome tips on the Media issues. I guess everyone goes through this at the start?

I just took Maverick for a spin and only noticed two tools that seem different. ( Apart from the main "Mint Tool" set-  backup, updater, software manager, mint menu etc.)Also, I might just not know where to look.

NDISwrapper gui. I'm so sick of my crappy netgear wireless dongle I'm going to buy a 50m CAT5 cable, or an out of the box answer. But for people who need wireless the NDISwrapper GUI is awesomely handy. 

The other one is system profiler/benchmark. The Ubuntu version asked me a bunch of annoying questions so I closed it. Mint version is just like device manager in WinBlows, See what's connected where and performance, stats drivers etc. I only know lspci as far as hardware investigations go in terminal. I'm sure I could google some, once I get my Network cable. (Hardware profile is rarely useful but when it is you it's nice to have it nice and handy)

Looks like everything else is the same, or just requires installations. In fact it looks like Ubuntu has extra tools that mint doesn't (or that mint hides in the back somewhere).

---

### Post by coffeecat on 2010-11-05
> **zen-geek said:**
> I'm going to buy a 50m CAT5 cable, or an out of the box answer.

A little more expensive but less likely to cause nasty accidents than 50m cable would be a couple of ethernet over mains devices. Be warned though. Very complicated installation procedure as follows:

1 - Plug in.

2 - Use.

:wink:

One great advantage is that through the magic of networking, if you buy a third ethernet over mains device and plug another computer in somewhere else in the house, your router will cope with it just fine. I have four altogether. 1 - router. 2 - main computer. 3 - network printer. 4 - Sony PS3.

You can set an encrypting password on these devices to guard against the possibility of someone listening in on the traffic. I have the Devolo ones. One advantage of this make is that they include Linux configuration software as well as Windows. Which is nice. :cool:

---

### Post by zen-geek on 2010-11-07
WOW...
I never even knew such a thing existed. We're pretty weak on choice here...You need to know what you're looking for so you can order it online. Electronics stores, and even most computer stores have nothing in the way of choice. The same 3-5 models of PCI cards and Dongles. The same 3-5 Routers... and they all suck, poor features, limited drivers RAAAGH makes me rage.

---

### Post by coffeecat on 2010-11-07
Whereabouts geographically are you?

It sounds as though you've done your research, but a couple of things you need to know about ethernet over mains. I'm a bit hazy about the details, but there are (at least) two incompatible protocols. Devices from different manufacturers that use the same protocol should work with each other, but it's best to choose your make and stick with it.

With the Devolos that I use [ [http://www.devolo.com/](http://www.devolo.com/) ] they do 14, 85 and 200 Mbit/s. 14 is a bit slow but the cheapest. I use the 85s. Be aware that this is a theoretical maximum. Poor wiring, multiway adapters and surge protectors can all reduce transmission speed. I've heard it said that if you have one device on one ring mains, and another on another, this will reduce the speed, but I've not seen this. It depends on the quality of your fusebox (tripswitch box) I suppose. The Devolo configuration software I mentioned can measure transmission speed for you.

Be warned also that the Devolo Linux software (or the one I got) is terminal based and you have to compile it from source. But they give clear instructions for Ubuntu.

---

### Post by zen-geek on 2010-11-10
Rural/semi-rural Australia. 
Like I said you can get anything off the net, but if you walk into an electronics store, or a computer store - the range is pretty limited.

Don't get me wrong, we're not tech Challenged, it's just one area of consumer choice that has been thoroughly overlooked in most parts of Aus.

---

### Post by coffeecat on 2010-11-10
> **zen-geek said:**
> Don't get me wrong, we're not tech Challenged

Ah no, I wasn't assuming that. :) I was wondering where you were before I posted the Devolo link, which I did anyway. I can't see an Australian link on the Devolo site but there are plenty of other makes to choose from.

Good hunting!

---

