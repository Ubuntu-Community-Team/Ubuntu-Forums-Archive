---
title: "ZERO sound in Karmic"
date: 2009-10-29
forum: General Help
---

### Post by HardcoreSSG on 2009-10-29
Okay after recently upgrading from jaunty to karmic I now have NO SOUND.  WHAT HAPPENED?

---

### Post by terry_gardener on 2009-10-29
check alsamixer to make sure it is not just muted.

---

### Post by magneze on 2009-10-29
I had the same issue. Raised a bug a few days ago:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/462735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/462735)

---

### Post by HardcoreSSG on 2009-10-29
Okay that's another thing. My alsa mixer is...gone. I have a "mixer" but no longer is there an ALSA setting!

---

### Post by bribera on 2009-10-29
Can you post a screenshot of what's shown in your Mixer control panel?

Specifically, what do you see in the "Sound card" drop down, and what controls are visible to you below that drop down?

---

### Post by HardcoreSSG on 2009-10-29
Sure - hope you can help!

---

### Post by dj-toonz on 2009-10-29
Karmic has a new mixer called gnome-volume-control-Pulse (pulse Volume control) doesn't use the gstreamer-Alsa Mixer now, I had the same problem when I first installed Karmic, I just un-muted it & opened up sound preferences & moved the alert volume to full & rebooted & stayed like that

---

### Post by bribera on 2009-10-29
Huh. I've had situations where one of the sound card volume controls was muted/off. Even though it wasn't the primary one, sound was off. Once I turned it up, things worked...

So, you might want to try opening up the other playback card and checking volume controls there. You also might want to enable any controls that look like they're related to volume and make sure they're turned up somewhat.

---

### Post by HardcoreSSG on 2009-10-29
Well that didn't work:(

Any other suggestions.

Also, my graphics are really laggy after switching from jaunty to karmic, can anyone answer that too?

---

### Post by HardcoreSSG on 2009-10-29
> **bribera said:**
> Huh. I've had situations where one of the sound card volume controls was muted/off. Even though it wasn't the primary one, sound was off. Once I turned it up, things worked...

So, you might want to try opening up the other playback card and checking volume controls there. You also might want to enable any controls that look like they're related to volume and make sure they're turned up somewhat.

I tried that all of the sound card are maxed.
**nothing.**

---

### Post by BlackxxJapan on 2009-10-29
I'm having a similar problem.

Is there any other sound configuration things than the Prefs under System -> Pref -> Sound?

Running an HP mini 1000 here and I know the ALSA drivers didn't work on Jaunty but Karmic was supposed to fix that, but still not working =[

---

### Post by abestatmos on 2009-10-30
I got the same problem. So, I just followed this instructions 
[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)
 to upgrade ALSA. But before this I had cut the PULSE from Ubuntu.
Now, sound is working well but there is no volume icon ;(

Good luck

---

### Post by magneze on 2009-11-02
So I turn on my laptop today and sound is working fine. Erm. :confused: but :guitar:

---

### Post by BlackxxJapan on 2009-11-03
> **abestatmos said:**
> I got the same problem. So, I just followed this instructions 
[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)
 to upgrade ALSA. But before this I had cut the PULSE from Ubuntu.
Now, sound is working well but there is no volume icon ;(

Good luck
Upgraded to ALSA *.21 but still no dice on the sound.

I've checked in alsamixer that nothing is muted.  This is pretty frustrating =/

---

### Post by abestatmos on 2009-11-06
Did you have sound before upgrade?

---

