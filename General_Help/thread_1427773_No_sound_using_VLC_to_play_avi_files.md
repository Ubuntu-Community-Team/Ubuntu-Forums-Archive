---
title: "No sound using VLC to play avi files"
date: 2010-03-11
forum: General Help
---

### Post by hdrip on 2010-03-11
Trying to figure out why when I open an avi file in VLC I get no sound.

I ran it from Terminal and this is what was spewed out...

VLC media player 1.0.2 Goldeneye
[0x98b3140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xb7326880] pulse audio output: No. of Audio Channels: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0xb7326880] pulse audio output error: Failed to connect to server: Connection refused
[0xb7326880] pulse audio output error: Pulse initialization failed
[????????] x11 video output error: X11 request 132.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  102
  Current serial number in output stream:  103


As a side note I did remove PulseAudio and install Esound then removed Esound and installd PulseAudio again, hopefully I did it right, because I get system sounds and no problem with music or youtube for example.

Any help would be appreciated.

Thanks

---

### Post by fusky on 2010-10-24
I am getting the same problem in ubuntu 10.10 ,i can play files with the other native program fine but when i try it in vlc i get no sound at all. im not sure how to run in terminal so i cant say what it says.

---

