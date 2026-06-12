---
title: "Firefox soaking up CPU"
date: 2009-12-08
forum: General Help
---

### Post by Belgatom on 2009-12-08
I've been on Ubuntu now for about two years on my main Desktop and four years on my laptop but I'm getting ready to really give up on Linux as a OS. And all because one big problem. 

Recently my Firefox is soaking up all the processor power I have whenever I hit certain sites. This is a recent thing. When first installing Jaunty, everything was fine now it's really getting out of hand. 90% of the time, I use the pc for surfin' the web. I have my usual haunts and whenever I hit these sites, my pc just starts stuttering, CPU usage goes to about 90% and I can't even open up my Home directory for lack of power. 

Sites I have a problem with:

Engadget - starts whining about unresponsive script and slows down to a crawl. 
IMDB - leave it open for more than 2 minutes and I have to kill the firefox process to get out of trouble
GoNintendo - some youtube movies are soaking up to 70 % of my processor. 

I am sure it has something to do with Flash, Java and Ajax, probably but I have no idea how to resolve it. 

More and more Webintigration and cloudcomputing is coming to the foreground and if Linux doesn't do anyting about making that kind of content easier accesible, there is no way non tech savy people will ever embrace it. 

I hope there are some peops out there that can tell me I'm wrong and hand me a simple solution. Personally I had been waiting on Chrome to come to the rescue but still nothing on the horizon. 

Why can't there be a browser that works like VLC, where all codecs and necessary plug-ins are within the program itself without the need for all this tweaking under need the engine hood. 

Sorry for the rant, but I have always been a big Ubuntu supporter but this is driving me round the bend. (The fact that I'm tired and just had a long day at work, didn't help either though).

---

### Post by mikewhatever on 2009-12-08
Logically, if only the selected sites give you problems, neither Linux nor Firefox has anything to do with it. That said, you could try deleting cache and cookies in Firefox or removing extensions that might be causing problems. A simple way to check if the current profile is the problem is to start Firefox under a different one with <firefox -P test>. Regardless of the cause, a glaringly obvious solution would be to  try a different browser that might work better for you. For example:
[http://www.google.com/chrome](http://www.google.com/chrome)
[http://www.opera.com/](http://www.opera.com/)

---

### Post by Belgatom on 2009-12-09
Will try this tonight. Currently working on MS at work.

---

### Post by khelben1979 on 2009-12-09
A few tips to speed up performance:

1. Make sure that you're using flash from Adobe and not some free software alternative.

2. Make sure you're using fast graphics drivers, not slow open source which easily get installed by an default install of Ubuntu.

3. If Firefox really is the problem, either go back to using Firefox 2 (it's possible despite your running the latest version of Ubuntu) or switch to another browser such as [Google Chrome]("http://en.wikipedia.org/wiki/Google_chrome") or [Opera]("http://en.wikipedia.org/wiki/Opera_%28software%29") to see if the problem gets fixed.

---

### Post by gradinaruvasile on 2009-12-09
> **Belgatom said:**
> I've been on Ubuntu now for about two years on my main Desktop and four years on my laptop but I'm getting ready to really give up on Linux as a OS. And all because one big problem. 

Recently my Firefox is soaking up all the processor power I have whenever I hit certain sites. This is a recent thing. When first installing Jaunty, everything was fine now it's really getting out of hand. 90% of the time, I use the pc for surfin' the web. I have my usual haunts and whenever I hit these sites, my pc just starts stuttering, CPU usage goes to about 90% and I can't even open up my Home directory for lack of power. 

Sites I have a problem with:

Engadget - starts whining about unresponsive script and slows down to a crawl. 
IMDB - leave it open for more than 2 minutes and I have to kill the firefox process to get out of trouble
GoNintendo - some youtube movies are soaking up to 70 % of my processor. 

I am sure it has something to do with Flash, Java and Ajax, probably but I have no idea how to resolve it. 

More and more Webintigration and cloudcomputing is coming to the foreground and if Linux doesn't do anyting about making that kind of content easier accesible, there is no way non tech savy people will ever embrace it. 

I hope there are some peops out there that can tell me I'm wrong and hand me a simple solution. Personally I had been waiting on Chrome to come to the rescue but still nothing on the horizon. 

Why can't there be a browser that works like VLC, where all codecs and necessary plug-ins are within the program itself without the need for all this tweaking under need the engine hood. 

Sorry for the rant, but I have always been a big Ubuntu supporter but this is driving me round the bend. (The fact that I'm tired and just had a long day at work, didn't help either though).

The problems are probably related to the flash player. Ads with flash content can be a performance hit especially on older hardware.

What firefox version, Ubuntu version, Flash version and what hardware (cpu/mem) do you have?
Do you use firefox 3.5, the latest stable version?

Also, Chromium (Chrome Linux version) is out already.
Download my attached script, launch it in a terminal. It will install the latest development build.

---

### Post by osmorphyus on 2009-12-09
id just like to inject here, that there is a known memory leak in FF.  ubuntu has nothing to do with it.  no matter what OS you run FF on, it will consume TONS of system RAM, SWAP & CPU resources.

i first looked into this when running XP.  its all over the internet.  try googling "firefox memory leak" and see what you find.

you might want to try another browser if your problem is that bad, or backup your much needed files and go with a quick re-installation of your system.  fresh systems seem to run better, i would use that however, as a last resort.  nobody likes restarting if they dont have to, afterall.

if you want a basic, super fast browser, look for something with no plugins, like dillo or something similar.  if im in a hurry just to ebay or jot out an email, ill use anything other than FF a lot of the time.

and do make sure you look into the FF memory leak issue.  it is very well known.

---

### Post by Ninja Tux on 2009-12-09
If you just need the text on the page, and not the flash animations that use all of your memory, you can disable flash animations using the tutorial[ here]("http://johnhaller.com/jh/useful_stuff/disable_flash.asp"). Flash uses a lot of memory. If you absolutely need those flash animations, try using [seamonkey]("https://help.ubuntu.com/community/SeaMonkey") or getting more RAM sticks.

---

### Post by paradigm2 on 2009-12-09
I have the same issue on occasion, however it also happened on windows.  I'm pretty sure it is related to the flash plugin.  You might consider the adblock plus extension to disable the flash ads.  That should help with many of the sites.

Also try disabling extensions one by one if you have many of them to see if one is causing problems.

---

