---
title: "Windows Media Player"
date: 2010-07-03
forum: General Help
---

### Post by jt867 on 2010-07-03
Hi,

 Can someone recommend a Linux application that compares to Windows Media Player? I am looking for an application that will burn my MP3 music files and convert them to cda to a CD-ROM.

Regards,

John...

---

### Post by luceerose on 2010-07-03
I use sound-juicer (Audio CD Extractor) to rip with the following profile;
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 quality=3 preset=standard vbr-max-bitrate=320 ! id3v2mux

Amarok to play.

Brasero to burn audio cds.

---

### Post by jt867 on 2010-07-04
Thanks, but my MP3 files on on my hard drive, I want to burn these files from MP3 to Wav or cda.

John...

---

### Post by bumanie on 2010-07-04
Have a look at this[ link]("http://www.ehow.com/how_5066158_convert-mp-wav-ubuntu.html") re soundconverter - it will do what you want.

---

### Post by dunnac on 2010-08-31
Thanks Bumanie, I have now successfully coverted and burned. What I don't understand is why I could burn mp3 files with Hardy, but not with Lucid??

---

