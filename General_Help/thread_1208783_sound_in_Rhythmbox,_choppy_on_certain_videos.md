---
title: "sound in Rhythmbox, choppy on certain videos"
date: 2009-07-09
forum: General Help
---

### Post by monkeyKata on 2009-07-09
I did a fresh install of jaunty recently so that I could try ext4, though now I am running into an audio quirk.

For a minute Rhythmbox wouldn't play anything.  Videos played fine.  After searching the issue I decided to install some packages that fixed the problem for someone else: gstreamer0.10-plugins-bad, gstreamer0.10-plugings-bad-multiverse, gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse.  I believe these packages are also a part of the ubuntu-restricted-extras.

So this fixed the problem with Rhythmbox and it plays music fine, yet certain videos (not every one) that played fine before now have a stuttery, choppiness to the sound.

I'd guess those gstreamer packages are the cause, but I must need them to get Rhythmbox running correctly.

Has anyone had this issue, or are there some tips to getting audio set up correctly in Jaunty that may help?

Lastly, when I open up an audio file individually in Totem I can not skip around the track, whereas I could before.

---

### Post by monkeyKata on 2009-07-10
bump

anyone have any ideas?  In addition, I have both pulseaudio and ALSA installed yet I've never really known if the two work together or if you don't need both and one actually works better than the other, if under the sound settings it's best to set everything to pulseaudio or to ALSA...

---

### Post by Malta paul on 2009-07-10
Have you tried testing your sound at System>Preferences>Sound ?
I also find that setting the volume settings using 'PulseAudio Volume Control' to 70% works good for me,

Hope this may help ;)

---

### Post by 6205 on 2009-07-10
regarding codecs, i would also install gstreamer-ffmpeg plugins.

bad sound may be if you have PCM set-up to max. default is cca 75 %

---

### Post by monkeyKata on 2009-07-10
thanks for the tips.  Trying to lower those volume settings to see if that helps

---

