---
title: "mp3 back to wav transfoming programm"
date: 2006-04-17
forum: General Help
---

### Post by GreveFelix on 2006-04-17
Hello, 
I am using K3b - Burning Programm. its good. But I am not able to burn a Audio CD using mp3 files. With OGG its no problem. 

Is it possible to install some plugin in K3b or is there any MP3 - WAV Transfoming programmm you could suggest?
Thanks for help ...

---

### Post by GreveFelix on 2006-04-29
OK, got it working. An easy fix. I just had to install a plugin.

---

### Post by lemix on 2006-04-30
Okay, i would also like to know what plugin that is cause i have the same problem...

---

### Post by lemix on 2006-04-30
Never mind. Its libk3b2-mp3 for anyone else who wants to know

> sudo apt-get install libk3b2-mp3

---

### Post by stoeptegel on 2006-05-01
wav-> mp3-> wav
is possible, 

but are you guys aware that once the quality is removed by converting wav files to a lossy format, that converting it back doesn't make it sound any better than the lossy format?
So in short you'll only wanna do this for practical use, like when a stereo doesn't support mp3/ ogg vorbis.

---

### Post by n3tfury on 2006-05-01
This probably doesn't apply to you since you were only trying to burn an audio cd, so just an fyi...

I'm sure some people know, but not everyone does:  transcoding is not recommended.  Anytime you transcode from a lossy format, the audio quality gets worse.  You cannot gain back the data you have lost.

---

### Post by GreveFelix on 2006-05-01
I fixed the Problem with adding the gstreamer0.8-pluginns, and there is also a k3b-mp3 pluginn. 

I know the Quality will not be the same as it was, before the first transcoding to mp3 or ogg. But, as you suggested, some People dont have a Cd-player with the abbility of playing MP3. ...  like me :-|

---

