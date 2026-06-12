---
title: "darkice stopped working"
date: 2010-09-10
forum: General Help
---

### Post by baddnady23 on 2010-09-10
I run a darkice audio streaming server at my place and it has been trouble free for nearly six months now.  Tonight, out of no where it stopped working and I cant get it to restart.  It runs on a headless server so any maintenance I do is ssh'ed into it.  This is the output I get when I attempt to start the server:
```
andrew@andrew-server:~$ sudo darkice -c /etc/darkice.cfg
DarkIce 0.19 live audio streamer, http://darkice.tyrell.hu/
Copyright (c) 2000-2007, Tyrell Hungary, http://tyrell.hu/

Using config file: /etc/darkice.cfg
Using OSS DSP input device: /dev/dsp
Using POSIX real-time scheduling, priority 98
[COLOR="Red"]DarkIce: TcpSocket.cpp:248: connect error [110][/COLOR]

```

I have rebooted the computer twice and made 0 changes to it or to the input audio capture device...and I'm all out of ideas tonight.

---

