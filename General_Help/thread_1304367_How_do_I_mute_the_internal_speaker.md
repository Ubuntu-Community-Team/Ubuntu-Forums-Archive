---
title: "How do I mute the internal speaker?"
date: 2009-10-29
forum: General Help
---

### Post by XGhozt on 2009-10-29
I can't figure out how to mute or disable the internal speaker on my desktop ubuntu box. I have my external speakers plugged in via the mobo, and it's playing all my sounds/music, etc.. from the internal speaker AND the stereo/speakers.

I searched around, and none of the solutions I found worked. I looked in the "Sound Preferences" and there's only one output device listed, "Internal Audio Analog Stereo".

Any ideas? I remember having this problem before, and there as a command I could run to just disable it. Unfortunately, I can't find it.

---

### Post by philinux on 2009-10-29
gksudo gedit /etc/modprobe.d/blacklist

At the end of the file, add this line.

blacklist pcspkr

---

### Post by XGhozt on 2009-10-29
That's already there. That must have been what I did before. This started happening again after I upgraded to ubuntu 9.10. Now what?

---

### Post by Paul.Tap on 2009-10-29
I'm experiencing the same problem here on a Lenovo D10. In 9.04 I was able to switch off the PC speaker via the sound preferences allowing the music to play via the external speakers only, but in Karmic this seems to have gone.

I've tried to undo the default blacklistings to see whether that would make a difference for the preferences but allas, so everything is back to defaults now. Disabling sound in my BIOS disabled all internal sound devices so that's no option either. Last thing to look at is "disabling" is manually by unplugging the cable but I'm not sure whether the speaker is connected that way. I'll open the machine tomorrow.

---

### Post by XGhozt on 2009-10-30
Is the only option here to unplug the speaker? There has to be a way to disable this...

---

### Post by XGhozt on 2009-11-04
I plugged in headphones to my front headphone jack and then the internal speaker shut off, while my extrernal speakers continued working. Lol?

---

### Post by doris orange on 2010-03-08
same situation here... my internal speaker rocks me until i plug my external speakers into the front headphone jack, then it goes quiet.  no change when i plug into the jack in the back.  i've been searching for a while now and haven't found a solution that worked for me, looks like i'll be opening her up...

---

