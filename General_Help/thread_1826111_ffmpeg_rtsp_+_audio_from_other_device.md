---
title: "ffmpeg rtsp + audio from other device"
date: 2011-08-16
forum: General Help
---

### Post by taran2L on 2011-08-16
Hello!

I need get video from ip camera (RTSP) and audio from netbook microphone and send to rtmp://

ffmpeg -an -i rtsp://[...] -f alsa -ac 2 -ab 96K -ar 44100 -i hw:0,0 -f flv "rtmp://[...]"

It'is not work! Audio get from ip camera :(

If i get only microphone — sound work!
ffmpeg -ac 2 -ab 96K -ar 44100 -i hw:0,0 -f flv "rtmp://[...]"

HELP!!1

---

### Post by howefield on 2011-08-17
Thread moved to "*General Help*"

---

