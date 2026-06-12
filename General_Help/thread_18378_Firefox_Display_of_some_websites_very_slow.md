---
title: "Firefox: Display of some websites very slow"
date: 2005-03-06
forum: General Help
---

### Post by Shambler on 2005-03-06
Hi,
on some websites, when I scroll the pages via the mousewheel, i noticed that the scrolling looks very slow. I tried the normal Mozilla suite, where I noticed no problems.
Any suggestions?

---

### Post by Jad on 2005-03-06
as I can understand its memory leaking?

---

### Post by bored2k on 2005-03-06
[QUOTE=Jad]as I can understand its memory leaking?[/QUOTE]
 try upgrading to the newest firefox thru the ubuntu backports . Also enable smooth scrool in preferences.

---

### Post by Shambler on 2005-03-06
Enabling Smooth Scrolling did not solve the problem. Is the Backport newer than Version 1.0, which is in Hoary, and if so, do you think that the problem lies in 1.0?

---

### Post by Geekboy on 2005-03-06
I have the same problem, I'm using Hoary.  

The funny thing is I have the same exact PC running WIndows 2000 with Firefox and that has no problems.

I'll try upgrading to the latest version of FIrefox.  Any other suggestions?

---

### Post by poofyhairguy on 2005-03-06
[QUOTE=Geekboy]I have the same problem, I'm using Hoary.  

The funny thing is I have the same exact PC running WIndows 2000 with Firefox and that has no problems.

I'll try upgrading to the latest version of FIrefox.  Any other suggestions?[/QUOTE]

Sure:

[http://extensionroom.mozdev.org/more-info/smoothwheel](http://extensionroom.mozdev.org/more-info/smoothwheel)

---

### Post by kassetra on 2005-03-06
[QUOTE=Shambler]Enabling Smooth Scrolling did not solve the problem. Is the Backport newer than Version 1.0, which is in Hoary, and if so, do you think that the problem lies in 1.0?[/QUOTE]

Ok, here are some issues with some microsoft mice in Firefox for Linux that I've tested out:

With some microsoft mice (usually wireless or optical or wireless/optical) the scrolling has issues where you'll scroll and then you'll have to wait for it to catch up. Also, using a scroll wheel instead of the scroll bars has a "bouncing" problem where it will go to the bottom of the page, and bounce the page up and down a few times.

The only thing I have been able to figure out is after trying the "smooth scroll plugin" that the microsoft mouse and the computer sometimes do not communicate well through Linux. The computer doesn't "hear" all of the mouse movements when they happen, and many times the mouse movement information gets lost in the process.

Upgrading firefox versions has not helped. So it's either the linux implementation of the smooth scroll plugin or the linux mouse drivers or both.

---

### Post by Geekboy on 2005-03-07
> 
 Sure:
 
 [http://extensionroom.mozdev.org/more-info/smoothwheel]("http://extensionroom.mozdev.org/more-info/smoothwheel")                                                                Already tried that one. No good, it didn't help.

 > 
With some microsoft mice (usually wireless or optical or wireless/optical) the scrolling has issues where you'll scroll and then you'll have to wait for it to catch up. That's exactly my problem. I doubt it has anything to do with it being Microsoft and Wireless. My mouse is a standard PS2 although it is Microsoft. Funny thing is it scrolls fine if I click and hold the scroll bar and move that up and down. Also, I've noticed the problem more on forums sites or sites with a lot of tables in them. Some regular sites scroll ok. 

And if I go to about:config, I can scroll very smoothly (is that a word? :lol:  ) up and down the page.  No problems at all.

---

### Post by gw90se on 2005-03-07
Hmmm... I have a Microsoft optical mouse and haven't noticed any problem. Acyually, I like it better wiith smooth scrolling and auto scrolling turned off. Now I have noticed that on the forums, I have to move the mouse off of a tabled area and over to the side to scroll. It seems to select the table, instead of the page and doesn't think it needs to scroll any.

---

