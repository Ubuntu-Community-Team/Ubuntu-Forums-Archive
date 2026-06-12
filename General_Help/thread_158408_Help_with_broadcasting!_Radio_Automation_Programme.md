---
title: "Help with broadcasting! Radio Automation Programme wanted!"
date: 2006-04-11
forum: General Help
---

### Post by marc5000 on 2006-04-11
Ok, so I had been (in windows) broadcasting my own radio station through a programme called Sam3 Broadcaster then to my icecast2 server. Thing is I still have my icecast2 server up and running, but nothing to broadcast to it with, now I am in Linux!  :( Are there any good ways to broadcast media and microphone through an encoder and to my icecast2 server? 

Let me know what you guys find. Maybe we could set up a development team, making a descent programme like Sam3 but for Linux! 

Marc5000

---

### Post by Revolution on 2006-04-11
Google is your friend.

[http://www.gnuware.com/icecast/chap_09_07.html](http://www.gnuware.com/icecast/chap_09_07.html)
[http://gentoo-wiki.com/HOWTO_Icecast_OGG_and_MP3_streaming](http://gentoo-wiki.com/HOWTO_Icecast_OGG_and_MP3_streaming)
[http://www.linuxdevcenter.com/pub/a/linux/2001/03/23/streaming_media.html](http://www.linuxdevcenter.com/pub/a/linux/2001/03/23/streaming_media.html)

---

### Post by marc5000 on 2006-04-11
Ok, thanks. Just some problems that I face! >.< how typical! So I installed darkice and darksnow. I presume darkice works fine, but when I use darksnow, I configure everything to my Icecast2 Server, but when it comes to the devices, some of them work, for about 10 seconds then the server stops! :s and some of them don't work at all?!?! Whats going on? 

When I run a jack_audio I get an error message: 

Using config file: /home/marc/.darksnow/darkice.cfg
DarkIce: AudioSource.cpp:95: trying to open JACK device without support compiledjack_auto [0]


and when I run a /dev/dsp 

The server starts then cuts out, error message as follows: 

Using config file: /home/marc/.darksnow/darkice.cfg
DarkIce: OssDspSource.cpp:279: read error [0]

Hope someone can sort this out! 

Thanks Marc5000

---

