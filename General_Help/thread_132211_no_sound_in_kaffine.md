---
title: "no sound in kaffine"
date: 2006-02-17
forum: General Help
---

### Post by dphipps on 2006-02-17
I just installed kubuntu on my computer.  Kaffine runs but does so without sound.  There is no problems with other programs like amaroK.  Does anybody know what I can do to fix this.

---

### Post by amoser on 2006-02-18
Try installing Kaffeine-xine,  and under the preference menu, change the engine to Xine.

~Alan

P.S. If I am a bit off, I am doing it from memory, I haven't used KDE in three months

---

### Post by Rog131 on 2006-02-18
Launch kaffeine in konsole -> get error messages (if any).

---

### Post by dphipps on 2006-02-18
I have install kaffeine-xine and changed the engine to Xine but it does not seem to help.  From the konsole I get this.
```
DVB 0 : No such file or directory
DVB 1 : No such file or directory
DVB 2 : No such file or directory
DVB 3 : No such file or directory
```

---

### Post by Rog131 on 2006-02-18
And when you play the file ...

---

### Post by Rog131 on 2006-02-18
What do you get from Player>Track info ?

Especially Mime and Audio.

---

### Post by dphipps on 2006-02-18
> And when you play the file ...
It just plays no errors or anything (except to sound).

> What do you get from Player>Track info ?
Here are too examples of what I get.

Length: 0:01:00
Mime: video/mpeg
Audio: MPEG layer 2/3 0kb/s
Video: MPEG (libmpeg2) 352x271

Length: 0:03:41
Mime: video/x-msvideo
Audio: MPEG layer 2/3 0kb/s
Video: ISO MPEG-4 (DivX5, ffmpeg) 640x430

---

### Post by Rog131 on 2006-02-18
Problem is here: Audio: MPEG layer 2/3 0kb/s

0kb/s -> no sound ?

I get:

Length:
0:44:09
Mime:
video/x-msvideo
Audio:
MPEG layer 2/3 128kb/s
Video:
ISO MPEG-4 (XviD, ffmpeg) 720x576

---

### Post by dphipps on 2006-02-18
The files I used have sound.  I think the 0kb/s just futher confirms that there is a problem with sound in Kaffeine.  It might be something to do with my sound drivers but i just don't know what to do about it.

I have had Kaffeine do this on other installations and never solved it.

---

### Post by Rog131 on 2006-02-19
There is small (about 20kb+kommander) tool for check avi info.

Kommander - visual dialog builder and executor tool (It is in the repositories).

AviUtils  (works with konqueror)
Description:
Little tool for lazy peoples, to visually work with avi files.
It can change fourcc and can accept a command line argument: filepath of the avi. Designed for seamless migration from win
apps Gspot and Fourcc changer.

[http://www.kde-apps.org/content/show.php?content=33026](http://www.kde-apps.org/content/show.php?content=33026)

AviUtils gives me audio info:
Freq.: 44100 Hz          Codec: n
Bitrate:127 kbps          Channels: 2
Type CBR                   format: 0x55
chunks: 66229             bytes: 42296310

---

