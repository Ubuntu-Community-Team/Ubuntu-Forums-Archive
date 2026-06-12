---
title: "Firefox suddenly stopped showing any graphics"
date: 2012-04-27
forum: General Help
---

### Post by madmax75 on 2012-04-27
I just experienced a weird problem with Firefox.

I am on Ubuntu 10.10. I made a Ubuntu One account and it offered to download an add-on for Firefox so I can sync my Bookmarks with it. 

After making the account and checking it out in Firefox, I closed the browser normally and then launched it again immediately.

Now, there are no graphics anywhere, all I get are just the plain text pages (black text, blue links, white background on all pages). 

The forward and back buttons do not work anymore, but I can open links in new tabs.

Google image search does not show any found images, just grey rectangles instead of thumbnails.

EDIT:

Also, all the preinstalled search engines from that Firefox search box in upper right have vanished.

Chromium on the other hand seems to work normally.

I suspect this has something to do with the Ubuntu One add-on, but I can't even access the add-on tab in Firefox to check things out. Or maybe it's the Java? No idea.

All I know that Firefox stopped showing any kind of graphics immediately after setting up an Ubuntu One account (with bookmark syncing and that mysterious add-on).

No idea how to fix this. I could delete Firefox and reinstall it, but I'm not sure if I can get it from any of the repositories anymore, given that I'm on a legacy system. I guess the 10.10 package archives and PPA's still work with legacy 10.10?

Ubuntu Linux 10.10
Firefox 11.0

---

### Post by madmax75 on 2012-04-27
Just tried reinstalling Firefox 11.0, but it doesn't help. Still the same problem, no graphical content or images displayed at all, just basic text.

EDIT:

Also, the Firefox address bar is not responding. The only things that work are the plain blue links that happen to be on a web page.

I have some add-ons installed. One of them is Adblock Plus, which according to other web pages can cause graphic display problems, but I can't check it out, since the Firefox add-on tab refuses to load up.

Tried to clean the cache with Bleachbit, didn't work, still no graphics.

I'm really at loss here :confused:

---

### Post by madmax75 on 2012-04-27
Could this be a Java problem? But I don't get how a malfunctioning Java could render the whole browser inoperable :confused:

---

### Post by sffvba[e0rt on 2012-04-27
*Thread moved to **General Help**.*


404

---

### Post by wbee on 2012-04-27
Hello,

I opened Firefox and it had eaten my bookmarks. I tried to recover from backup,but no bookmarks.

My graphics are OK,but the blue links are gone. That is,the only way I can navigate is putting "http://www.insertaddresshere.com" in the address box.

I uninstalled it, re installing it,and it was exactly the same.

Like Max,I'm using Google Chrome,which is working fine. That would seem to suggest the problem is isolated to Firefox.

I'm going to wait a month to upgrade to !2.04,so I am hoping Google Chrome will hold me to them.

When I get home,I'll post on the Mozilla sight,but this is a bright group at Ubuntu,so if you know the shell command to decontaminate the registry,or what ever the problem is,please share it.

-------

wbee

---

### Post by madmax75 on 2012-04-27
I suspect that this problem comes from Adobe's abandonment of the Linux port of Flash some time ago, and the fact that Firefox apparently just updated to 12.0. Or something.

Chrome/Chromium is the only browser that support Flash at this time in Linux.

But I have hard time understanding how this could render even the back and forward buttons and all the search bars in my Firefox 11.0 completely broken? How is that even possible :confused: :confused: 

Or are even these basic functions made with Adobe Flash in Firefox?

I just don't get it.

---

### Post by jeebustrain on 2012-04-27
I had this exact same problem on my desktop machine running 10.10... The address bar and all of the buttons became inoperable all of the sudden. It's been at least a month and I still haven't been able to find a root cause. I've even gone in and whacked my .mozilla directory and started from scratch and it still doesn't work. I've been running the mozilla ppa to get the current ones. I've been thinking of moving back to the stock 10.10 browser, but will probably just rebuild the machine using 12.04 anyway, now that it seems that the multi-monitor issues with Unity appear to be fixed. 

Ironically, I switched over to Chromium right after this started and anything flash related (especially youtube) completely borks the browser and causes it to hang. No cure for that either.

---

### Post by madmax75 on 2012-04-27
I managed to get Firefox back up and running with instructions from this thread:

[http://ubuntuforums.org/showthread.php?t=1949230](http://ubuntuforums.org/showthread.php?t=1949230)

But I can't still access the add-on tab. It just keeps loading and loading. Also, the download buttons in the Firefox add-on download site (I can't remember it's "real" name) don't work.

*sigh*

The situation is better, but still not optimal. If I could just get the freaking add-ons to work :(

EDIT:

Yeah, NOW it's the good-awful Flash. Can't remember how I get that to work.

EDIT:

Okay, got Flash working (for now), by going to the Adobe Flash site, then something happened, and it seems to work.

Now the problem is Java. That has to be reinstalled as well. The problem is that I have old repositories, so no way getting the debs for it. Do I really have to do it manually (did it once, it was awful).

I can't even save web pages in Firefox...? Is this because of Java? I don't know.

Sigh. Maybe Firefox just isn't worth it anymore :-/

Maybe the IcedTea stuff will work?

Or maybe it is just time to upgrade to 12.04 and use Chrome for Flash stuff.

I just hate this Flash and Java stuff.

---

### Post by madmax75 on 2012-04-27
> Purge your Firefox installation. And reinstall.

I already did that, and it is still broken. It actually got worse again, since I am not able to reinstall Sun Java - I can't get the packages anywhere anymore (I'm on legacy 10.10).

I think I will just install 12.04. I downloaded the Ubuntu and Xubuntu versions.

Maybe I will also ditch Firefox for Chromium/Chrome for good. It was fun while it lasted :-/

---

### Post by wbee on 2012-04-28
Hello,

Thank you,Paddy Landau.

The shell commands in this post:[http://ubuntuforums.org/showthread.php?t=1949230](http://ubuntuforums.org/showthread.php?t=1949230)

solved the problem.:-)

---

### Post by madmax75 on 2012-05-01
> **wbee said:**
> Hello,

Thank you,Paddy Landau.

The shell commands in this post:[http://ubuntuforums.org/showthread.php?t=1949230](http://ubuntuforums.org/showthread.php?t=1949230)

solved the problem.:-)

I tried these exact commands, it did work for a while, then it went broken again.

But I mark this thread as "solved", because I'm probably installing the new Xubuntu 12.04 fairly soon.

---

