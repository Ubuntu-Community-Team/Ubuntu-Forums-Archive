---
title: "MPlayer error."
date: 2005-01-22
forum: General Help
---

### Post by Jaivaz on 2005-01-22
I've installed it correctly and everything, but when I try and open an .avi file (I think this may be due to the fact it needs the DIVX Codec...) and I get an error telling me that /dev/dsp is currently "in use", and I get no sound, but the video is just find. 


Can anyone help me?


(Also, sorry if this is in the wrong forum.)

---

### Post by poofyhairguy on 2005-01-22
[QUOTE=Jaivaz]I've installed it correctly and everything, but when I try and open an .avi file (I think this may be due to the fact it needs the DIVX Codec...) and I get an error telling me that /dev/dsp is currently "in use", and I get no sound, but the video is just find. 


Can anyone help me?


(Also, sorry if this is in the wrong forum.)[/QUOTE]


Well...I'll help you the best way I can. It is my opinion that Mplayer is so-so. I personally  use a media player in Ubuntu which plays everything and looks nice.

Xine-ui

[http://ubuntuguide.org/#xine-ui](http://ubuntuguide.org/#xine-ui)

Make sure you install the Multimedia Codecs.

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

That last part alone might fix your problem.

---

### Post by Jaivaz on 2005-01-25
I managed to fix the problem, but now I have a new one...

I try and play a video file and the video lags behind the audio.

---

### Post by ctt1wbw on 2005-01-26
I'm still trying to fix my no audio problem in MPlayer.  I can't seem to find the w32codecs anywhere...

---

### Post by Quest-Master on 2005-01-26
sudo apt-get install w32codecs?

Make sure you have universe/multiverse enabled.

---

### Post by ctt1wbw on 2005-01-26
Okay, done.  Thanks.  But I'm still getting the same error:

Could not open/initialize audio device -- no sound

I still haven't been able to fix this so I can use MPlayer...   :?:

---

### Post by RaIrata on 2005-01-27
Try to change audio drivers to EsD in your preferences.

---

### Post by ctt1wbw on 2005-01-27
Okay, I give up.  What are your settings in codecs part of the prefs?  I've tried everything and every combo.

---

