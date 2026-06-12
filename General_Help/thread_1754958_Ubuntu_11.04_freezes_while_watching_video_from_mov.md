---
title: "Ubuntu 11.04 freezes while watching video from movie player or flash videos"
date: 2011-05-10
forum: General Help
---

### Post by n0_m0r3_pa1n on 2011-05-10
Hi!
I'm new to Ubuntu but I installed Ubuntu 11.04 with no problems. I activated the recommended drivers for my laptop. My laptop is: Acer Aspire 7540G with ATI Mobility Radeon HD 4570 video card and AMD Athlon II X2 processor. So the problems comes very very often. I watch videos on fullscreen or I leave them playing in youtube. While playin a video the laptop just freezes. Everything stops working. I think this problems comes up may be every 30-40 minutes of watching a movie. I'm not a fan of holding the shut down button for 10 seconds every 40 minutes so I'll be very grateful if someone helps. I've removed Syn to Vblank from the CompizConfig because otherwise Ubuntu runs really slow on my computer and the videos are playing very slow and with very bad quality. When i removed it everything began to run faster but now I've this problem with the freezing... Any ideas ? :confused:

---

### Post by harpreetsingh on 2011-05-11
I am facing a similar problem.
While playing videos from browser,
after 10 -15 min, the system goes in power saving mode because of inactivity and the screen goes off. If i move my mouse now, the screen lights up but with the video frozen. the sound keeps playing though.
No keys respond and i have to restart it get it back.

---

### Post by n0_m0r3_pa1n on 2011-05-12
Hi!
Well I've installed the drivers for my video card and I'll see if the problem continues. Why don't you try the same thing too ? What is your video card ? :)))) I have this problem even when I'm opening multiple tabs in Google Chrome.. then the screen freezes and I have to reboot my laptop manually...

---

### Post by alejandrosergio on 2011-05-13
The same for me. My ATI card is an R5450, but Ubuntu freezes even without playing flash... I was thinking in downgrading to ... to... (noooooooooooo!)

---

### Post by darb101 on 2011-05-31
Hello,

Same problem here, dell studio 1537 with ATI HD Radeon 3400. Happens randomly when going full screen on videos, e.g. youtube, vimeo etc. Screen freezes, audio sometimes loops, the keyboard doesn't work and I have to manually reboot. Tried adjusting flash settings by disabling hardware acceleration, installed flash aid and still no luck. Any help appreciated

Cheers

---

### Post by alejandrosergio on 2011-06-13
Well, I got it; it is the kernel. Downgrading to 2.6.32 it is fine again. I could see three entire full screen flash movies without freezing. Hope someone can get a useful conclusion here.

---

### Post by bossbruin on 2011-10-19
2.6.32.32 is working for me.  any later kernel is freezing not only for video but browsing and editing.

---

