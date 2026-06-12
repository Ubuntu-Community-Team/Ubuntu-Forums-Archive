---
title: "Web browser keeps crashing"
date: 2010-03-14
forum: General Help
---

### Post by perceptor1337 on 2010-03-14
Hi!

I have a problem with the web browser, currently firefox but i have tried numerous others with the same results.
It seems that no matter which ubuntu version I have the web browser eventually crashes, i.e. it just shuts down. Over time this happens all the more frequently until it is almost impossible to view any webpage. I have both reinstalled the version I used primarily and I have also chosen other versions of Ubuntu. My deduction skills lead me to some kind of hardware problem but on the other hand I do not experience this problem in windows.

Please help!

Best regards,

perceptor1337

---

### Post by efflandt on 2010-03-14
There are a lot of flash ads on a lot of web sites.  What flash version and plugin are you using?

If you have an older CPU (like my Athlon64 3200+ from 2004) it does not have the lahf_lm instruction that real 64-bit flash uses.  And that can cause Firefox to instantly vaporize.  Someone did come up with a flashplugin-lahf-fix, but Hulu changed something that made 64-bit flash no longer work from a browser.  So I am now using flashplugin-installer which uses 32-bit flash with nswrapper.

Otherwise try disabling desktop effects and see if that helps.

With flashplugin-installer and no desktop effects, I have no browser issues (Currently 64-bit Firefox 3.5.8).

---

### Post by perceptor1337 on 2010-03-14
Thank you for your response!

I am currently running flash by installing flashplayer-installer through synaptic package manager.
My CPU is definitely newer, intel core 2 duo 7400 2,8GHz if I recall correctly.

How do I turn off the desktop effects? (and what are those? I haven't seen any "effect" at all on my desktop)

---

### Post by subedistra7 on 2010-03-14
> **perceptor1337 said:**
> Thank you for your response!

I am currently running flash by installing flashplayer-installer through synaptic package manager.
My CPU is definitely newer, intel core 2 duo 7400 2,8GHz if I recall correctly.

How do I turn off the desktop effects? (and what are those? I haven't seen any "effect" at all on my desktop)

it may not work, but try removing the flash from synaptic and install [this](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29)

---

### Post by perceptor1337 on 2010-03-14
Thanks for the suggestion but it seems there is no plugin for a 64-bit system.
The one your link pointed to was for 32-bit systems, it wouldn't even let me install it.

---

### Post by subedistra7 on 2010-03-14
> **perceptor1337 said:**
> Thanks for the suggestion but it seems there is no plugin for a 64-bit system.
The one your link pointed to was for 32-bit systems, it wouldn't even let me install it.

oh you are using 64 bit?

then you may need to run a certain command

---

### Post by subedistra7 on 2010-03-14
try this terminal (applications -> accessories -> terminal)

copy + paste this into it (terminal) & press enter.

```
sudo aptitude purge flashplugin-nonfree flashplugin-installer && rm -f /usr/lib/mozilla/plugins/*flash* && rm -f ~/.mozilla/plugins/*flash* && rm -f /usr/lib/firefox/plugins/*flash* && rm -f /usr/lib/firefox-addons/plugins/*flash* && rm -rfd /usr/lib/nspluginwrapper
```

---

### Post by perceptor1337 on 2010-03-14
But I already have flash installed on my system. What is the difference between installing it from synaptic and through the terminal??

---

### Post by subedistra7 on 2010-03-14
> **perceptor1337 said:**
> But I already have flash installed on my system. What is the difference between installing it from synaptic and through the terminal??

that cleans the system a little. it doesnt install flash, it removes the installed version.

you need to install the 64 bit flash.

---

### Post by km0r3 on 2010-03-14
Have you tried de-activating Visual effects?

System > Preference > Appearance > Visual effects

---

### Post by perceptor1337 on 2010-03-17
Thank you everyone for your replies.
I have tried every method described above but firefox still crashes although i have discovered that it happens when I have aroun 8-10 tabs open at the same time.
Can this be a problem?

---

### Post by km0r3 on 2010-03-17
> **perceptor1337 said:**
> Thank you everyone for your replies.
I have tried every method described above but firefox still crashes although i have discovered that it happens when I have aroun 8-10 tabs open at the same time.
Can this be a problem?

Yes, this is a problem.

Please check that you're using the latest stable version of Firefox. Maybe you're using an old Ubuntu version or custom sources for Firefox.

If the problem persists, please consider reporting this behavior as a bug to the Mozilla [Bugtracker]("https://bugzilla.mozilla.org/").

---

### Post by perceptor1337 on 2010-03-18
My version of firefox is the same one which is included in the latest distribution of ubuntu and as far as I know I haven't updated it yet.

---

### Post by wojox on 2010-03-18
What happens if you download Chrome: [http://www.google.com/chrome/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-sk&utm_medium=ha](http://www.google.com/chrome/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-sk&utm_medium=ha)

What pages crash Firefox? Heavy Flash pages? How much memory and do you use swap?

---

### Post by perceptor1337 on 2010-03-18
Generally every page has the "capacity" to crash firefox. I have 4GB RAM memory and swap is on default settings. Since I do not experience this problem when running windows I dont think it is a problem of memory shortage.

---

### Post by gatordude on 2010-04-12
I am having the same issue. I recently put a new system together.
Athlon II 630 
4G of ram
Ubuntu 9.10 (32 bit version)

Everything was fine for about 2 weeks then the last few days it started to stall loading pages (FF and Chrome).
I run HTop to see if something is hogging the resources and all seems normal.

As far as I can tell I have all of the latest updates.

There does seem some weird things happening. If I start from Google.com I can navigate semi normal. If I try loading a page from memory (FF or Chrome) it hangs. Sometimes it freezes the whole system and I have to do a hard reboot. I removed all extensions and add-ons from both FF and Chrome.

Any suggestions?

---

### Post by gatordude on 2010-04-14
Hey,

If your problem is related to Flash don't read any further.
If the problem you have is the same as mine read these posts.
My browser (didn't matter which one) got hung all the time and I could do a few things (band aide or whatever) but when I changed the MTU setting in my router I have been stable for the last two days with seamless web browsing. I came from a cable BB area to a DSL only area and all of my Windows machines were not affected by this at all. 

[http://ubuntuforums.org/showthread.php?t=1446791&highlight=connection+hangs]("http://ubuntuforums.org/showthread.php?t=1446791&highlight=connection+hangs")

[http://ubuntuforums.org/showthread.php?t=1376506]("http://ubuntuforums.org/showthread.php?t=1376506")

I changed the MTU setting in my router from 1500 to 1492 and I have had no issues.

I just wanted to share the info. I hope this helps...

---

