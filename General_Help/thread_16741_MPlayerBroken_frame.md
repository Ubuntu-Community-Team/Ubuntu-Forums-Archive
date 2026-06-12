---
title: "MPlayer:Broken frame"
date: 2005-02-23
forum: General Help
---

### Post by csindone on 2005-02-23
I am trying to play bin/cue movies in MPlayer, the movies play fine in XP. The HDD the file is on has DMA enabled. When I play the movie it start's just fine then it stops and see:

Broken frame at 0x9D249
A:  23.8 V:  24.7 A-V: -0.903 ct:  0.007 600/600  5%  0%  0.5% 0 0


If I scroll up I see:
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts. 

How would I add the line? And will that solve the problem?

---

