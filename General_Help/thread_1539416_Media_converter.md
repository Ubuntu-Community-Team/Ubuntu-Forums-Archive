---
title: "Media converter"
date: 2010-07-26
forum: General Help
---

### Post by michael.the.bone on 2010-07-26
Does anyone know of a good media converter program?

I want to convert a .wav format file to .mp3...

Cheers.

M

---

### Post by nmaster on 2010-07-26
you say media, but isn't mp3 just for audio? ... look at soundconverter.  by default it'll convert to ogg, but you can change that (i think).

---

### Post by grantoos on 2010-07-26
Look for a program called "Sound Converter", very simple and straightforward. It actually converted some old files I had from RM to MP3!

---

### Post by pricetech on 2010-07-26
Audacity will do it as long as you have Lame installed.

---

### Post by ajgreeny on 2010-07-26
If you are not afraid of the command line ffmpeg is the way to go, though you will need one or more of several libraries to encode mp3s.  Install libavcodec-extra-52, (most important), libavdevice-extra-52, libavfilter-extra-0, libavformat-extra-52, and libavutil-extra-49, plus ffmpeg and you should be good to go.  If you must have a gui, try winff.

The command line will you more control than the gui versions, and will be a lot quicker than audacity.  Also the ubuntu sound-converter package is somewhat broken at the moment and will not allow you to encode to VBR, and defaults to CBR at 128bps, I think.

---

### Post by FakeOutdoorsman on 2010-07-26
You could use **lame** by itself:
```
lame input.wav -V 4 output.mp3
```
You could combine this with the *find* command to encode many WAV all at once.
```
for input in *.wav; do lame $input -V 4 `basename $input .wav`.mp3; done;
```

---

### Post by robotman5 on 2010-07-26
this program might work [http://download.cnet.com/WAV-to-MP3-Encoder/3000-2140_4-10060500.html](http://download.cnet.com/WAV-to-MP3-Encoder/3000-2140_4-10060500.html)


make sure to use Wine

---

### Post by scouser73 on 2010-07-27
> **grantoos said:**
> Look for a program called "Sound Converter", very simple and straightforward. It actually converted some old files I had from RM to MP3!

+1 for this.

---

### Post by HermanAB on 2010-07-27
Sox

---

### Post by cascade9 on 2010-07-27
> **ajgreeny said:**
> The command line will you more control than the gui versions, and will be a lot quicker than audacity.  Also the ubuntu sound-converter package is somewhat broken at the moment and will not allow you to encode to VBR, and defaults to CBR at 128bps, I think.

Huh? AFAIK, you can get all the options from a command line on a GUI.....maybe not with soundconvter (I dont use it) but with grip, sure. I *think* that you can get all the options wtih soundkonvter as well.

---

