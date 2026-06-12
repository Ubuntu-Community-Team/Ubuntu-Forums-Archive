---
title: "Vlc player crashes when opening avi files"
date: 2012-04-11
forum: General Help
---

### Post by GreatDanton on 2012-04-11
Hey!

Yesterday i was playing with the xubuntu settings, and i added Cairo Dock (program to change the look of the desktop). After that i tried to play some avi file, but when i click on it the vlc opened the file and then immediately closed himself.(before playing with the settings everything worked just fine). Mp3 files work ok on it.

I searched on the internet and i only found that i have to change the output of the video file (that solution doesnt work for me, because then i got gpu hung).

I thought, that i did something wrong, so i reinstalled my linux xubuntu 10.04, but the problem still remains.

Movie player does the same, like vlc.

If i run vlc in terminal i got this (in terminal):

> 0x9de4548] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[0x9e0f018] pulse audio output: No. of Audio Channels: 6
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  103
  Current serial number in output stream:  104
My configuration:
Dell inspiron 1100
512 Mb ram
Intel(R) Celeron(R) CPU 2.40GHz
Graphic card: Intel chipset 82845G/GL [Brookdale-G]

So, what i have to do now?


EDIT:
I solved the problem. I upgraded from xubuntu 10.04 to xubuntu 10.10 and now i have newer version of vlc and everything work fine.

---

