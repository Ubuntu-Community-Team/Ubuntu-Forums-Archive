---
title: "pitivi bad sound"
date: 2011-01-24
forum: General Help
---

### Post by william_lane on 2011-01-24
Hi I'm use pitivi to edit a video of my desktop made by Xvdidcap and I added 2 mp3 tracks with it. Works good its a cool editor but I needed it to come out as mpg so the audio codec is FFmpeg Advanced audio Coding encoder[ffencaac] and the video is FFmpeg MPEG-1 video encoder [ffenc_mpeg1video] but the audio is coming out bad as it you blasted blown speakers. Anyone have Ideas for me? PS: I am using DVDStyler to put it on a dvd thats why I need that code.
Thank You anyone that responds.

---

### Post by NightwishFan on 2011-01-24
I have a lot of issues with Pitivi however it does look good for the future. Try openshot in the meantime, and perhaps someone might be able you with Pitivi if you want as well.

---

### Post by william_lane on 2011-01-24
> **NightwishFan said:**
> I have a lot of issues with Pitivi however it does look good for the future. Try openshot in the meantime, and perhaps someone might be able you with Pitivi if you want as well.

Okay, I'll give it a shot thank you for the advice.

---

### Post by dewdrop_world on 2011-01-24
"Blasted blown speakers" means *clipping* (a.k.a. distortion). That's what happens when the signal level goes out of range.

Since you added two MP3 tracks, one possibility is that both of them are already at high volume and you're mixing them together. If we say that 1.0 is the maximum amplitude that can be represented without clipping (this is the way most pro audio applications do it), you might have one track that peaks at 0.98 and another track that peaks at 0.95. Then, theoretically, if those high-amplitude waveform peaks coincide, you could have a peak of 1.93, which would be horribly clipped along with the sample values alongside it.

I don't know Pitivi well enough to say how to handle audio amplitude scaling (volume control) in it. I'm also not sure why it (presumably) sounded okay while you were editing. One possible explanation for that is that the system-level volume control could have been turned down. Most audio frameworks these days use floating point numbers for sample values. You could have one application pumping out samples outside of the +/- 1.0 range, and if the master volume control is low enough, those values will be scaled to be in range before the HW output phase and you don't hear any distortion. But, when you render the video, pitivi has no choice but to write out the values -- that are *not* subject to scaling-down by the system volume control. Then, your rendered file contains the distorted waveform.

FWIW I gave up on Pitivi after I had trouble finding the right codecs for it. I don't edit video much but I've had some success with kdenlive.

James

---

### Post by NightwishFan on 2011-01-24
That is possible but I think it is actually the output renders constantly like garbage with some codecs. I have no trouble with video but audio always is iffy, which is why I stopped using it for now. I tested the bleeding edge one and it worked great though, so Natty should be fine. :)

---

