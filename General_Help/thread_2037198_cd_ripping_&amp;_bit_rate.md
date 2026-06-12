---
title: "cd ripping &amp; bit rate"
date: 2012-08-03
forum: General Help
---

### Post by Vega on 2012-08-03
Seems lately the only options I have without loss in quality is FLAC. I'm wondering if I can rip Audio CDs in 320VBR. I've tried some common applications but it was a no go. 

Anyone know of any nice alternatives?

---

### Post by David Andersson on 2012-08-03
> **Vega said:**
>  I've tried some common applications but it was a no go. 

What did you try?

I used *Sound Juicer* few years ago (package sound-juicer, menu name Multimedia>Audio CD Extractor). You can add output formats (profiles) as you wish. Look at the 160 kbit profile and make a new 320 kbit profile.

*VLC* can rip CDs, but it is not the most user friendly for this purpose. Open CD. Select Audio CD. Select a track. Select Convert in stead of Play. Look at the MP3 profile (128 kbit) and change it to 320 kbit or create a new profile for 320 kbit. 

Another ripping program is *Ripper X* (package ripperx). Click Config and select Target directory and MP3 parameters. Click CDDB. Click Select All. Click Go!.

Other ripping programs I have not tried are *K3b* and *Asunder*.

If you like the terminal you may want use the commands *cdparanoia* and *lame*, possibly in a script for repeated use. Cdparanoia extracts wav files. Lame converts to mp3.
```
cdparanoia --batch
for f in track*.wav; do lame --preset extreme "$f" "${f%.wav}.mp3"; done
```

(Replace "extreme" with "insane" if you are not only extreme but insane about audio quality.)

Another command line ripper is *abcde*:
```
abcde -p -o mp3:"--preset extreme"
```
(As many other rippers it simply uses cdparanoia and lame behind the scene. Compared to the pure use of cdparanoia and lame commands, abcde also set tags and filenames from CDDB.)

---

### Post by Vega on 2012-08-04
> **David Andersson said:**
> What did you try?

I used *Sound Juicer* few years ago (package sound-juicer, menu name Multimedia>Audio CD Extractor). You can add output formats (profiles) as you wish. Look at the 160 kbit profile and make a new 320 kbit profile.

*VLC* can rip CDs, but it is not the most user friendly for this purpose. Open CD. Select Audio CD. Select a track. Select Convert in stead of Play. Look at the MP3 profile (128 kbit) and change it to 320 kbit or create a new profile for 320 kbit. 

Another ripping program is *Ripper X* (package ripperx). Click Config and select Target directory and MP3 parameters. Click CDDB. Click Select All. Click Go!.

Other ripping programs I have not tried are *K3b* and *Asunder*.

If you like the terminal you may want use the commands *cdparanoia* and *lame*, possibly in a script for repeated use. Cdparanoia extracts wav files. Lame converts to mp3.
```
cdparanoia --batch
for f in track*.wav; do lame --preset extreme "$f" "${f%.wav}.mp3"; done
```

(Replace "extreme" with "insane" if you are not only extreme but insane about audio quality.)

Another command line ripper is *abcde*:
```
abcde -p -o mp3:"--preset extreme"
```
(As many other rippers it simply uses cdparanoia and lame behind the scene. Compared to the pure use of cdparanoia and lame commands, abcde also set tags and filenames from CDDB.)

I tried Rythembox, Nightingale, and some other cd ripping program that I found on the ubuntu software center.

Ripper X seems to be the one.

Thx for the suggestion!

---

### Post by ads52 on 2012-08-11
I would like to echo David Andersson's comments about abcde as one of the more flexible cd rippers available. You may be interested to know that you can also run the application from a configuration file rather than directly from the commandline. At the risk of (once again) pimping my own site, there is a set of examples here to start customising for your own use:

[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

Well worth even a brief look, and of special interest is the fact that abcde is under active development again...

---

