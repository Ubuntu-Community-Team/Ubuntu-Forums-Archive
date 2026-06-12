---
title: "vlc using high amounts of memory"
date: 2011-04-30
forum: General Help
---

### Post by 55tptag on 2011-04-30
Hello,

I just installed Kubuntu 11.04.

I ran VLC and it brought my PC to a halt.

I attached a picture of memory usage from htop.

Why do you think VLC is using so much system resources?

Thank you.

---

### Post by blueridgedog on 2011-04-30
There appears to be several running instances of VLC.  Try killing them off and playing a single item.  The following should kill them all:

```
killall vlc
```

---

### Post by 55tptag on 2011-05-01
Thanks but it's normal to see the program listed more than once.  So, unfortunately that's not the fix.  

I did uncheck "Enable desktop effects" in the "Desktop Effects - System Settings" and VLC is playing better now.

---

### Post by KweeK on 2011-05-07
I have the same problem. I played a game of Spider (Kpatience) while I watched a 720p video downloaded from youtube and it really got out of hand.

Top gave info about 82% memory usage for vlc and my whole desktop froze untill I killed vlc. There is a discussion about it over here [http://forum.videolan.org/viewtopic.php?t=67478](http://forum.videolan.org/viewtopic.php?t=67478) but no solution. The vlc ppl mostly say it is a gtk or pulse bug and not a vlc bug.

I don't have Desktop Effects on. So that's not causing the memory leak.

I switched to smplayer for now. Hope it will be fixed in the future.

---

