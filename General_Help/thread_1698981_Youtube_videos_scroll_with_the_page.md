---
title: "Youtube videos scroll with the page"
date: 2011-03-03
forum: General Help
---

### Post by Sethun on 2011-03-03
I have flash-aid for 64bit flash, I've tried re-installing everything, firefox, flash-aid, taking off add-ons. Nothing seems to be working, and it's been happening all the sudden with youtube, I try to scroll down to read comments but the video scrolls with the page and blocks it, then gets all weird and glitchy, and if I open a new browser it shows up in that browser as well.

---

### Post by Sethun on 2011-03-03
I've downloaded chrome, and it seems to be happening in all browsers.

---

### Post by Vaphell on 2011-03-03
100% confirmed (FF 3.6.14 and 4, Opera), started to happen to me yesterday. Ungodly annoying, also heavy flickering occurs.

At least in my case it appears to be youtube related, because vimeo, metacafe or dailymotion play stuff just fine. i think it may have something to do with the fact that Youtube has slightly updated page layout.

---

### Post by wave21 on 2011-03-08
so, is there a fix for this problem by now or do we have to wait for youtube to do something?

---

### Post by corncob on 2011-03-08
YouTube has been working for me but other people have been having problems:
[http://ubuntuforums.org/showthread.php?t=1693931](http://ubuntuforums.org/showthread.php?t=1693931)

---

### Post by wave21 on 2011-03-08
the problem isn't that the videos don't play. it's just extremely glitchy for me. the video scrolls with the page and even pops up in other tabs of the browser. It happens on FF, Opera and chromium. I've also reinstalled flash but to no avail.

---

### Post by seemore on 2011-03-08
Exactly the same problem. Flash-aid does nothing.

---

### Post by mclizardman on 2011-03-08
Sometimes that happens to me, sometimes it doesn't. A restart solves the problem. Annoying. Very annoying.

---

### Post by Werm on 2011-03-08
It's a known problem for 64 bit. Try this...

Open terminal: 

sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer

---

### Post by Werm on 2011-03-08
Oh run

sudo apt-get remove --purge flashplugin* nspluginwrapper

first

---

### Post by Vaphell on 2011-03-08
i have native 64bit flash - i disabled hardware acceleration (right click on flash site, settings) and it stopped doing that.

---

### Post by wave21 on 2011-03-08
I can't access the settings, it's grey.
Edit: ok, I could change the settings on a different website, it's working fine now, thanks!

---

### Post by kali_yuga on 2011-03-09
i also have this anoying problem with youtube, i tried many things including flash-aid, nothing works, if somebody knows some efective solution, please help................

---

### Post by Vaphell on 2011-03-09
have you tried disabling hardware acceleration of flash?

---

### Post by kali_yuga on 2011-03-09
im not sure what it means

---

### Post by Vaphell on 2011-03-09
you right click on some flash element and in context menu there are settings, global settings and flash info. Settings is the one you want, there is a checkbox that controls hardware acceleration. Not everywhere that option is active (youtube has it disabled for example), i used [http://derbauer.de/](http://derbauer.de/)

---

### Post by kali_yuga on 2011-03-09
sorrz, have much bigger problem now, doesnt want to boot at all, i answer from live iso environment..........

---

### Post by kali_yuga on 2011-03-09
im back. i got your point, i made it and it works. thanx a lot man!!

---

### Post by Eremis on 2011-03-13
same here

---

### Post by cosan on 2011-03-16
[http://www.youtube.com/watch?v=AdayWLsPeqo](http://www.youtube.com/watch?v=AdayWLsPeqo)


HUUULK SLAAAAMMMMM!!

---

