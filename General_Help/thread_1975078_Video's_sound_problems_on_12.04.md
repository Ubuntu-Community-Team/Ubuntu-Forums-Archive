---
title: "Video's sound problems on 12.04"
date: 2012-05-06
forum: General Help
---

### Post by Sicadastra on 2012-05-06
Since I upgraded to 12.04 I've noticed some problems with my laptop. But the most glaring of all is the problems with the video playback. When I play YouTube videos they buffer properly but the sound comes out stuttering. Even when I play a movie on VLC sometimes when I have to pause-and-play the sound would disappear.

Is there anything I can do to solve this?

I'm noting though the sound problem *only* occurs with videos. When I play music on Banshee, there are no problems at all.

---

### Post by Sith Lord Kyle on 2012-05-06
Good question.  I also have problems with sound on 12.04 ... but not every time.  Sometimes starting videos on VLC will produce static or other weird sound issues.  If I start/stop it, it'll work fine after that.

Sound drive issues maybe?

---

### Post by Sicadastra on 2012-05-06
Yes, it's most likely although I have no idea where to start troubleshooting. :(

---

### Post by Sicadastra on 2012-05-06
I somehow managed to solve my problem on my own without knowing what exactly it was I did. I tinkered with the alsamixer and when I tried playing YouTube videos again they sounded fine at last.

---

### Post by ranganathan16 on 2012-05-10
I created a new profile. The sound works in new profile.

---

### Post by Sith Lord Kyle on 2012-05-22
Luckily, instead of having to create a new profile, one of the last recent updates seems to have cleared up that issue for me.

I guess something was just buggy previously.

---

### Post by jdsampayo on 2012-07-07
Hello,

I have the same problem, fullyupdated Ubuntu 64, and the sound in videos gets stuffed even if the video is fully loaded, I noticed it only pops when the video presents a lot of bass frecuencies (like movies), when the sound is more treblee (like one guy playing guitar) it doesn't happen, actually it pops for example with very bassy bass drums (modern ones), anyone else experimenting this?

P.D. the same sound doesn't gets stuffed in Windows, so it is not problem of my speakers, it started with the update of Ubuntu to 12.04

EDIT: Found a solution for my problem,
alsamixer => disable auto mute
[http://www.youtube.com/watch?v=Wrhl8iaDzFI](http://www.youtube.com/watch?v=Wrhl8iaDzFI)

---

### Post by Cube_Code on 2012-10-27
> **jdsampayo said:**
> Hello,

I have the same problem, fullyupdated Ubuntu 64, and the sound in videos gets stuffed even if the video is fully loaded, I noticed it only pops when the video presents a lot of bass frecuencies (like movies), when the sound is more treblee (like one guy playing guitar) it doesn't happen, actually it pops for example with very bassy bass drums (modern ones), anyone else experimenting this?

P.D. the same sound doesn't gets stuffed in Windows, so it is not problem of my speakers, it started with the update of Ubuntu to 12.04

EDIT: Found a solution for my problem,
alsamixer => disable auto mute
[http://www.youtube.com/watch?v=Wrhl8iaDzFI](http://www.youtube.com/watch?v=Wrhl8iaDzFI)

worked great, thanks.

---

