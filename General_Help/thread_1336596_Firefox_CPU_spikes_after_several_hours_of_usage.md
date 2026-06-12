---
title: "Firefox CPU spikes after several hours of usage"
date: 2009-11-24
forum: General Help
---

### Post by another_sam on 2009-11-24
This is sort of a bug but hard to reproduce.

I am perceiving that on Ubuntu 9.10 Karmic Koala (in previous versions I wouldn't know to tell), Firefox feels sluggish after a while; couple of hours or so. And looking at system monitor I noticed CPU spikes every 10 seconds if I don't touch anything, and every 2-3 seconds if I start typing in a textbox like this one, or doing other simple things such as right-click somewhere, or clicking some menu item...

It is strange because, when I begin the session, Firefox goes fast indeed. But then I start browsing, working, opening tabs, using FireFTP (I will discuss this next), etc. and eventually Firefox becomes unresponsive 30% of the time or so; I have to wait several seconds for almost everything.

In particular, using FireFTP for web developement (upload, test, change, upload, ...) becomes consistently unbearable after a couple of hours because of the conjunction of this two effects:
1. Each transfer doesn't last for 1 to 2 seconds but for 5 to 10 seconds 
2. During all the time of the transfer, not only FireFTP but Firefox itself gets unresponsive and I can't use any tab for anything.

So, does anyone have detected similar behavior on his Firefox? What could be the cause? What could I try to locate it better? (closer process/memory monitoring, ... I don't know)

Thank you.

---

### Post by tripolitan on 2009-11-24
CPU/RAM/HD info please.

---

### Post by lovinglinux on 2009-11-24
From your description looks like the problem is with FireFTP. Some extensions can leak memory and make Firefox very slow and unresponsive. Disable FireFTP and test it for a couple of hours.

It could also be some javascript on a web site.

Also take a look at [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by TheOnlyMrK on 2009-11-24
I've had this problem with Firefox since the day I started using it years ago on Windows, no matter what OS, what add-ons, or what computer you have, Firefox will lag/freeze/crash if left open for too long or more then 10 to 15tabs are open. I've noticed that it's RAM use increases over time and if browsing the internet for a very long time without restarting Firefox it will freeze for a few seconds whenever I do anything and when I look at RAM usage for it it can be near and sometimes even over 1GiB. Basically Firefox is a great web browser, and this one flaw is nowhere near enough for me to stop using it, but it's not made to be open for long periods of time, which really needs to be fixed.

---

### Post by another_sam on 2009-11-28
Sorry just learned "Thread tools" > "Subscribe to this Thread" today.

CPU: Intel Core Duo T2400
RAM: 2GB at some blazing fast speed
HD: Fujitsu 320GB MHZ2320BH G2: System in ext4 partition, Firefox profile in ext3 partition

I'll test what happens without FireFTP. Based on what I can recall now from previous weeks, I would say that the progressive slowness happens anyway, but it does not exceed the pain threshold as when using FireFTP.

Quite relevant data here is that testing with a fresh Firefox profile on a fresh Firefox session on a fresh OS session, with Windows XP SP3 FireFTP transferences take 10% to 20% of CPU but with Ubuntu 9.10 take 60% to 80%.

I think this last point will be much more easy to test and discuss for all than the previous one.

---

### Post by tripolitan on 2009-11-28
I didn't know that FireFTP is for mozilla. Mozilla, by itself, is a cpu hog, I would personally stay away from FireFtp and any un-necessary add-ons. On my system, Firefox starts to crawl when I open more than 4 tabs, any more than that could freeze it...

A better alternative, in my opinion, is gFTP, a native GTK ftp tool.

p.s. what do you mean by "Profile in ext3 partition"? do you mean /home partition?

---

### Post by another_sam on 2009-11-29
> **tripolitan said:**
> A better alternative, in my opinion, is gFTP, a native GTK ftp tool.

p.s. what do you mean by "Profile in ext3 partition"? do you mean /home partition?

I prefer to have the FTP client embedded on Firefox and since I use FireFTP successfully on Windows I expected to do it on Ubuntu as well. I hope the performance issues will be eventually fixed.

By "Profile" I meant "Firefox profile". Sorry, it was not that clear. Now I edited. (well, actually my whole /home is in that ext3 partition but my reference was particularly about the location of the Firefox profile folder).

For what you and TheOnlyMrK said, both you have major performance issues with Firefox itself. I'd wish to spot and fix them but both things are beyond the scope of my skills. Still there is one thing I can suggest if you find it compatible with your needs: go to options > privacy and set Firefox to clear all history and online website data when closes.

---

### Post by tripolitan on 2009-11-30
I found that what works on one system may not necessarily work as well on another; LimeWire, Firefox, Picasa and OpenOffice, to name a few. Firefox, in particular, has some quirks on Windows that don't exist in Linux but the performance issue has been going on for quite sometime, despite all the problems, it has improved quite a bit in version 3.5. Firefox is a cpu hog and that is that...until "they" fix it!

FYI, my cpu right now is running between 50% and 70% and all I have on is Firefox with 3 tabs open + XMarks as an add-on!

---

### Post by another_sam on 2009-12-05
Just web developing with FileZilla instead of FireFTP during the last two hours. Firefox keeps fast as fresh.

Interaction with FileZilla is quite agile since I browse through it, then I right-click > Edit the files I need to, work on the files, and when I turn the focus back to FileZilla, I just have to click OK on a prompt for each modified file.

Moreover, FileZilla GUI runs 5 to 10 times faster than FireFTP GUI does, even when FireFTP is fresh.

Really FileZilla has improved since the last time I used it. I'll be using it for now.

---

