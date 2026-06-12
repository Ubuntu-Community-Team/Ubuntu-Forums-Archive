---
title: "system slows down"
date: 2011-02-20
forum: General Help
---

### Post by msidhard on 2011-02-20
hi friends my system slows much down so that i cannot use it at all when am watching any online videos or movies am using firefox 3.6.13 . and my spec is 
intel celeron  2.53 Ghz
512 Mb ram
ubuntu 10.04 on 40 GB seagate ide harddisk
Windows Xp on 80 GB western digital ide harddisk in dual boot.
And also my browser cannot open login page of yahoo site and some time it waits saying waiting for s7.addthis.com, or waiting for ad.yieldmanager.com like some thing when i am trying to open some sites

---

### Post by megabuffen on 2011-02-20
I would suggest installing adblock plus to prevent your browser from loading content from external sites such as yieldmanager and addthis. You can find it here: [http://adblockplus.org/en/installation](http://adblockplus.org/en/installation). It is a Firefox pluging, so you should be able to run it on any operating system. Adblock uses filters to select which content not to load. You might want to subscribe to a list as this will automatically block a lot of ads etc that might slow down your browsing experience. If this doesn't fix you issue, you just need to manually add yieldmanager.com, addthis.com and any other domain that is causing problems. Just make sure not to block any website that you want to visit.

As for your system slowing down, it might simply be because your hardware is to slow. I assume the videos are displayed using Adobe Flash, which isn't always the most performance efficient way to watch videos. Did this problem start recently or has it always been the same? Does it affect both Ubuntu and Windows?

---

### Post by msidhard on 2011-02-20
recently my system slowed down while watching online movies or videos

---

### Post by no2498 on 2011-02-20
install htop
type it in a terminal click enter it tells you how to install it
you can run it from the terminal or it comes up in applications system tools

look at the cpu and memory
find what is using the most thats a starting place

---

### Post by emarkay on 2011-02-21
512 Mb of RAM?   And doing video?  You are fortunate you get anything at all - that's a RAM intensive process and even 2Gb of RAM sometimes is not enough depending on your processor and the size of teh video file, and the codec used.

you should see how much swap file is being used while running the video - that will tell you if you are maxing out the RAM.  If you have an older 5400 RPM Hard disk, and you have no RAM or Swap, you are going to have much latency - or no video at all, too.

Also what type of graphics card and how much VRAM? Hardware is always the first place to look as it's a "Fixed" entity.

Yes, I also recommend NoScript and Flashblock to force your browser to display only the exact and specific data you need! and of course no other running apps below the browser.

Finally, are you sure your broadband source is delivering the full bandwidth - most onlue vodeo sites need about 2.5Mbps minimum, and that's on a newer PC.

---

