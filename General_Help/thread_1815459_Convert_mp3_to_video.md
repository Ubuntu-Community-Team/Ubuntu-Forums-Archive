---
title: "Convert mp3 to video"
date: 2011-07-31
forum: General Help
---

### Post by BuiltLord on 2011-07-31
Probably posting this in the wrong place or it's a really simple search to find my answer, i assure you i did look i'm just braindead atm. Sorry in advance.


I have found lots of 'Extract audio from video ~ Linux ' but i'm looking for the opposite kinda, i want to find a command line method to attach an image to a mp3 and convert it to a video format (so i can upload it to youtube). Seen websites which do this ( [for example]("http://www.mp32u.net/") )but they add their own ''Converted by xxxxx'' to the upload. Obviously i could download the files after they have been converted and upload them manually and they SHOULD be free from all adverts but, i'd much rarther just have a command or series of to do this. 

Can anyone help?

** It has to be command line, can't be through GUI. **

---

### Post by vanadium on 2011-07-31
This probably can be done with mencoder or ffmpeg. You may search tutorials that provide a suited example of the command line needed.

---

### Post by FakeOutdoorsman on 2011-07-31
Using ffmpeg from the repo (as of Natty):
```
ffmpeg -loop_input -r 5 -i image.jpg -i audio.mp3 -vcodec libx264 -vpre medium -crf 22 -threads 0 -acodec copy -shortest output.mkv
```

Using [compiled ffmpeg](http://ubuntuforums.org/showthread.php?t=786095):
```
ffmpeg -loop 1 -r 5 -i image.jpg -i audio -vcodec libx264 -preset medium -tune stillimage -crf 22 -threads 0 -acodec copy -shortest output.mkv
```
or for lossless H.264:
```
ffmpeg -loop 1 -r 5 -i image.jpg -i audio -vcodec libx264 -preset lossless_slow -threads 0 -acodec copy -shortest output.mkv
```

---

### Post by BuiltLord on 2011-07-31
> **FakeOutdoorsman said:**
> Using ffmpeg from the repo (as of Natty):
```
ffmpeg -loop_input -r 5 -i image.jpg -i audio.mp3 -vcodec libx264 -vpre medium -crf 22 -threads 0 -acodec copy -shortest output.mkv
```Using [compiled ffmpeg]("http://ubuntuforums.org/showthread.php?t=786095"):
```
ffmpeg -loop 1 -r 5 -i image.jpg -i audio -vcodec libx264 -preset medium -tune stillimage -crf 22 -threads 0 -acodec copy -shortest output.mkv
```or for lossless H.264:
```
ffmpeg -loop 1 -r 5 -i image.jpg -i audio -vcodec libx264 -preset lossless_slow -threads 0 -acodec copy -shortest output.mkv
```


Absolute life saver :)

---

