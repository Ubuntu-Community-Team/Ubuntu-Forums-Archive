---
title: "Webcam: audio and video work separately, but not together"
date: 2012-03-13
forum: General Help
---

### Post by flar on 2012-03-13
I have a Logitech c525 webcam.  It's a uvc webcam and should work out of the box.  If I use cheese or some other program to look at the video, it works fine.  If I open gnome-sound-recorder and record audio from the built in microphone, it works fine.  But if I have the video streaming and try to use the microphone (e.g. on Skype), the sound is all static.  Note this is not a Skype issue.  If I open cheese to show the video and try to record audio with gnome-sound-recorder, there is static in the recording.  

Basically, whenever the video output is being used, the sound is all scratchy and static-y.


Other info: I'm using Maveric (10.10).  I've tried the Maverick kernel (2.6.35) and the Natty kernel (2.6.38 ) .  I can't try kernel 3.x because of my video driver.

---

### Post by flar on 2012-03-22
For future reference, the problem must have had something to do with the combination of this webcam and the motherboard or onboard sound.  I tried the webcam in another computer running the same version of Ubuntu and it worked perfectly.  Ultimately, my solution was to get a different webcam, which works fine.

---

