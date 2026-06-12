---
title: "mplayer i have installed the codecs with problems"
date: 2006-01-23
forum: General Help
---

### Post by njzillest on 2006-01-23
i installed Mplayer and its codecs through automatix. When i try to play an asx file, it sais something along the lines of wrong video codecs. I went to the preferces, codecs tab and looked into the video codecs family. I Have about 25 codecs installed. I have no idea wich video, and audio codec i should use to play ASF files and DVD's

---

### Post by emitter on 2006-02-01
Hi!

I have the same problem. I wanted to listen to this stream [http://www.hirtv.net/adas.asx](http://www.hirtv.net/adas.asx) (a hungarian TV-stream)
I use Ubuntu 5.10 and mplayer. But all the other players in gnome I've tried didn't work.

Starting from console, I get this:

[INDENT]emitter@LAPTOP:~$ mplayer [http://www.hirtv.net/adas.asx](http://www.hirtv.net/adas.asx)
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Intel  ( Family: 6, Stepping: 8 )
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing [http://www.hirtv.net/adas.asx](http://www.hirtv.net/adas.asx).
STREAM_HTTP(1), URL: [http://www.hirtv.net/adas.asx](http://www.hirtv.net/adas.asx)
Resolving [www.hirtv.net](www.hirtv.net) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.hirtv.net](www.hirtv.net)
Resolving [www.hirtv.net](www.hirtv.net) for AF_INET...
Connecting to server [www.hirtv.net](www.hirtv.net)[195.70.35.150]:80 ...
STREAM_ASF, URL: [http://www.hirtv.net/adas.asx](http://www.hirtv.net/adas.asx)
Resolving [www.hirtv.net](www.hirtv.net) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.hirtv.net](www.hirtv.net)
Resolving [www.hirtv.net](www.hirtv.net) for AF_INET...
Connecting to server [www.hirtv.net](www.hirtv.net)[195.70.35.150]:80 ...
size_confirm mismatch!: 22611 28271
Error while parsing chunk header
failed, exiting
STREAM_HTTP(2), URL: [http://www.hirtv.net/adas.asx](http://www.hirtv.net/adas.asx)
Resolving [www.hirtv.net](www.hirtv.net) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.hirtv.net](www.hirtv.net)
Resolving [www.hirtv.net](www.hirtv.net) for AF_INET...
Connecting to server [www.hirtv.net](www.hirtv.net)[195.70.35.150]:80 ...
Cache size set to 1024 KBytes
Cache fill:  0.03% (303 bytes)[/INDENT]


What sort of codec do I need to avoid this?
Somebody told me that avisynth.dll is the correct codec for asx-stream. I have this dll in directory /usr/local/lib/codecs. I've also made symlinks to this dir from /usr/local/lib/win32 and /usr/local/win32, as this guy suggested.

I would really appreciate any help from you!
Thx


Ps. sorry for my english :-\"

---

### Post by renzokuken on 2006-02-01
assuming you are using firefox as your browser, install the firefox mplayer plugin and see if the .asx files work through firefox

---

### Post by emitter on 2006-02-01
But I have this plugin, still it don't work. Because it only forwards the stream to mplayer, which cannot play it, you know...
I also have MediaPlayerConnectivity ext, it does the same.

mod: It's interesting that the Mozilla-mplayer plugin doesn't appear in about:plugins...
I installed the plugin with synaptic
I use FF 1.5

---

### Post by emitter on 2006-02-02
Up!
Pls help!

---

### Post by emitter on 2006-02-02
tha 2nd (and last) up for today:(
is there nobody who had a problem like this? pls!!!

---

### Post by TechSonic on 2006-02-02
I have a working mplayer in mine, even if you were able to view it, it would stop it after it buffers.  That stream is not compatible anyways.

---

### Post by emitter on 2006-02-02
ye, thanks!
meanwhile I've been informed so too
the stream uses maybe wmv9-codec, and it's not open-source - if I'm right...
so nothing can be done, I can only wait for MS publishing its code.. what a sh1t :(
or for the TV-webmaster streaming in an open format:-k

---

### Post by bram on 2006-07-18
> **emitter said:**
> 

STREAM_HTTP(2), URL: [http://www.hirtv.net/adas.asx](http://www.hirtv.net/adas.asx)
Resolving [www.hirtv.net](www.hirtv.net) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.hirtv.net](www.hirtv.net)
Resolving [www.hirtv.net](www.hirtv.net) for AF_INET...
Connecting to server [www.hirtv.net](www.hirtv.net)[195.70.35.150]:80 ...
Cache size set to 1024 KBytes
Cache fill:  0.03% (303 bytes)[/INDENT]


What sort of codec do I need to avoid this?
Somebody told me that avisynth.dll is the correct codec for asx-stream. I have this dll in directory /usr/local/lib/codecs. I've also made symlinks to this dir from /usr/local/lib/win32 and /usr/local/win32, as this guy suggested.




If you check the asx file you will see it's a playlist.

Passing -playlist to mplayer will solve your problem.
(mplayer -playlist [http://streamlalalala/lala.asx](http://streamlalalala/lala.asx))

---

