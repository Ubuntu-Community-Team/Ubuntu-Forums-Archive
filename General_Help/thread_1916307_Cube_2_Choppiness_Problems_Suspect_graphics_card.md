---
title: "Cube 2 Choppiness Problems Suspect graphics card?"
date: 2012-01-27
forum: General Help
---

### Post by neanderslob on 2012-01-27
Hi All,

I've just built myself a new computer 8 gigs ram, quad core processor but for some reason, my favorite fps, Red Eclipse, is REALLY slow.  I DID get a bargain on my graphics card, which uses an Nvidia GeForce FX 5200 (128 MB memory) and so I'm wondering if that's the problem.  I don't have any graphics cards on hand to swap out and so I need some advice on diagnosing the issue.  Yes the nvidia-glx-173 driver is installed and I did try it with an older version too.

A few leading questions I have are:

1) Might I be leaving out some basic configuration that I need to do?

2)Is there a way to test the graphics card's performance/integrity? 

Thanks in advance!

---

### Post by neanderslob on 2012-01-30
Bump?

---

### Post by mastablasta on 2012-01-30
glxgears command should tell you how well the card is running under pressure.
 
why did you go with an outdated card on a modern mashcine? :-) oh well i think it should still be able to run cube2. maybe the issue is in drivers or some bug within them. have you tried with opensoruce drivers?

---

### Post by neanderslob on 2012-01-30
Hey DOOD, thanks for the tip.  

I ran glxgears (cool little program btw) and ended up finding that when I'd take it full screen it would act.... well, pretty much like Cube 2 did.  

This is what happened when I gradually expanded the window and then went full screen:

2669 frames in 5.1 seconds
1015 frames in 5.0 seconds
253 frames in 5.0 seconds
312 frames in 5.0 seconds
259 frames in 5.0 seconds
299 frames in 5.0 seconds
153 frames in 5.0 seconds
109 frames in 5.1 seconds
17 frames in 5.2 seconds
19 frames in 5.1 seconds
19 frames in 5.1 seconds

What would that indicate to you?

Also, you mentioned open drivers.  I thought Nvidia only ran off the proprietary drivers; am I mistaken?

The reason I skimped on the graphics card is I'm simply not much of a gamer (I got hooked on Red Eclipse because Red Eclipse is free and free's awesome).  I put together the system because I use the computer for work which involves a lot of computation (thankfully, I've been very happy with how it's been handling that).  :D

Thanks again, much appreciated.

---

