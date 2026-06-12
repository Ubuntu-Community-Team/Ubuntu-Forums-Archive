---
title: "hwo to use more RAM in 9.10"
date: 2010-03-06
forum: General Help
---

### Post by woofy on 2010-03-06
currently have 9.10 clean install to 120gb hdd with 1gb ram and checked the box during install to encrypt home directory. system is slow, bogs down, and apps freeze frequently. after i wait a bit, the apps unfreeze for my next command but freeze again. cant run more than one app at a time.

used to have 9.10 (upgraded from 9.04) on a 40gb hdd with 1gb ram and no home directory encryption. ran perfectly.

usually only have transmission, firefox, nautilus, terminal, and system monitor open. system cant handle them. check system monitor and ram usage never exceeds 50%. swap (set at 3gb) never exceeds 90mb. 

did the research and only found complaints of too much ram/swap usage. saw lots of instructions on how to limit memory usage. in my case, i want to allow the system to max out the ram/swap. dont know if this is the problem or my encrypted home directory is the problem, but i'd like to try to increase the amount of ram ubuntu uses and see if it performs better.

am i way off base here? how do i let ubuntu max out my ram/swap?

thanks

---

### Post by Rasa1111 on 2010-03-06
hey man, 

 Im sorry I cant help with your main question. 
 But I have wondered the same, if it's possible to make Ubuntu use more available RAM. 

I am pretty new to all of this, 
and I have made this suggestion before here, to others...

SO maybe try it, see if it helps? 

 Is your " Visual effects" on?

 I installed 9.10 on a friends machine the other day, 
His processor is 2.8 ghz, and he has 4 gb of RAM. 
(better than my own, which runs great!.. but i also have the visiul effects off)

 The system ran like absolute crap, with lots of freezes, and not being able to have more than one thing open at a time, without freezing entirely, so that a reboot was needed. 

 after about 2 hours of messing around ( dang newbs) lol....

 I went into the system>appearance> visual effects tab, and selected the top, "none"
 ( the middle option was selected by default). 

 after that, his machine runs beautifully now. 

 very simple I know, but after I found it, It did make a whole world of difference. 

Sorry not to be of more help. 
but i hope it does help/

good luck. 

rasa

---

### Post by woofy on 2010-03-06
rasa1111

changed the appearance thing to 'none' just like you recommended and works just like you said. checked on a couple things and all seems to be working like a champ now. 

i cant believe how simple that was! thanks for the reply. glad you happened to be online and reading through the forums.

now that my problem seems to be fixed, i am still curious to know if i can max my ram or what. still sittin at 50%. feels like im wasting the other half. why would i even bother ever getting more ram if my box aint gonna use it?

will leave this unresolved for now since id still like a solution to the ram question but thanks to rasa1111 for the solution to my performance issue. awesome!!

---

### Post by Rasa1111 on 2010-03-06
haha, Niiice!!  

 Soo happy it worked for you.:D
( you might be the only person to have taken said advice from this newb) lol

woohoo! after all the help ive received here, it feels good to help someone else. :lol:

It is a much nicer experience when it actually works eh? lol

 I also really would like to know the answer to your question myself though. 
Thanks for letting me know it worked. :)

edit:...  ohh, I do remember reading in one of the many Ubuntu books I downloaded, something about getting Ubuntu to recognize (and possibly use?) up to 4gb of RAM? hmmmm
ill have to go back and find that, I know i saw it somewhere... .... lol

  <3 Rasa

---

### Post by MasterJS on 2010-03-06
To use complete 4 GB, you would need to have the 64bit version. To use this, you would need to make sure that your processor is indeed capable of 64 bit (though all modern processors are capable but its never a bad thing to check). The problem with swap is that it is using hard drive space as RAM. This is naturally going to be slower, and even slower depending on your hard drive's read/write speeds. The best way to go would be getting another GB of RAM. And finally, with the visual effects, the problem could more than likely be with the video card.  Your friend's system seemed more than capable of running the visual effects, Compiz as the program is called, and I would attribute the problem being the video card.

EDIT: Also, for your question about staying at 50%. The amount of RAM used depends on the programs you are using. I have an older PC with just 1 GB of RAM, running 9.04, and it has maxed its RAM out. This i could attribute to trying to run music, video, and a couple of other programs. The swap has never gone above 20% for me.

