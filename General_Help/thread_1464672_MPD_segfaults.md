---
title: "MPD segfaults"
date: 2010-04-28
forum: General Help
---

### Post by arrrghhh on 2010-04-28
So MPD keeps segfaulting everytime it tries to play anything.  I tried compiling a version from the MPD site, but that couldn't even see my music for some reason.  Same user running MPD, same permissions on the files...

So I'm at a loss here.  I'd really like to get MPD working again, but it keeps segfaulting with this:
```
nas kernel: [161048.253573] mpd[22957] general protection ip:b6efc1b5 sp:b53e1850 error:0 in libavcodec.so.52.20.1[b6ab4000+52b000]
```

Anyone use MPD or is perhaps wise enough to assist me with this problem?  I wiped my server recently because of all the custom stuff I had installed, and now MPD won't play music :(

Any help would be greatly appreciated, thanks!

---

### Post by arrrghhh on 2010-04-29
So this thread makes me think...

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=556198](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=556198)

It sounds like the EXACT problem I'm having.  Their issue was fixed with an update, I'm running 10.04 -server with all the updates... What can I do?!?

Confirmed - I can play MP3's, but M4A/AAC files cause MPD to segfault.  What package/codec am I missing, I thought it was faad/libfaad2, which is installed....

---

