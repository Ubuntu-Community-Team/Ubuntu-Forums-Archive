---
title: "Major Google Chrome Memory Leak"
date: 2012-06-11
forum: General Help
---

### Post by neu5eeCh on 2012-06-11
I've noticed, now ,  that if I leave Chrome open for any length of time, it will start eating up my memory, then force everything into the swap partition. Chrome has a history of this, I notice (having done some Google searches). My otherwise fast computer is slowed to a pitiable crawl.

My question:  Has anyone else noticed this? Any solutions (besides using Opera or FF -- which I'm already doing)? Is this related to Ubuntu somehow?

---

### Post by hansdown on 2012-06-11
Hi VTPoet.

Have you tried clearing the cavhe and cookies?

Just a suggestion.

[http://support.google.com/chrome/bin/answer.py?hl=en&answer=95582](http://support.google.com/chrome/bin/answer.py?hl=en&answer=95582)

---

### Post by neu5eeCh on 2012-06-11
> **hansdown said:**
> Hi VTPoet.

Have you tried clearing the cavhe and cookies?

Just a suggestion.

[http://support.google.com/chrome/bin/answer.py?hl=en&answer=95582](http://support.google.com/chrome/bin/answer.py?hl=en&answer=95582)

Thanks, I'll try that.

---

### Post by vasa1 on 2012-06-11
> **VTPoet said:**
> I've noticed, now ,  that if I leave Chrome open for any length of time, it will start eating up my memory, then force everything into the swap partition. Chrome has a history of this, I notice (having done some Google searches). My otherwise fast computer is slowed to a pitiable crawl.

My question:  Has anyone else noticed this? Any solutions (besides using Opera or FF -- which I'm already doing)? Is this related to Ubuntu somehow?
Is there a way to graph the increase in memory of Chrome?
Vaphell showed me how to chart information from the "sensors" command ([http://ubuntuforums.org/showthread.php?p=12008436#post12008436](http://ubuntuforums.org/showthread.php?p=12008436#post12008436)). Similarly, one could process information re. Chrome's memory usage over time from top?

I use Chrome on 12.04 primarily to access my GMail and GDrive. I haven't noticed a problem with my 4GB RAM laptop slowing down but, OTOH, I haven't specifically looked to see if memory usage is rising.

BTW, re. "I notice (having done some Google searches)." which of these is the most pertinent? You could provide that link. There's a lot of noise out there.

---

### Post by gn0m3boy on 2012-06-11
How many extensions do you have installed?
 
Also, if you click the 'tool' icon in the top right corner, select 'Settings' and then 'Show Advanced Settings' at the bottom of the page, the last setting should say something like, "Continue running background apps when Google Chrome is closed".  Do you have this enabled by chance? 

I realize your referring to when chrome is open, but with a little [[COLOR="Blue"]further study[/COLOR]]("http://support.google.com/chrome/bin/answer.py?hl=en&answer=1184722") I learned that there are a myriad of services that run in the background while chrome is open.  

You can view the 'back-ground' apps by selecting the settings icon and then selecting 'View Background Pages' and a box will appear and show you everything that is going on in the background of chrome...I found that for me there is **alot** going on there.


I would recommend leaving chrome open for awhile and when you start experiencing the 'memory-leak' that you check the 'View Background Pages' function and see what is chewing up your memory

---

### Post by vasa1 on 2012-06-12
> **VTPoet said:**
> I've noticed, now ,  that if I leave Chrome open for any length of time, it will start eating up my memory, then force everything into the swap partition. Chrome has a history of this, I notice (having done some Google searches). My otherwise fast computer is slowed to a pitiable crawl.

My question:  Has anyone else noticed this? Any solutions (besides using Opera or FF -- which I'm already doing)? Is this related to Ubuntu somehow?
How much time is needed for forcing everything into swap? I've been running Chrome for about 10 min and swap is 0 (as usual) and the PC remains as snappy as ever.
I have very few extensions: AdBlock Plus, Stylish, and High Contrast.
I have close Background apps ticked.
I'm not using safe browsing and the various suggestions that Google can offer (under Privacy, everything is unticked).
I haven't enabled "instant" search.
Synch is on.

I'll leave Chrome running for some more time and post back but I'd really like specific links to reports of Chrome hogging memory on Ubuntu.

---

### Post by gn0m3boy on 2012-06-12
While running Chromium press Shift+ESC to bring up the chromium task manager.  Click the 'Stats for Nerds' button and see which process in Chrome is using the most memory.  May be a bad extension? 

Also try launching Chrome from command line with option 
--purge-memory-button

Like this:

```
google-chrome --purge-memory-button
```

When you bring up the task manager you will see an alternate button 'purge-memory'

---

### Post by Bucky Ball on 2012-06-12
I use Iron (a derivative of Chrome) and don't seem to be having a problem. Perhaps you could try that and see if you experience the same issue.

[http://www.srware.net/en/software_srware_iron.php](http://www.srware.net/en/software_srware_iron.php)

---

### Post by neu5eeCh on 2012-06-12
I think I have wrongly fingered Chrome.

In fact, j'accuse Firefox, in the Butler's Pantry,  with the plugin-container. I've been using System Monitor to follow the killer and noticed at one point that my plugin-container was hoarding about 1 gig of memory. Some Google searches suggest that there may be add-on conflicts.

---

