---
title: "The Weather Channel Videos"
date: 2010-05-21
forum: General Help
---

### Post by vwbug on 2010-05-21
I'm having problems viewing videos on the weather channel.  I have Ubuntu 9.10 and Firefox 3.5.9. Starts to load and never starts.  Only happens on the weather channel.  Thought it might be a pop up blocker or ad blocker, but I disabled them and had the same result. Tried it using Opera and it worked fine! Anyone else had this problem?

---

### Post by lovinglinux on 2010-05-23
See the fifth item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html).

Also Install [FLASH-AID](http://ubuntuforums.org/showthread.php?t=1491268) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by vwbug on 2010-05-28
Well for some reason I was able to watch a video on the Weather Channel today, but just one!!! Now I can't even see the one I just watched. Just something about the Weather Channel.

---

### Post by vwbug on 2010-05-29
Whatever it is seems to be related to "read admin.brightcove.com"
It stops loading at that point.  Just wondering if anyone else had the same problem.

---

### Post by lovinglinux on 2010-05-29
> **vwbug said:**
> Whatever it is seems to be related to "read admin.brightcove.com"
It stops loading at that point.  Just wondering if anyone else had the same problem.

Install [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722) and block third-party scripts.

---

### Post by vwbug on 2010-06-21
flash-aid and no-script didn't help. Threw in an old hard drive I had and tried it with a "fresh install" with the same results.  Works fine with Opera and Google Chrome. The Weather Channel changed something, but no ideas what, just that Firefox doesn't like it.

---

### Post by XSAlliN on 2010-06-21
> **vwbug said:**
> I'm having problems viewing videos on the weather channel.  I have Ubuntu 9.10 and Firefox 3.5.9. Starts to load and never starts.  Only happens on the weather channel.  Thought it might be a pop up blocker or ad blocker, but I disabled them and had the same result. Tried it using Opera and it worked fine! Anyone else had this problem?

Firefox + Flash under Linux = not a very good combination. 

On the other hand Chromium works just fine, yet I wouldn't use it for everyday browsing (security related - which is he's weakest point) - I have it installed just for flash streaming or rare situations. Chrome being the spyware browser from Google that is, yet using it for YouTube can't hurt, since it's also part of Google. 


> **lovinglinux said:**
> See the fifth item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html).

Also Install [FLASH-AID](http://ubuntuforums.org/showthread.php?t=1491268) extension for Firefox. **It will remove conflicting plugins** and install the proper flash version according to your browser architecture. 



What conflicting problems? All it those is detect your os architecture and install the required flash.

---

### Post by lovinglinux on 2010-06-21
> **XSAlliN said:**
> What conflicting problems? All it those is detect your os architecture and install the required flash.

If it just did that, then it wouldn't be useful. The extension removes swfdec, gnash, flash installed with Wine and manually installed flash versions before installing the required flash.

---

### Post by XSAlliN on 2010-06-22
Probably does that as weell, wouldn't know since mine where already removed. I tried it and all it did for me was installing flashplugin-nonfree which didn't fixed nothing... well, nothing beyond what I already fixed before... The thing is, with Chromium runs pretty decent but can't say the same about FF - Mozilla and Adobe are the only ones who can fix this... and maybe those that work on alternative projects and have their share of knowledge and experience with this subject, but none shown any significant progress so far. Yet on paper Lightspark looks pretty promising..

---

### Post by vwbug on 2010-06-22
I was able to watch the Weather Channel videos in Firefox under Wine! Its just a Linux-Firefox-Weather Channel problem.  Really weird because I can watch videos anywhere but the Weather Channel.

---

### Post by vwbug on 2010-07-29
Can watch weather channel videos now.  Didn't do anything, so it must have been something "they" changed.  Hope "they" leave it alone :)

---

