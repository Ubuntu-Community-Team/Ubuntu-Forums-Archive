---
title: "No video when playing m4v format"
date: 2011-07-15
forum: General Help
---

### Post by manybodycpa on 2011-07-15
Dear all,

Recently, I noticed that I can no longer see any video when playing m4v
files (audio is OK). These files worked fine until recently, and the problem persists across mplayer, totem, banshee and even firefox.

I am running Natty with the 2.6.39 kernel. Any tips regarding how to
debug this are appreciated.

Thanks,

Martin

---

### Post by nomko on 2011-07-15
Did you try Vlc? This program can be found in the repositories and it run almost everything without extra plugins!

---

### Post by manybodycpa on 2011-07-17
Hi!

I just gave vlc a try (and kmplayer), with no success. However, some more googling provided the answer. For some reason, mplayer was using the wrong
video driver (xv instead of gl). 

Running 

mplayer -vo gl file 

produces correct audio and video.

This can be automated by adding 

vo="gl"

to the config file in .mplayer.

Best,

Martin

---

