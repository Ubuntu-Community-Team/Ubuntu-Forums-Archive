---
title: "EOF problem with mplayer - do I need to update?"
date: 2010-12-13
forum: General Help
---

### Post by tobytoby on 2010-12-13
I get the following error when streaming an audio stream with mplayer (the stream runs for a few hours before it happens):
```
ds_fill_buffer: EOF reached (stream: audio)   0% 
ds_fill_buffer: EOF reached (stream: audio)   0% 
EOF code: 1  27:19.6) of -0.0 (unknown)  1.0% 0% 

Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: mp3lib
vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)
```

The version of mplayer is: MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team

The command I start the stream with is: /usr/bin/mplayer -slave -input file=/tmp/mplayer-control [http://www.musicstreamsomething](http://www.musicstreamsomething) -user myusername -passwd mypassword -v -cache 1024 -cache-min 80

I have tried it on Ubuntu 10.04 as well as 10.10, tried the (old) rc3 Mplayer from Ubuntu.com:s repositoies, another version from 2010-04-16, but always with the same result.

I have seen that this EOF problem has been a problem on some versions. Does someone know where I can find a repository with a really new version of mplayer? (I have tried to compile from source but I just get a lot of errors so I prefer using a repository)

Thanks/

---

