---
title: "Audio Problems?"
date: 2011-08-25
forum: General Help
---

### Post by kpayton on 2011-08-25
For some reason my Audio has stopped working.  I can hear the sound upon logging in but any youtube videos I only see Video.  Volume is up but I don't get anything.  Can someone help me?  Where do I start?

---

### Post by kpayton on 2011-10-09
Anyone have an answer for this?  Before I reformat and start over :(

---

### Post by hollowsyndicate on 2011-10-09
do u use hdmi?

---

### Post by kpayton on 2011-10-09
Nope - Laptop has an HDMI port but I dont use it.

---

### Post by hollowsyndicate on 2011-10-09
wat ubuntu are u using?

---

### Post by kpayton on 2011-10-09
11.04

---

### Post by hollowsyndicate on 2011-10-09
open a youtube video, click volume tray icon, click sound preferences, go 2 applications and look if mute is ticked.

---

### Post by runny6play on 2011-10-09
> **kpayton said:**
> For some reason my Audio has stopped working.  I can hear the sound upon logging in but any youtube videos I only see Video.  Volume is up but I don't get anything.  Can someone help me?  Where do I start?

So the problem is just limited to YouTube am I correct?
try other flash videos and see if its all flash videos or you tube specificity.   
i have a feeling it might be your flash driver

---

### Post by kpayton on 2011-10-09
It was defaulted to mute but I turned it up and no dice.  I see video but no sound  I can't even play Sample sounds from Ubuntu.

---

### Post by hollowsyndicate on 2011-10-09
type this in terminal

alsamixer

wat number is pcm out of 100??

---

### Post by kpayton on 2011-10-09
It says cannot open Mixer No such file or directory?

---

### Post by hollowsyndicate on 2011-10-09
did u type alsamixer?

---

### Post by kpayton on 2011-10-09
Yes Droppd into terminal and typed in alsamixer

It says Cannot open mixer: No such file or directory

---

### Post by hollowsyndicate on 2011-10-09
> **kpayton said:**
> Yes Droppd into terminal and typed in alsamixer

It says Cannot open mixer: No such file or directory

lol wat?

type

sudo apt-get install alsa-utils

---

### Post by kpayton on 2011-10-09
0 Upgraded 0 Newly installed 0 to remove and 57 not upgraded

---

### Post by hollowsyndicate on 2011-10-09
> **kpayton said:**
> 0 Upgraded 0 Newly installed 0 to remove and 57 not upgraded

wtf? are u using the normal ubuntu 11.04?

---

### Post by kpayton on 2011-10-09
LMFAO!!!  Yup 64 Bit.  The Natty Warhal

---

### Post by hollowsyndicate on 2011-10-09
kk try this in terminal.

speaker-test

u hear anything?

---

### Post by kpayton on 2011-10-09
Nothing - and the volume is cranked.

---

### Post by hollowsyndicate on 2011-10-09
kk that is weird. when did it stop?

---

### Post by kpayton on 2011-10-09
I think it was when I couldn't get a Codec to work or something I was trying things and then it just up and stopped working :(

---

### Post by hollowsyndicate on 2011-10-09
umm that mite be bad lol. how did u try to fix the codec thing?

---

### Post by kpayton on 2011-10-09
LOL - Thats how I got into this situation.  I don't even know how I installed them just started clicking things and it never worked .LOL

---

### Post by hollowsyndicate on 2011-10-09
><

did it show u a window with a search to install codecs?

---

### Post by kpayton on 2011-10-09
Don't remember its been that long ago :(  Is there a way just to remove all codecs and restore Audio to normal operation?

---

### Post by hollowsyndicate on 2011-10-09
i dunno sry. i could but it mite make it worse lol. if u want 2 do a new ubuntu install ill help u install the codecs the way i do it, which always works 4 me.

---

### Post by kpayton on 2011-10-09
NBD, I appreciate the help.  I may just have to blow it away and start over..  I was just thinking there was a way to restore to an earlier version..

---

### Post by hollowsyndicate on 2011-10-09
10.04 is awesome :D

---

### Post by kpayton on 2011-10-09
When is 12 Coming out?

---

### Post by hollowsyndicate on 2011-10-09
april something.

---

### Post by kpayton on 2011-10-09
Way too far away ;-)

---

