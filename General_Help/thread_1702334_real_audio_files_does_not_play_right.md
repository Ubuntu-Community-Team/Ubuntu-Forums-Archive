---
title: "real audio files does not play right"
date: 2011-03-07
forum: General Help
---

### Post by linuxcss on 2011-03-07
I am trying to play the following real audio file but it does not play right,
can anyone else hear it correctly if so what codec have you installed??

I have also tried other real audio files from the same website that also do not play correctly.

I am running maverick ubuntu 10.10

[http://www.lesfeldick.org/audio/s01-01.ra](http://www.lesfeldick.org/audio/s01-01.ra)

---

### Post by xtremesupremacy3 on 2011-03-07
If you are referring to the poor quality gargling noise, then it's not your problem, then it's the sites problem, as I am also hearing that lol

---

### Post by ron999 on 2011-03-07
Hi
The link opens for me in Firefox with gecko-mediaplayer plugin.

That stream is some kind of Real codec.
Mono 8Khz 8Kbps.
It sounds terrible.

It can be downloaded using mPlayer like this:-
```
mplayer -bandwidth 99999 -dumpstream -dumpfile s01-01.ra "http://www.lesfeldick.org/audio/s01-01.ra"

```
It's a 1.MB file.
It will play for me with mPlayer but not VLC.

---

### Post by linuxcss on 2011-03-07
i just install mplayer 

and then i try your command but it dumps core

cssadmin@cw200x4b-1:~$ mplayer -bandwidth 99999 -dumpstream -dumpfile s01-01.ra "http://www.lesfeldick.org/audio/s01-01.ra"
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://www.lesfeldick.org/audio/s01-01.ra](http://www.lesfeldick.org/audio/s01-01.ra).
Resolving [www.lesfeldick.org](www.lesfeldick.org) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.lesfeldick.org](www.lesfeldick.org)
Resolving [www.lesfeldick.org](www.lesfeldick.org) for AF_INET...
Connecting to server [www.lesfeldick.org](www.lesfeldick.org)[66.96.134.75]: 80...
Cache size set to 320 KBytes
Resolving [www.lesfeldick.org](www.lesfeldick.org) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.lesfeldick.org](www.lesfeldick.org)
Resolving [www.lesfeldick.org](www.lesfeldick.org) for AF_INET...
Connecting to server [www.lesfeldick.org](www.lesfeldick.org)[66.96.134.75]: 80...
Core dumped ;)

Exiting... (End of file)
cssadmin@cw200x4b-1:~$

---

### Post by ron999 on 2011-03-07
Have you looked to see if the file **_s01-01.ra_** has been downloaded into your home folder?

> ron@ubuntu:~$ mplayer -bandwidth 99999 -dumpstream -dumpfile s01-01.ra "http://www.lesfeldick.org/audio/s01-01.ra"
MPlayer2 2.0-rc1 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://www.lesfeldick.org/audio/s01-01.ra](http://www.lesfeldick.org/audio/s01-01.ra).
Resolving [www.lesfeldick.org](www.lesfeldick.org) for AF_INET6...

Couldn't resolve name for AF_INET6: [www.lesfeldick.org](www.lesfeldick.org)
Resolving [www.lesfeldick.org](www.lesfeldick.org) for AF_INET...
Connecting to server [www.lesfeldick.org](www.lesfeldick.org)[66.96.134.75]: 80...

Cache size set to 320 KBytes
Resolving [www.lesfeldick.org](www.lesfeldick.org) for AF_INET6...

Couldn't resolve name for AF_INET6: [www.lesfeldick.org](www.lesfeldick.org)
Resolving [www.lesfeldick.org](www.lesfeldick.org) for AF_INET...
Connecting to server [www.lesfeldick.org](www.lesfeldick.org)[66.96.134.75]: 80...

Stream dump complete.

Exiting... (End of file)


---

