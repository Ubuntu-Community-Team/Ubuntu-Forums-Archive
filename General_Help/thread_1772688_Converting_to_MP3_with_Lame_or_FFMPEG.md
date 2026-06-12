---
title: "Converting to MP3 with Lame or FFMPEG"
date: 2011-05-31
forum: General Help
---

### Post by joshuachoo on 2011-05-31
Is there a difference in quality between converting an audio file (e.g. *.wav) to MP3 using LAME or FFMPEG? Or do they produce the same results?

---

### Post by linuxinstalledfromhdd on 2011-05-31
I'm not sure, I use lossless instead. The quality sounds great though:

[http://manpages.ubuntu.com/manpages/natty/man1/dir2ogg.1.html](http://manpages.ubuntu.com/manpages/natty/man1/dir2ogg.1.html)

---

### Post by joshuachoo on 2011-05-31
Thanks, but lossless quality takes up too much space :P

---

### Post by linuxinstalledfromhdd on 2011-05-31
I could be wrong, but doesn't ffmpeg use lame to create mp3s? 

There is a really cool application you can check out called:

Audacity

Audacity is a multi-track audio editor for Linux/Unix, MacOS and
Windows.  It is designed for easy recording, playing and editing of
digital audio.  Audacity features digital effects and spectrum
analysis tools.  Editing is very fast and provides unlimited
undo/redo.

Supported file formats include Ogg Vorbis, MP2, MP3, WAV, AIFF, and AU.

You can install it from terminal with:

sudo apt-get install audacity

For more converters scroll to the bottom of this guide:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by joshuachoo on 2011-06-01
> **linuxinstalledfromhdd said:**
> I could be wrong, but doesn't ffmpeg use lame to create mp3s? 

I think you are right, though I was not so sure about it. I guess that I may as well convert to MP3 with FFMPEG alone. Thanks though!

---

### Post by FakeOutdoorsman on 2011-06-01
FFmpeg uses libmp3lame, the LAME MP3 encoding library, so the quality should be the same in theory.

Don't forget that FFmpeg can use the -aq option instead of -ab to create VBR audio. "-aq 5" is basically the same as "lame -V5".

Also, you could use both FFmpeg and LAME with a pipe to avoid making an intermediate WAV file and giving you access to whatever additional LAME options you want. Example:
```
ffmpeg -i input -f wav - | lame -V4 - output.mp3
```

---

### Post by joshuachoo on 2011-06-02
> **FakeOutdoorsman said:**
> Don't forget that FFmpeg can use the -aq option instead of -ab to create VBR audio. "-aq 5" is basically the same as "lame -V5".

What's the difference between setting the bitrate "-ab", and setting audio quality "-aq"? What difference would it make if I excluded "-aq 5".

---

### Post by ron999 on 2011-06-02
> **joshuachoo said:**
> What's the difference between setting the bitrate "-ab", and setting audio quality "-aq"? 

Hi
Using -ab sets the bitrate for _**Constant**_ Bit Rate.
Using -aq sets the quality for _**Variable**_ Bit Rate.

---

### Post by FakeOutdoorsman on 2011-06-02
> **joshuachoo said:**
> What difference would it make if I excluded "-aq 5".

If you excluded aq, then ffmpeg would use a default setting of -ab 64k. External encoder libraries, such as libmp3lame, all use different ranges for the aq value, so using *-aq 5* would not necessarily work the same if you changed from *-acodec libmp3lame* to *-acodec libfaac*. If you want to know what value to use, then see: *lame --longhelp* or *man lame* and look at the *-V* option. Also see: [Recommended Encoder Settings for LAME](http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_encoder_settings).

---

