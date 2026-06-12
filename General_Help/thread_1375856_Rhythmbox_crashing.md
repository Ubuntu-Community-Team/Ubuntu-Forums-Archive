---
title: "Rhythmbox crashing"
date: 2010-01-08
forum: General Help
---

### Post by saturnblackhole on 2010-01-08
i just updated to rhythmbox 0.12.6 and tried to use the new context plug-in and have noticed that it crashes rhytmbox when a new song is loading. is anyone else having this issue? is there a way i can get the logs for rhythmbox so i can file a bug? 

o yeah im using ubuntu 9.10

---

### Post by saturnblackhole on 2010-01-08
ok i found and use the log viewer application this is the log from rhythmbox when it crashes. 

> Jan  8 13:12:41 my-laptop pulseaudio[2139]: ratelimit.c: 113 events suppressed

Jan  8 13:13:29 my-laptop kernel: [42350.102351] rhythmbox[15277]: segfault at 14 ip b5582d9e sp bf98c510 error 6 in libwebkit-1.0.so.2.11.2[b4fa0000+bc8000]



i have libwebkit installed so i dont know what the problem is any suggestions?

---

### Post by saturnblackhole on 2010-01-09
found the launch pad bug forum and filed it there maybe someone there knows what to do.

---

### Post by brookie on 2010-01-23
Hello,
I'm having the same problem with Rhythmbox 0.12.6 with the context plugin enabled, or hidden with the "I" button. 
I can reproduce it a lot. 

To test: 
1. start rb
2. enable context panel plugin
3. play a song in your library
4. click towards the end of the song
5. song switches ok sometimes and crashes rb sometimes

6. when rb crashes, re-start, disable context panel, no more crashes

Error: 
Jan 23 12:58:55 kernel: [ 4170.298465] rhythmbox[3494]: segfault at 0 ip b5d39e87 sp ac83beb0 error 4 in libwebkit-1.0.so.2.11.2[b5757000+bc8000]

I found [this]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/504876") bug (#50487) at launchpad but it is closed. Could you post the bug report you filed? 

My wife loves the lyrics in the context panel plugin. Too bad this is crashing rb. Dang! 

brook

---

### Post by saturnblackhole on 2010-01-30
the bug that you linked in your post is the bug that i filled. i pretty much given up on it, i just plan on waiting for the next release and hopefully it will work if it doesn't im just going to switch to rhythmbox.

---

