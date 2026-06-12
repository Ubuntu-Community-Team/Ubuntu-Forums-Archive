---
title: "Editing System Startup Scripts / Mplayer stream-ripping"
date: 2005-02-26
forum: General Help
---

### Post by ixus_123 on 2005-02-26
I have got Mplayer runneing perfectly at last & am very happy with it.  I just got a link from slashdot.org about the first episode of Battlestar Galactica being available for download.  Great, I thought.  It's in real media & I can only get it to play through a stream.  I tried copying the url. . ..

[http://play.rbn.com/?url=usanet/usanet/g2demand/scifi/battlestar/33/33.rm](http://play.rbn.com/?url=usanet/usanet/g2demand/scifi/battlestar/33/33.rm)

. . . to a link & right click saving but that also didn't work. So I googled & found out it's possible to streamrip using mplayer.  I've tried but keep getting errot messages.  Either the command I am typing is somehow wrong or I need to edit my startup scripts as it tell me.  Thing is, I don't really understand the error message.  I don't know where the startup scripts are or what exactly to edit - even with mplayers 'help'

This what I typed & got back:

```
kieren@ubuntu:~ $ mplayer -dumpstream -dumpfile 339.rm http://play.rbn.com/?url=usanet/usanet/g2demand/scifi/battlestar/33/33.rm
MPlayer 1.0pre6-3.3.4 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon Thunderbird (Family: 6, Stepping: 2)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx


77 audio & 188 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Playing http://play.rbn.com/?url=usanet/usanet/g2demand/scifi/battlestar/33/33.rm.
Resolving play.rbn.com for AF_INET6...
Couldn't resolve name for AF_INET6: play.rbn.com
Resolving play.rbn.com for AF_INET...
Connecting to server play.rbn.com[66.203.112.60]:80 ...
Cache size set to 320 KBytes
Connected to server: play.rbn.com
Stream not seekable!
Core dumped ;)

Exiting... (End of file)
kieren@ubuntu:~ $
``` 

Can anyone tell me what to do from here?

---

### Post by ixus_123 on 2005-02-26
Oh :(

I can't even view the stream with Mplayer & 2005 codec pack

so. . .

I installed Realplayer thinking as a Real Media file, Real Playere for linux will play it.  It doesn't what a silly format Real is :(

---

### Post by ixus_123 on 2005-02-27
test thing I tried on someones advice:

```
 kieren@ubuntu:~ $ sudo echo 1024 > /proc/sys/dev/rtc/max-user-freq
bash: /proc/sys/dev/rtc/max-user-freq: Permission denied
kieren@ubuntu:~ $
``` 

^ As you can see, it didn't work.  How can sudo get denied?  :(

---

### Post by Ste on 2005-02-27
That real file is a meta package.

the content is:

rtsp://rx-wes-sea138.rbn.com/farm/*/usanet/usanet/g2demand/scifi/battlestar/33/33.rm
--stop--
pnm://rx-wes-sea138.rbn.com/farm/*/usanet/usanet/g2demand/scifi/battlestar/33/33.rm

Try them in real player or mplayer.

---

### Post by ixus_123 on 2005-02-28
Thanks.  Neither worked though.  I think I might try the same on [http://www.apple.com/trailerrs/](http://www.apple.com/trailerrs/)  to see if I can rip a quicktime trailer at least.

---