---

### Post by lildigiman on 2010-03-06
Just Like MasterJS said, Visual Effects most likely is a graphics card thing, though if you either have a graphics card thats not being used to its fullest potential, or just a really crappy card, Visual Effects will take up a lot of the PCs CPU power (at least I have noticed on some PCs).

The weird thing is, I have a Pretty crappy Dell, P4 (2.8GHz) with 512MB ram (I just acquired it) and it runs full compiz fusion without any problem, and theres no freezing of the PC, and it runs at about 50% ram no swap space.

---

### Post by woofy on 2010-03-09
Thanks for all the feedback. Definitely somethin wrong with my install. Do have 64bit AMD processor so all should be good. Most likely also have crappy video card, but didn't have these problems with 9.04. At this point will probably just have to reinstall 9.04 and then upgrade to 9.10 rather than installing 9.10 directly. Can't figure it out.

Thank for the help. You all provided a lot of helpful info.

---

### Post by quequotion on 2010-03-10
I just made a related post. I'm trying to do anything I can to max out my RAM usage.

Note that maxing out the ram is exactly what I intend to do, not make anything faster or better, but just make sure it is in fact possible to max out 8GB of ram in Karmic (amd64 of course). 

So far, even with a ridiculous amount of CPU, GPU, and hard diskt intensive applications running simultaneously, I can't use more than 1.2GB....

---

### Post by von kluth on 2010-03-10
While a 64-bit OS would be needed for 4 Gb of RAM, the 32-bit version should be able to use at least 3 Gb if not more (as in 3.3 or 3.5 Gb). Correct me if I'm wrong. :confused:

---

### Post by egalvan on 2010-03-10
> **von kluth said:**
> **While a 64-bit OS would be needed for 4 Gb of RAM, **the 32-bit version should be able to use at least 3 Gb if not more (as in 3.3 or 3.5 Gb). Correct me if I'm wrong. :confused:

Yes, you are wrong... :D

First,
Linux is Not Windows... ;)

There are no artificial RAM barriers.
If the hardware sees 4GB, then the software sees 4GB...
**Even 32bit Linux can see 4GB of RAM,** if the hardware allows it.
( I have a Dell with 4GB of RAM, and 32Bit Hardy sees almost all of it (3.8, if I remember a`right). I have another Dell with 8GB RAM and full PAE support, and 32bit Hardy sees all 8GB. Yes it does )

Of course, the problem is usually the hardware that uses some of the RAM for other things, and limits the amount that the software can see.
 There is video RAM, BIOS holes, etc, that lowers the total RAM that the hardware leaves as unused...
Also, some hardware cannot see more than 4GB of RAM, and has no PAE support... in which case the software cannot see more than 4GB.

Second,
Linux is Not Windows...;)

Linux has much better algorithms to make efficiant use of RAM.
While it *may* be possible, in some *specific* combination of hardware and software, to tweak the RAM usuage, 
the default settings will be the best.
Linux is simply better equiped to *efficiantly* use RAM.

---

### Post by no2498 on 2010-03-10
ok you can do this 2 ways
open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to..x window system (no xv)
you did save what it was set to so you can set it back if this does not help

up top is click, system, preferences , multimedia systems selector
same window pops up as gstreamer-properties do as i said

am all most positive you need to restart the computer before you see it work

try the effects lets see some feed back 

this all comes from the cheese help faq's

---

### Post by Slim Odds on 2010-03-10
> **egalvan said:**
> Yes, you are wrong... :D

First,
Linux is Not Windows... ;)

<snip>

You need to do your research before you start preaching.

32 bit OS's of all flavors have limitations that mean that they cannot use the entire 4GB for the OS itself. A significant portion of the RAM space below 4GB is dedicated to devices (like graphics cards, I/O devices, etc.). Since a 32 bit OS can only address 4GB of total address space, and some is used by devices.... you don't get 4GB for your OS (Windows, Linux, whatever).

[http://en.wikipedia.org/wiki/PCI_hole](http://en.wikipedia.org/wiki/PCI_hole)

So get down off your high horse.

---

