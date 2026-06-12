---
title: "Microphone"
date: 2010-01-20
forum: General Help
---

### Post by HardcoreSSG on 2010-01-20
I'm attempting to record using Sound Recorder with my USB headset and i'm not being picked up. It's not the mic because I can use it while playing playstation. Can any one help?

---

### Post by paradox_qu on 2010-01-20
Maybe your mic volume is turned all the way down.  Try running alsa mixer and hit tab to go into the CAPTURE settings.  Make sure your mic is turned up and make sure that it is the selected input device

---

### Post by zollie on 2010-01-20
run alsamixer

[TAB] over until you see "Capture" or ALL highlighted. Then play with the various levels.  Leave whatever says "Boost" alone, it's the other ones that matter.

---

### Post by HardcoreSSG on 2010-01-20
everything is maxed out. still nothing.

---

### Post by paradox_qu on 2010-01-20
It might be muted.  It should have a green 00 under it not MM.

If it is MM hit "m" to unmute the channel.  Also try opening the gnome sound control and make sure it is unmuted and pointing to the mic and not line or something else.

---

### Post by HardcoreSSG on 2010-01-20
I attached a pic of the mixer, see what you can find out. Ima clueless. lol

---

### Post by lyall on 2010-01-20
> **HardcoreSSG said:**
> I'm attempting to record using Sound Recorder with my USB headset and i'm not being picked up. It's not the mic because I can use it while playing playstation. Can any one help?

check your connections again

there should be three ports 
one for head set
one for mic
one for line in

good luck and have fun learning

---

### Post by fragos on 2010-01-21
Configuration of sound is different with Ubuntu 9.10. I got mike to work by right clicking the sound icon, selecting Preferences and then the input tab. There are a lot of options here that weren't available before and for my system the default didn't work. Try some different things with your mike pugged in and the input level meter will tell you if the microphone is working. Not that not all applications use the system settings for sound and must be individually configured, Skype for example.

---

