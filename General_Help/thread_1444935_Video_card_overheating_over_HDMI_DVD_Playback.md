---
title: "Video card overheating over HDMI DVD Playback"
date: 2010-04-01
forum: General Help
---

### Post by Ancanus on 2010-04-01
So I finished watching a movie on my TV, and I took the dvd out of my laptop only to find it was scorching hot. Then I checked the video card temperature: 135 degrees C! What!

Is there a way I can set the computer to slow down, or at least halt when it reaches a certain temperature? I really don't want to blow it out.

Player: Totem
Card: NVIDIA
Driver: 195.36.15
Thru: HDMI

Thanks

---

### Post by conradin on 2010-04-02
What you're essentially asking for is to reduce performance when you system starts to heat up. Yes, there are ways to do that, but I would recommend investigating your current cooling system, because its apparently ineffective. How old is this laptop? Dust that collects in the heat-sink and fan can make crazy heating issues arise from normal use. 

The answer to your question is to use CPU scaling which may or may not be supported by your hardware to various extents. For example my CPU only supports 2 cpu frequencies. 
[http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/](http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/)

other options could be to renice values of programs using a lot of CPU time.

---

### Post by Ancanus on 2010-04-02
True! I've had issues with dust accumulation before. I ordered a air duster a bit ago so I'm going to try it and see if the problem persists. I'll also look into GPU scaling.

---

