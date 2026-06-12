---
title: "Convert music files?"
date: 2006-06-25
forum: General Help
---

### Post by Cable on 2006-06-25
What program can I use to convert music files from FLAC to other formats?

---

### Post by Patsoe on 2006-06-25
[QUOTE=Cable]What program can I use to convert music files from FLAC to other formats?[/QUOTE]

There's a tool called soundconverter. I don't have experience with it though.
NB: there's also a package called soundconvert, that's yet something else...
Both are in the universe repository.

Alternatively, you could use gstreamer pipes, if you're into a bit of weird command line notation :)
It's not really hard and it's quite fast and convenient once you get the hang of it, I guess.

---

### Post by vigleik on 2006-06-25
You're also supposed to be able to use lame, at least for mp3. For example "lame infile.flac outfile.mp3". Except it doesn't work for me right now, outfile.mp3 consists entirely of static. Strange....

Vigleik

---

### Post by vigleik on 2006-06-25
All right, converting directly from flac to mp3 seems to be no good, but first converting from flac to wav with flac (!) and then from wav to mp3 with lame seems to work. If you don't like the command line then something like soundconverter (or soundkonverter if you like kde) should work nicely.

Vigleik

---

### Post by jethro10 on 2006-06-26
Gnormalize also converts and has a GUI, 


jeff

---

### Post by matrooswolf on 2006-06-26
I use audio-convert, it is a plugin for Nautilus (a script).  If it is installed, you can simply right-click on a file and convert it from within nautilus.  I use it for flac, ape, ogg, mp3, etc ...

You can find audio-convert in synaptic.  

Then, run
```

audio-convert-install
```
in a terminal.

(You maybe have to install some extra packages to have all the formats working, but I don't remember at the moment (and I gotta work, to bring the money home ;))

---

### Post by kingcharles1666 on 2008-04-06
After installing from synaptic I had:

To enable this script run the following as user:
nautilus-script-manager enable ConvertAudioFile

To disable it run the following as user:
nautilus-script-manager disable ConvertAudioFile

AMD64 Gutsy user
Works great though for converting MP3 to AAC for my nokia phone.

---

### Post by sekinto on 2008-04-06
soundconverter is a nice program, I use it myself. But I am writing a program in Python because the bitrate options in soundconverter are kind of limiting.

---

### Post by kingcharles1666 on 2008-04-06
I tried soundconverter but the version in the repo does not support AAC

---

