---
title: "converting .ogg to .mp3"
date: 2010-02-03
forum: General Help
---

### Post by redbull1415 on 2010-02-03
I need to convert a couple files on a CD to .mp3 files to put them on my mp3 player. I searched help and these forums, and can't find an answer.

---

### Post by Bradj47 on 2010-02-03
> **redbull1415 said:**
> I need to convert a couple files on a CD to .mp3 files to put them on my mp3 player. I searched help and these forums, and can't find an answer.

If this is a regular audio CD you bough from Independent Records or Amazon or something, it's probably either .cda or .wav and you should be able to extract it using the default CD extractor that comes with Ubuntu. I doubt it's .ogg. 

If not, try Sound Converter. **sudo apt-get install soundconverter** should work.

---

### Post by redbull1415 on 2010-02-03
No. I loaded all the songs into rythembox, and went into my music folder, and all the songs ended with .ogg .

---

### Post by Enigmapond on 2010-02-03
```
sudo apt-get install soundconverter
```

---

### Post by redbull1415 on 2010-02-03
Never mind. Found the download to the mp3 file converter for the program. Thanks for the help guys. Very much appreciated.

---

### Post by Enigmapond on 2010-02-03
> **redbull1415 said:**
> Tried the soundconverter program, I can't figure out how to make it convert into .mp3 files. It just has two other kinds of formats.


In the preference you can change the format, I have ogg, mp3, FLAC, wav and m4a listed.

---

### Post by Lars Noodén on 2010-02-04
You may want to try to upgrade your music player to work with Ogg.  

In addition to the usual arguments about open standards that apply, the sound quality of Ogg Vorbis is much better than for MP3 if the files are to be the same size.  Or you can have the same quality with a smaller Ogg file.  

Transcoding from lossy format to lossy format **multiplies** the degradation in sound quality.  So if you want to make MP3s from Vorbis or Ogg Vorbis from MP3, don't try.  Instead, find the 'originals' either on CD or in FLAC or WAV or other *lossless* format and re-rip to the lossy format.

---

