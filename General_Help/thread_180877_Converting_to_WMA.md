---
title: "Converting to WMA"
date: 2006-05-23
forum: General Help
---

### Post by silhouette on 2006-05-23
I know there is a way to convert WMA files to WAV files using MPlayer... but is there a way to convert WAV to WMA?

---

### Post by RudolfMDLT on 2006-05-23
Yip! Soundconverter. 

In the terminal type:

> sudo apt-get install soundconverter

After the install:

Application => Sound & Video => Sound Converter

Just setup the output folder in prefrences or it'll dump everything in the source folder.

---

### Post by frodon on 2006-05-23
Audioconvert is realy good too : [http://ubuntuforums.org/showthread.php?t=82806](http://ubuntuforums.org/showthread.php?t=82806)

---

### Post by silhouette on 2006-05-23
Awesome. I've never heard of soundconverter, so I'll have to see how that works. I *have* read that thread about audio-convert, but looking through the source code it seems like WAV -> WMA hasn't been implemented yet.

---

### Post by adi-beg on 2006-06-13
It's not working. Options of output file formats are: ogg vorbis, mp3, flac and wav. But not wma...:-(

---

### Post by Andrew Golightly on 2006-06-26
I'm interested in using SoundConverter too.. but want to convert all my wma files to something like ogg so I can burn a Cd using serpentine.

SoundConverter looks likes it's processing the files, but then unfortunately doesn't actually do anything. I guess it's pretty obvious when it says "conversion done, in 1s"

Basically just want to create an audio cd using serpentine from wma files. Audio-convert doesn't seem to work too well either. :p

Any ideas or helpful hints?

A

---

### Post by lixy on 2006-07-13
That soundconverter seems to fail silently as Andrew mentionned. Here's something I came across that did the trick for me. [http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Convert_WMA_to_MP3]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Convert_WMA_to_MP3")
Note that ```
-ao pcm -waveheader
``` is deprecated and should be replaced with ```
-ao pcm:waveheader
```
Have a nice day folks,

---

