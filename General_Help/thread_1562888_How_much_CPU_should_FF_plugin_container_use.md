---
title: "How much CPU should FF plugin container use?"
date: 2010-08-28
forum: General Help
---

### Post by oxf on 2010-08-28
How much of CPU should Firefox plugin continer be using?
and what about Firefox bin?
What are reasonable figures?

I've been monitoring them and seems to me at times they are running high, 40,50% even higher at times though then it drops back.

---

### Post by rnerwein on 2010-08-28
> **oxf said:**
> How much of CPU should Firefox plugin continer be using?
and what about Firefox bin?
What are reasonable figures?

I've been monitoring them and seems to me at times they are running high, 40,50% even higher at times though then it drops back.

hi
i guess it depends on what you are running with your firefox. on ubuntu - what's i'am using now it's only
( or lower ) 1 %. but if you are looking video or something else stuff it will rayse up to the max.
what i want to tell you is - it depends on what you are doing. 
ciao

---

### Post by oxf on 2010-08-28
> **rnerwein said:**
> hi
i guess it depends on what you are running with your firefox. on ubuntu - what's i'am using now it's only
( or lower ) 1 %. but if you are looking video or something else stuff it will rayse up to the max.
what i want to tell you is - it depends on what you are doing. 
ciao

Thanks,

Well my concern is that I'm not doing much when it shoots up. eg I'm just browsing a webpage and it goes up quite high. I suppose flash content on the page could be setting it off though. 

Like you right now its low but I just opened another tabpage and it suddenly went up to 80% and then backed down to 40% FF bin also shoots up.

---

### Post by WorMzy on 2010-08-28
It's almost certainly caused by flash content.

Are you using the 64-bit version of Ubuntu? Flash on 64-bit Linux has always been a bit of a headache I'm afraid. Try using [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/"), I've seen other people recommending it to people with Flash issues, although I've never used it myself. Might be worth a try.

---

### Post by lovinglinux on 2010-08-28
> **oxf said:**
> How much of CPU should Firefox plugin continer be using?
and what about Firefox bin?
What are reasonable figures?

I've been monitoring them and seems to me at times they are running high, 40,50% even higher at times though then it drops back.

It is "normal". The CPU spikes are caused by flash content and I get the same values here. 

The plugin container is responsible for out of process plugin technology, that allows the browser to stay alive if the plugin crashes. This feature was introduced in Firefox 3.6.4 and currently supports Flash, Silverlight and Quicktime plugins. So if it is using too much CPU, then it is certainly because of flash.

I would advise to install [Flashblock](https://addons.mozilla.org/en-US/firefox/addon/433/) or [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/") to block flash content you don't need to be loaded automatically. [Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/") might help as well.

> **oxf said:**
> Thanks,

Well my concern is that I'm not doing much when it shoots up. eg I'm just browsing a webpage and it goes up quite high. I suppose flash content on the page could be setting it off though. 

Like you right now its low but I just opened another tabpage and it suddenly went up to 80% and then backed down to 40% FF bin also shoots up.

Depending on what you are doing Firefox CPU usage will spike above 50% and can even reach 100%, but it should stay very low if you are not viewing a page with Flash and heavy javascript or performing heavy heavy database operations, like synching bookmarks.

Nevertheless, it shouldn't spike to 80% all the time. If that happens with every page, then you might have an extension that triggers some heavy function whenever a new page is loaded. To verify if this is the problem, close Firefox and start it in safe mode:

```
firefox -safe-mode
```

This will disable all extensions temporarily, so you can determine if the source of the CPU usage is one of them. 

One thing that certainly helps, specially when using the address bar or managing bookmarks, it to [optimize the databases]("http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html").

> **WorMzy said:**
> Try using [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/"), I've seen other people recommending it to people with Flash issues, although I've never used it myself. Might be worth a try.

As the developer of that extension, I must clarify that what it does is to remove conflicting plugins from several places and install the proper version of the Adobe version from the repositories. Although it has been reported by some users that FLASH-AID solved some performance related issues, it is not intended to fix those issues specifically. Nevertheless, these issues might be associated with other plugins that FLASH-AID removes (gnash for example).

Anyway, starting with the installation of FLASH-AID won't hurt and will make sure you have the most compatible flash version.

Also see [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by oxf on 2010-08-28
> **lovinglinux said:**
> It is "normal". The CPU spikes are caused by flash content and I get the same values here. 

The plugin container is responsible for out of process plugin technology, that allows the browser to stay alive if the plugin crashes. This feature was introduced in Firefox 3.6.4 and currently supports Flash, Silverlight and Quicktime plugins. So if it is using too much CPU, then it is certainly because of flash.

I would advise to install [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/") or [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/") to block flash content you don't need to be loaded automatically. [Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/") might help as well.



Depending on what you are doing Firefox CPU usage will spike above 50% and can even reach 100%, but it should stay very low if you are not viewing a page with Flash and heavy javascript or performing heavy heavy database operations, like synching bookmarks.

Nevertheless, it shouldn't spike to 80% all the time. If that happens with every page, then you might have an extension that triggers some heavy function whenever a new page is loaded. To verify if this is the problem, close Firefox and start it in safe mode:

```
firefox -safe-mode
```This will disable all extensions temporarily, so you can determine if the source of the CPU usage is one of them. 

One thing that certainly helps, specially when using the address bar or managing bookmarks, it to [optimize the databases]("http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html").



As the developer of that extension, I must clarify that what it does is to remove conflicting plugins from several places and install the proper version of the Adobe version from the repositories. Although it has been reported by some users that FLASH-AID solved some performance related issues, it is not intended to fix those issues specifically. Nevertheless, these issues might be associated with other plugins that FLASH-AID removes (gnash for example).

Anyway, starting with the installation of FLASH-AID won't hurt and will make sure you have the most compatible flash version.

Also see [Flash Optimization]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html")

OK thanks (all) Thats useful info. I wont say it's spiking to 80% ALL the time, however, I do feel that both plugin container and bin are often running higher than they should. In fact from time to time they hog the cpu and screen greys out and I loose control functions

---

