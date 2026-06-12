---
title: "Ubuntu 8.10 - No Sound After Updates"
date: 2009-09-27
forum: General Help
---

### Post by umechanism on 2009-09-27
I'm running version 8.10 (32 Bit) on a Dell Desktop.  I recently realized that I no longer have sound.  I did have sound and have had sound for a long time but now I do not.

[LIST]
[*]YouTube = No Sound
[*]mp3s on hard drive = no sound
[*]No system sounds during boot up (Ubuntu Theme Song).
[/LIST]

I'm running dual boot so I switched over to Vista.  Sound works there but not in FireFox 3.5...just in I.E.  Strange.

Any ideas?

---

### Post by aysiu on 2009-09-27
Do you remember what packages got updated?

The fact that sound doesn't work in some parts of Vista (i.e., in two operating systems on the same computer) indicates it may be a hardware problem. Not sure, though.

---

### Post by umechanism on 2009-09-27
Unfortunately..I'm one of those users that just accepts all updates and hopes they work.  So no, I don't know which one caused the problem.  

I did notice that in the Pulse Audio Device chooser, under "Volume Control" then "Playback" it now lists "**ALSA plug-in [firefox]**: ALSA Playback" as the default playback device.  This is different than what it used to be.  I used to list my USB speakers there.  Wonder what happened?

---

### Post by umechanism on 2009-09-30
So I checked again.  Vista has all the sounds it is suppose to.  During start up I hear the MS music, systems sounds are working, email notifications are audible.  The only thing that does not have sound in Vista is Firefox.  Youtube and other streaming media is silent in Firefox but works just fine in I.E.

On the Ubuntu side (Dual Booting) - no sound at all.  No system sounds, no startup sounds, no e-mail notifications.  Firefox has no sounds either.

All of this worked just fine up until about two weeks ago (near as I can remember).  I believe some update changed my settings but I don't know which update it was.

Can I roll back the updates until I find the culprit?

Thanks!

---

### Post by umechanism on 2009-10-02
Anyone?

---

### Post by dazzlindonna on 2009-10-02
If you go to System / Preferences / Sound, does everything look ok in there? If so, then I'd add the volume applet to your panel if you don't already have it on there, and then click on it's Volume Control button.  Look for any of the sliders that are all the way down that should be up, etc.  Check each tab.  If none of that solves it, maybe reinstall Alsa or Pulseaudio?

---

### Post by umechanism on 2009-10-02
Man, this is bringing back some bad memories!  I spent about a month trying to get the sound to work about a year ago.  Has been working fine since then with no changes to the hardware or system except for the updates.  I think I may go insane!

Ok...so, yes..I did check the preference and everything is there.  However, under the Sound Preferences tab, I can't remember what should be selected for "Sound Playback", "Music and Movies", "Audio Conferencing", and "Default Mixer Tracks".  What does yours have?

Thanks!

---

### Post by umechanism on 2009-10-02
I used this thread to get the sound to work in the first place.
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Worked like a charm then.  What changed?

---

### Post by umechanism on 2009-10-09
I still have no sound.  Can someone suggest a fix?  
[LIST]
[*]I've tried using an Ubuntu boot disc...no sound there either.
[*]I've used a Linux Mint boot CD...no sound there.
[*]No system sounds during start up (beeps and such).
[*]No Ubuntu theme sound at login screen.
[*]I dual boot with Vista - Vista has sound.  No problems at all.
[*]I had sound in 8.10 until about three weeks ago.  Since then, no sound.
[*]Hardware is functional.  Problem is within Linux.
[/LIST]

Any help is appreciated.

---

### Post by umechanism on 2009-10-11
bump.

Anyone?

---

### Post by umechanism on 2009-10-11
Here is a screen capture of my sound settings.  I have music playing in the background but there is no audio.  I have even installed new speakers.  Still no audio.  

Audio works fine in Vista (Dual Booting).

Of special note, during startup, I hear the speakers make a "popping" noise as Ubuntu starts but no theme songs are heard after that.

---

### Post by umechanism on 2009-10-11
Got it to work!  The stinking "Master" was turned down!  I had to go to a terminal and type "alsamixer -Dhw" then turn the Master Control volume up.  It was muted!!!  How the crap does this happen?  I mean, the average Linux users, and especially newcomers from Windows, would have no idea that "alsamixer -Dhw" even exists.  I've complained about this before but just look at how many volume controls/settings/options and windows there are in this image.  Very confusing!

Ubuntu developers...can we simplify this??????

---

