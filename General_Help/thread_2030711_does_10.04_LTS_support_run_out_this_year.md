---
title: "does 10.04 LTS support run out this year?"
date: 2012-07-21
forum: General Help
---

### Post by eival on 2012-07-21
and someone explain the pros/cons of the 32/64 bit versions of 12.04

i do alot of multimedia flash streaming (gametrailers, youtube, mlb.tv, nba league ***, nfl rewind/ect..)

along with basic text/forums/sites, thats literally everything. no extensive video or photoshopping or other stuff and i dont run games on it.

im not big on needing shiny things, i turn off all the desktop aesthetics and effects, whether it can actually handle it or not, i just dont care about that crap.

so would 64bit enhance multimedia streaming quality?

or would i just be wasting my hardware resources to run the 64bit OS rather than just run the 32bit version

and most importantly, how is Adobe's support of the 64 bit plugin for Ubuntu and how does it perform?


i dont wanna have to be a Guinea pig for a bunch of plugins and apps in 64bit if every company still isnt supporting like they should yet

---

### Post by kansasnoob on 2012-07-21
First of all 10.04 LTS is supported until April 2013 so you have time to decide what you want to do :)

In case you don't know Ubuntu 12.04 LTS is supported for five whole years this time, previously only the server editions were supported for 5 years while the desktop editions were supported for only 3 years.

IMHO this makes 12.04 well worth any issues you might encounter but before I even get into the 32 bit vs 64 bit thing let's talk desktop environment. By default Ubuntu now uses the Unity desktop environment. Since you like video here's two that'll give you some idea what to look forward to:

[http://www.howtogeek.com/119219/an-introduction-overview-of-unity-in-ubuntu-12.04-for-beginners-video/](http://www.howtogeek.com/119219/an-introduction-overview-of-unity-in-ubuntu-12.04-for-beginners-video/)

[http://ubuntuforums.org/showthread.php?t=2026920](http://ubuntuforums.org/showthread.php?t=2026920)

But DO NOT freak out! If Unity is just not your cup of tea, and since you said this:

> im not big on needing shiny things, i turn off all the desktop aesthetics and effects, whether it can actually handle it or not, i just dont care about that crap.


I think you might find my thread here very helpful:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

While I actually like Unity on wide-screens up to about 19" there are still places where I want pure old fashioned simplicity :)

Now one more thing before we discuss 32 bit vs 64 bit. Regardless of what desktop environment you might prefer you need to check hardware compatibility so, even if you're planning to upgrade through the Update Manager, I strongly suggest downloading 12.04 and creating a live CD/USB.

After doing so the next step is to check the live media integrity. Ubuntu began hiding the boot options in Lucid so when the first screen appears with the two small logos at the bottom you have a whopping 3 seconds to press a key and display the language selector followed by the boot options. Be sure to choose "check disc for defects". It takes several minutes to complete but I can't think of anything more frustrating than finding out the installation media was faulty. Look here:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

While running the live media is always less responsive than a true installation/upgrade that should give you some idea of whether or not your hardware is going to cause you problems with the upgrade or re-installation.

Now about 32 bit vs 64 bit, you'll find that opinions and personal experience vary greatly, but first you asked:

> how is Adobe's support of the 64 bit plugin for Ubuntu and how does it perform?

It now seems fine, BUT ..................

I have two sets of 64 bit capable hardware:

> AMD Sempron Processor LE-1250 @ 2.2 GHz
nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)
nVidia MCP61 High Definition Audio (rev a2)
nVidia MCP61 Ethernet (rev a2)
2GB DDR2 RAM

*********************************************

Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

But you'll notice that each has only 2GB of RAM and I've personally found 32 bit to perform much better! 

I even used this app:

[http://ubuntuforums.org/showpost.php?p=11473552&postcount=208](http://ubuntuforums.org/showpost.php?p=11473552&postcount=208)

And I could visibly see that memory usage was much more conservative under 32 bit than it was under 64 bit.

So my personal recommendation is that if you have less than 4GB of RAM just stick with 32 bit (aka: i386).

---

### Post by Bucky Ball on 2012-07-21
April 2013, as mentioned.

If you don't need bells and whistles why not Xubuntu or Lubuntu 12.04 LTS. Unlike Ubuntu, Xubuntu 12.04 LTS is supported for three years and Lubuntu is not an LTS release and regular eighteen months, both from April 2012. This will give you a better understanding of the release cycle, etc:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Think of it this way: 12.04 = 2012, April (fourth month). LTS = Long Term Support, in this case five years. Easy. 10.04 was a three year support, so ... ;)

PS: Unity seems to be a bit of a love or hate thing among the community. I would advise to definitely try it out from the install disk before installing. Other option is to install then install the DE of choice. Good luck.

---

