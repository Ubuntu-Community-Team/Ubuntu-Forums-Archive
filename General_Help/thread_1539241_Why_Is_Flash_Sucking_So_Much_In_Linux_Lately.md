---
title: "Why Is Flash Sucking So Much In Linux Lately?"
date: 2010-07-26
forum: General Help
---

### Post by Mark76 on 2010-07-26
Controls are unresponsive... Browsers crash... What *is* going on? ](*,) :mad:

---

### Post by Lucradia on 2010-07-26
Turn off Hardware acceleration, or downgrade to 10,0,42,34 using archived flash players: [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

If you use ATI, you may have problems where 10.1 causes slowdowns of the movie. (nVidia was Adobe's partner to make hardware accel. for flash.)

---

### Post by VH-BIL on 2010-07-26
Have you tried uninstalling it and reinstalling it from the adobe website?

---

### Post by Goolie on 2010-07-26
seconded, i'll try reverting, thx for the tip

---

### Post by Mark76 on 2010-07-26
It'll still suck even if I do that.

What I need is something that can stream the videos to a standalone player.

---

### Post by Helkaluin on 2010-07-26
> **Mark76 said:**
> What I need is something that can stream the videos to a standalone player.
May I ask which site?

---

### Post by RiceMonster on 2010-07-26
I've been having the same issues ever since they dropped the 64 bit version and I had to switch to the 32 bit wrapped version.

---

### Post by Mark76 on 2010-07-26
Youtube... Google... BBC... All of them.

I tried switching back to the 32 bit version with nsdiswrapper but that didn't change anything. I'm currently trying to figure out why I can't get clive to stream to mplayer.

clive [http://video.google.com/videoplay?docid=8681633512797721477#docid=8968064794581858968](http://video.google.com/videoplay?docid=8681633512797721477#docid=8968064794581858968) -s --stream-exec=mplayer

---

### Post by forrestcupp on 2010-07-26
Lately? :lol:

---

### Post by Mark76 on 2010-07-26
Hush you, and tell me the correct syntax for streaming flash videos to a-media-player :p

---

### Post by VH-BIL on 2010-07-26
> **Mark76 said:**
> Hush you, and tell me the correct syntax for streaming flash videos to a-media-player :p

LOL how can he hush and tell you something at the same time.

---

### Post by philinux on 2010-07-26
Moved to General Help.

---

### Post by FuturePilot on 2010-07-26
> **forrestcupp said:**
> Lately? :lol:

Took the words right out of my mouth.

---

### Post by dtfinch on 2010-07-26
Lately (since 3.6.4 or so) I've had an issue where right clicking Flash usually freezes it and the entire browser. Killing the npviewer.bin process unfreezes it and I can resume browsing.

They moved plugins out of process to protect Firefox from plugin crashes, but it still doesn't handle plugin freezes very well.

---

### Post by Bluesan on 2010-07-26
> **VH-BIL said:**
> Have you tried uninstalling it and reinstalling it from the adobe website?

Adding...

I finally just gave up on the default install, and deleted openjdk-6, and the flashplugin installer that got in through the extras package, and started over.

**First**, I installed Sun Java 6, and **then** reinstalled the flashplugin-installer. I did that about a week ago, and so far, I haven't had a crash on either Firefox or Chrome...

(Using 64 bit Lucid)

---

### Post by philinux on 2010-07-26
> **Mark76 said:**
> Hush you, and tell me the correct syntax for streaming flash videos to a-media-player :p

[http://ubuntuforums.org/showthread.php?t=1538471](http://ubuntuforums.org/showthread.php?t=1538471)

---

### Post by RJARRRPCGP on 2010-07-26
> **Mark76 said:**
> Controls are unresponsive... Browsers crash... What *is* going on? ](*,) :mad:

I'm not having that problem. Sorry. :(

---

### Post by v1ad on 2010-07-26
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

works 99% of the time.

---

### Post by rjbl on 2010-07-26
No problems with Flash on Ubuntu 10.04. Not now, nor ever.

rjbl

---

### Post by SunnyRabbiera on 2010-07-26
Removing openjdk helps, disabling hardware acceleration helps, running a 32bit kernel heps.

---

