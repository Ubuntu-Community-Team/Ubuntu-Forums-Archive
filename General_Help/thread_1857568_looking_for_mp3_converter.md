---
title: "looking for mp3 converter"
date: 2011-10-10
forum: General Help
---

### Post by elkhedewy on 2011-10-10
Hello,
i have 10G.B. videos .VOB Files, and i need to convert them all to mp3 .
Any ideas??

---

### Post by thatguruguy on 2011-10-10
mp3 is for audio.  Are you sure that's what you want?

---

### Post by dniMretsaM on 2011-10-10
Both FFmpeg and VLC can do batch command line converting with a BASH script (or a script in some other language. BASH is the most common for simple stuff like that though). If you're not up for command line work, try one of the many GUI converters out there. SoundConverter and soundKonverter are two popular ones (I use soundKonverter) that can do that. I'm not 100% sure they handle .vob files (never used them) but they should. Make sure you have the correct [FONT=Courier New]*buntu-restricted-extras[/FONT] package for your distribution installed (you'll need it to convert to MP3). And are you sure you want to convert all those videos to audio? If you want them to still be videos, use Ogg Theora (.ogv) or something.

---

### Post by elkhedewy on 2011-10-11
Yes Mp3 Audio

---

### Post by elkhedewy on 2011-10-11
i tried the above applications, but i got an error :
FAILED:
The requested plugins are:

DVD subpicture decoder

---

### Post by andrew.46 on 2011-10-14
> **elkhedewy said:**
> i tried the above applications, but i got an error :
FAILED:
The requested plugins are:

DVD subpicture decoder

Can you give the FFmpeg command you used and the uncut terminal output? If actually you missed using FFmpeg the syntax will be something like:

```
ffmpeg -i *input.vob* -vn -acodec libmp3lame -ab 128k *output.mp3*
```

You may need to visit this guide if you do not have mp3 encoding enabled in your copy of FFmpeg:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

