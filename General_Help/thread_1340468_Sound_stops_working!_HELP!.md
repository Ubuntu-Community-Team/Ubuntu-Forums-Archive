---
title: "Sound stops working! HELP!"
date: 2009-11-28
forum: General Help
---

### Post by Mike_IronFist on 2009-11-28
My sound just randomly quits on me when watching a Youtube video for any given length of time, listening to a song or podcast, or anything else sound-related that doesn't involve the usage of JACK. The "sound crash" seems to be on a per-process business, as other apps can still make sounds when one of my open programs suddenly goes silent.

For example, I'll be listening to a podcast on Banshee, when the sound process apparently crashes, because the sound stops, but Banshee recognises this and stops playing the podcast.

This is super-annoying with Youtube videos, because I'll be watching one, and then it will suddenly go mute, and I'll have to reopen Firefox to fix it!

I'm running Karmic 64-bit. Can anyone help me?

---

### Post by Mike_IronFist on 2009-11-28
Okay, this is getting SERIOUSLY annoying! This is the sixth time that I've posted this problem and I haven't gotten a single response apart from my own bumps! Doesn't ANYONE have some kind of suggestion?

---

### Post by growthmetal on 2009-11-28
Try going to System > Preferences > Sound and changing the value in the sound playback dropdowns and the default mixer device dropdown.  (Note: I'm using 9.04 so maybe things look different to you.)

---

### Post by Mike_IronFist on 2009-11-29
> **growthmetal said:**
> Try going to System > Preferences > Sound and changing the value in the sound playback dropdowns and the default mixer device dropdown.  (Note: I'm using 9.04 so maybe things look different to you.)

No offence, but changing the volume of seperate sound components (which is all that is) is not going to fix my audio crashing.

---

### Post by Mike_IronFist on 2009-11-29
> **Mike_IronFist said:**
> No offence, but changing the volume of seperate sound components (which is all that is) is not going to fix my audio crashing.

Now excuse me for assuming, but I tried doing that, and for the first time, Ubuntu didn't boot up muted! I don't know if it solved any of the issues with the sound crashing though...

---

### Post by ikacer on 2009-11-29
> **Mike_IronFist said:**
> My sound just randomly quits on me when watching a Youtube video for any given length of time, listening to a song or podcast, or anything else sound-related that doesn't involve the usage of JACK. The "sound crash" seems to be on a per-process business, as other apps can still make sounds when one of my open programs suddenly goes silent.

For example, I'll be listening to a podcast on Banshee, when the sound process apparently crashes, because the sound stops, but Banshee recognises this and stops playing the podcast.

This is super-annoying with Youtube videos, because I'll be watching one, and then it will suddenly go mute, and I'll have to reopen Firefox to fix it!

I'm running Karmic 64-bit. Can anyone help me?

does this happen with any output driver? (ie oss, alsa, pulse)
try changing that and see if it makes a difference.

---

### Post by Mike_IronFist on 2009-11-29
> **ikacer said:**
> does this happen with any output driver? (ie oss, alsa, pulse)
try changing that and see if it makes a difference.

It seems to be Pulse Audio crashing.

---

### Post by Sin@Sin-Sacrifice on 2009-11-29
Then try what growthmetal said and change the output driver to see if others work better. Otherwise refer to [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by ikacer on 2009-11-29
> **Mike_IronFist said:**
> It seems to be Pulse Audio crashing.

then switch to alsa and everything should be peachy keen.

---

### Post by Mike_IronFist on 2009-11-29
> **ikacer said:**
> then switch to alsa and everything should be peachy keen.

How would I "switch to ALSA"? I thought PulseAudio was a sound server and ALSA is a driver? Explain?

---

### Post by Mike_IronFist on 2009-11-29
Bump

---

