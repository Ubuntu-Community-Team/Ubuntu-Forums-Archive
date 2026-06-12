---
title: "Trivial But...   What Happened to the Fireworks Screensaver?"
date: 2010-05-02
forum: General Help
---

### Post by casparov on 2010-05-02
Hi, Everyone... 

I really liked the Karmic fireworks screensaver, which appears MIA in Lucid.  

Does anyone know how I could acquire and install this feature?

Thanks so much for any help, 

C.

---

### Post by inameiname on 2010-05-04
If you are talking about a screensaver called 'skyrocket', which I think you are try this:

Open Synaptic Package Manager and search for skyrocket, and you'll find it's in a screensaver package called 'rss-glx'. And then just install it.

And easier way is just sudo apt-get install rss-glx. It's only 4.3 mb.

Found that through this: 

[http://ubuntuforums.org/showthread.php?t=1471916](http://ubuntuforums.org/showthread.php?t=1471916)

---

### Post by casparov on 2010-05-05
Iname...   

Thank-you so much for that idea--I will try that tonight.  

I apologize for not replying sooner. 

Thanks again,

C.

---

### Post by casparov on 2010-05-05
Iname...  

I applied the Terminal line (thank-you for that--what a help), and it worked!!!!

Fantastic!!!   Anyone who does not have Skyrocket on Lucid would be well advised to give this a try.  Show off Lucid to your friends!!!;)

All Regards,   C.

---

### Post by inameiname on 2010-05-06
No problem. Actually, looking more into screensavers, not only does 

sudo apt-get install rss-glx 

get you another 20, but I found a few threads on here that can give you 200 with

sudo apt-get install xscreensaver-data xscreensaver-data-extra xscreensaver-gl xscreensaver-gl-extra

I ended up just installing them. I know they just take up space, but it's only 25-30 MBs for all of

sudo apt-get install rss-glx xscreensaver-data xscreensaver-data-extra xscreensaver-gl xscreensaver-gl-extra


so why not? :P


Oh, and one of those new screensavers in the xscreensaver package is another fireworks one.

---

### Post by EazyEVM on 2011-08-03
[FONT="Verdana"]That screensaver package is awesome!  Thanks iname![/FONT]

---

### Post by pqwoerituytrueiwoq on 2011-08-03
now if we can figure out how to enable the sound in the skyrocket screensaver
```
/usr/lib/xscreensaver/skyrocket -m 50 -v 100
```
the volume settings does nothing :(
i know it uses openal for sound and it was removed as a dependency since sound is disabled by default

---

### Post by inameiname on 2011-08-03
> **EazyEVM said:**
> [FONT=Verdana]That screensaver package is awesome!  Thanks iname![/FONT]


Sure, No problem. I still use this package and love the variety.

---

### Post by inameiname on 2011-08-03
> **pqwoerituytrueiwoq said:**
> now if we can figure out how to enable the sound in the skyrocket screensaver
```
/usr/lib/xscreensaver/skyrocket -m 50 -v 100
```the volume settings does nothing :(
i know it uses openal for sound and it was removed as a dependency since sound is disabled by default


Hmmm, interesting idea. I wouldn't know how to go about it, but I'm sure some smart guy or girl on here might. :)

---

