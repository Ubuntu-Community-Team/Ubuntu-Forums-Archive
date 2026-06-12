---
title: "what programme is good for recording my screen??"
date: 2011-06-11
forum: General Help
---

### Post by nsk tacticzz on 2011-06-11
hi im looking for a programme like hypercam 2 or camtasia studio 7 which can record my pc but can also speed it up so i can make a speed art in graphics.

wat programme is best on ubuntu for screen recorder but also can speed it up

---

### Post by 3xp10r3r|X13 on 2011-06-11
There is gtk-recordmydesktop, which is quite simple and works quite well and there is ffmpeg, which has loads of other functions and includes more possibilities referring to configuration (conversion of files etc.), but is a bit more difficult to handle (runs in the terminal).

Just use both:

- ffmpeg to convert your files to different formats
- gtk-recordmydesktop to record your desktop

if you want to edit your recordings afterwards (speeding it up), just use kdenlive.

---

### Post by pqwoerituytrueiwoq on 2011-06-11
here are 3 recorders
kazam (not a final release yet last i checked)
xvidcap (it works for me)
recordmydesktop (i have issues with compiz with this one)

---

### Post by Habitual on 2011-06-11
vlc
Istanbul if you "must" be a GUI.

from a terminal, run 
```
ffmpeg -f x11grab -s wxga -r 25 -i :0.0 -sameq ~/mymovie.mpg
``` if you simply need to "Git 'er Done".

YMMV

---

### Post by FakeOutdoorsman on 2011-06-11
> **Habitual said:**
> vlc
Istanbul if you "must" be a GUI.

from a terminal, run 
```
ffmpeg -f x11grab -s wxga -r 25 -i :0.0 -sameq ~/mymovie.mpg
``` if you simply need to "Git 'er Done".

YMMV

Your command doesn't supply a proper rate control method, and sameq doesn't do what most people think it does (*sameq* tells FFmpeg to use the "same quantizer as source", but that does not necessarily mean same quality). A better solution using FFmpeg is shown here:

[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026)

> **nsk tacticzz said:**
> wat programme is best on ubuntu for screen recorder but also can speed it up
FFmpeg can be used to also speed up your video. This example should double the speed of your video. Edit the *setpts* value increase or decrease the speed of the output:
```
ffmpeg -i input -vcodec libx264 -preset medium -crf 23 -acodec copy -vf setpts=0.5*PTS output.mkv
```
*Note*: As of Natty you will have to compile FFmpeg to gain access to FFmpeg filters, such as setpts:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

