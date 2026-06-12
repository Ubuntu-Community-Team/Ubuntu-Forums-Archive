---
title: "Exaile progress bar not working"
date: 2010-03-21
forum: General Help
---

### Post by piyushchandrakar on 2010-03-21
I just installed exaile on my karmic.
when i want to seek forward a particular track using the progress bar it is not getting forwarded.
previously it was running excellent.. before i formatted my pc.. i just installed ubuntu again.. and now the problem coming up

---

### Post by piyushchandrakar on 2010-03-21
if you are playing MP3 file than

Easy.. dont worry install gstrreamer ugly plugin

 Troubleshooting
Progress bar stuck at 0:00

First, make sure there are no problems with your sound architecture (ALSA, OSS, etc.). And your playback sink in Exaile is set correctly. Try setting it to automatic first.

If you're trying to listen to an MP3 file, try playing an audio file encoded in a different format, such as .ogg or .flac. If these play correctly then try installing gstreamer-ugly.

pacman -S gstreamer0.10-ugly gstreamer0.10-ugly-plugins


you can do this by using synaptic package manager

or just try to play any wmv file in your ubuntu default movie player..
it asks for installation of that plugin just say yes.

---

