---
title: "Convert TO m4a"
date: 2009-08-15
forum: General Help
---

### Post by Alligator on 2009-08-15
It's 5am here.  Anyway just a little frustrated with firefox wanting to find a program/script to take a audio cd and convert to m4a (ipod) Maybe I'm doing something wrong - "convert wav to m4a" comes up with a lot of hits with the reverse m4a to wav.  I'm using gtkPod and just trying to add to the library.  It's time to go back to bed.
ps I've searched this forum as well.

Ron

---

### Post by SuperSonic4 on 2009-08-15
edit the third: First of all you will need **faac** and/or **libfaac** as this is the aac encoder. I believe both are in medibuntu

ffmpeg works. For converting to m4a try ```
ffmpeg -i input.wav -ac [COLOR="Red"]2[/COLOR] -ab [COLOR="Red"]160k[/COLOR] -acodec libfaac output.m4a
```

-ac 2 means 2 channel audio (stereo)
-ab 160k means 160kbps bitrate

You can change these values to whichever quality you want.

-------------

You should also be able to use faac (but I need to test that command)

```
faac -q 200 -w input.wav
```

*-q <num> * Set default variable bitrate (VBR) quantizer quality in percent (default: 100). *

*-w * Wrap AAC data in MP4 container (default for *.mp4 and *.m4a). *

* taken from ```
man faac
```

edit the first: that command does work :]
edit the second: both commands work

---

### Post by Alligator on 2009-08-15
Thank you -  merci

---

