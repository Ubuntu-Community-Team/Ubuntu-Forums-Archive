---
title: "winff help please"
date: 2011-05-31
forum: General Help
---

### Post by cowboy7305 on 2011-05-31
libpostproc   51. 2. 0 / 51. 2. 0
[flv @ 0x9dc2420]Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from '/media/New Volume/greatrift_11_01_01.flv':
  Metadata:
    duration        : 2904
    moovPosition    : 36
    width           : 640
    height          : 360
    videocodecid    : avc1
    audiocodecid    : mp4a
    avcprofile      : 77
    avclevel        : 31
    aacaot          : 2
    videoframerate  : 25
    audiosamplerate : 44100
    audiochannels   : 2
  Duration: 00:48:24.04, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 640x360 [PAR 1:1 DAR 16:9], 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16
Unknown encoder 'libxvid'
Press Enter to Continue

when i try to use winff to convert a movie i get the message above any help please

---

### Post by coffeecat on 2011-05-31
> **cowboy7305 said:**
> Unknown encoder 'libxvid'
Press Enter to Continue

Do you have the package "libxvidcore4" installed? If you don't and installing this fixes this problem, you might want to think about installing "ubuntu-restricted-extras" which will bring in a lot of multimedia stuff which you might also need.

---

### Post by cowboy7305 on 2011-05-31
knew i needed something ,i never remember all the extras 
thanks for help

---

### Post by linuxinstalledfromhdd on 2011-05-31
You can install the rest of the codecs here:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

