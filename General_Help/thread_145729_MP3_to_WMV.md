---
title: "MP3 to WMV"
date: 2006-03-16
forum: General Help
---

### Post by souteneur3190 on 2006-03-16
Is there some program for ubuntu linux that converts mp3 to wmv in a fast way? I say this because most mp3 players can play up to twice as many song if they are in wma format.

---

### Post by UeB on 2006-03-16
this is not true
if you the take a 128kbit mp3 file and a windows media file with the same quality it will have aproximatly the same bitrate and therefore the same size!
read here for information about audiocodecs:
[hydrogenaudio.org]("http://wiki.hydrogenaudio.org/index.php?title=Main_Page#Audio_Formats")

---

### Post by souteneur3190 on 2006-03-16
With its 2GB capacity you can hold 1000 WMA songs or 500 MP3 songs.

Explain that

---

### Post by souteneur3190 on 2006-03-16
"Even though Microsoft claims it is able to deliver the same quality as MP3 at half the bitrates, that statement is certainly false. A more realistic number would be same quality at around 25% smaller bitrates - and that applies to low bitrates only. At 128kbps, it is easily bested by LAME."

from that site u gave me.

---

### Post by joe_bruin on 2006-03-17
The responder did not answer your question, so here goes:

To my knowledge, there are no Linux apps that can encode WMA.  Windows Media Audio is a proprietary audio stream format and Microsoft does not share the details of the encoding algorithm with anyone, so it is extremely difficult to make an encoder for it.  It can be done using the Windows DLLs, and there may be some encoders that make use of these, but again, I've never specifically heard of any.  It may also be possible to run Windows Media Player using Wine, but this is a fairly advanced topic.

But, the responder made a good point.  Saying twice as many WMA files as MP3 is deceptive, since the WMA files are *lower quality* than the MP3s (despite what Microsoft claims).  You could just as easily make lower quality MP3 files, which would result in smaller files as well, and fit more of those on your player.

---

### Post by UeB on 2006-03-17
ok some precise advice:

take the programme you use to encode mp3 files.
find the option where you can lower the qualitiy.
set a quailty where you get apoximalty the same file sizes as with wma.
encode one song twice with wma and mp3 with a quality set where the output files have aproximatly the same size.
listen to both of them.
decide if the mp3 files sound worse than the wma files.
if not your problem is solved because the mp3 encoding programm will now produce  files with the same size as your wma encoding programm without letting you here the differences.

---

