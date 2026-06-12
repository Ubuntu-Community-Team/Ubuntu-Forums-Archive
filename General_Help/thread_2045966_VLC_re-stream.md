---
title: "VLC re-stream"
date: 2012-08-22
forum: General Help
---

### Post by adi003 on 2012-08-22
VLC re-stream

Postby adi003 » 2012-08-22 08:13
Hello guys,

How can I re-stream a radio stream using VLC? My company has blocked port 8000,8001 and 8002 but if found several ones opened.

The radio I am trying to re-stream is on port 8000 [http://live.radio.test:8000/listen.pls](http://live.radio.test:8000/listen.pls) (just an ex). What configuration do I have to make to do this re-stream on port 80, 443 or 10000 from my server?

Also i would like the re-stream to start at server restart.

So far I'm thinking this will do the trick (for redirect to port 10000):

Code: Select all
    cvlc -vvv 'http://live.radio.test:8000' --sout '#transcode{vcodec=none,acodec=mp3,ab=128,channels=2,samplerate=44100}:http{mux=raw,dst="localhost:1000"}'  :sout-all :sout-keep



Thanks

Si vers in romana:

am portul portul 8000 blocat. cum fac restream (alt port) la un radio folosind serverul meu si vlc?

---

