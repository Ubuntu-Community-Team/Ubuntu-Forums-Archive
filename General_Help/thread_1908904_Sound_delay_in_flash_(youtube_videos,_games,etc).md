---
title: "Sound delay in flash? (youtube videos, games,etc)"
date: 2012-01-14
forum: General Help
---

### Post by hatashii on 2012-01-14
I've recently installed ubuntu 11.1 on my pc, dual booted with windows 7

I've installed flash player and anything that uses flash will have a 2-3 second sound delay. For example I'm on youtube, I play a video; whilst the video plays immediately the sound starts about 2 seconds later, if I were to adjust the volume it would adjust 2 seconds after I've changed it, if I pause the video the video pauses immediately but the sound takes an extra 2 seconds to stop. This goes for flash games to.

Anything that doesn't use flash, e.g. music on my computer etc... syncs perfectly fine.

I have literally gone trough every single post I could find on google and they have all the same issue's as me but no solution to it :( 

Does any one have any idea how to fix this? 

(my main browser is google chrome but the bug is in all web browsers / anything that uses flash)

pc specs:

i7-860 3.4Ghz with intel turbo boost + hyper threading
8GB XMS 3 DDR3 3333Mhz ram
1TB Samsung HDD 7200rpm 32MB cache

(the sound in flash was fine in ubuntu 11.04)
(p.s [this]("http://ubuntuforums.org/showpost.php?p=10849047&postcount=27") post don't help me)


Any help is appreciated,
- Hatashi

---

### Post by dino99 on 2012-01-14
few answers:
- bad video quality posted on youtube (you cant do anything)
- your logs show some errors/warnings like missing codecs: check both .xsession-errors into /home & /var/log/ files
- check that your video driver is activated (sudo jockey-gtk)
- look at sound system settings
- into synaptic: purge flashplayer, then install flashplugin-installer

---

### Post by pqwoerituytrueiwoq on 2012-01-14
use flash-aid to make sure you have the correct version of flash
[https://addons.mozilla.org/firefox/addon/flash-aid/](https://addons.mozilla.org/firefox/addon/flash-aid/)

---

### Post by hatashii on 2012-01-16
> **pqwoerituytrueiwoq said:**
> use flash-aid to make sure you have the correct version of flash
[https://addons.mozilla.org/firefox/addon/flash-aid/](https://addons.mozilla.org/firefox/addon/flash-aid/)

I tried it out, it removed all flash plugins and re-installed a stable flash on my pc but I still have the same problem :(

---

### Post by hatashii on 2012-01-16
> **dino99 said:**
> few answers:
- bad video quality posted on youtube (you cant do anything)
- your logs show some errors/warnings like missing codecs: check both .xsession-errors into /home & /var/log/ files
- check that your video driver is activated (sudo jockey-gtk)
- look at sound system settings
- into synaptic: purge flashplayer, then install flashplugin-installer

Sound works fine within ubuntu, It's just a flash problem, I've looked at all the points above already, what do you mean by purge flashplayer?

---

