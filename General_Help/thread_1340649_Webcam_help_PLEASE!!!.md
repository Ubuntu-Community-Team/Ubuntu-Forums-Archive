---
title: "Webcam help PLEASE?!?!?!"
date: 2009-11-28
forum: General Help
---

### Post by dxtac1 on 2009-11-28
I took the plunge today and rid myself of MS on my home pc. Everything has been going smoothly during this transition with one exception so far. I have a Logitech Quickcam Communicate MP Plus webcam and I can not get the mic to work on Skype. It may not sound like a big deal but since I have NO IDEA what I'm doing yet with Ubuntu and Linux in general it is a very big deal. I use this cam to see my wife and kids while I'm on the road for work. Any and all help would be greatly appreciated!! I believe it may be a driver issue as I've read that some cams work out of the box and others do not but I'm clueless.
 
Thanks in advance,
 
Derek
 
Forgot to mention I am running 9.10

---

### Post by Mazin on 2009-11-28
Hi there,

I assume the video works fine on your webcam.  And Karmic is 9.10 right?  (the versions are starting to blur on me.)  And you're using the latest version of Skype right? (I think I'm using 2.1).

Usually USB audio devices like your built-in mic are pretty generic.  Right-click the volume icon in your tray and choose "Sound preferences".  Under the hardware tab, does it list your microphone device?  There will probably be at least two entries, one for your computer's built-in sound and one for your webcam's mic.  Choose the webcam and I'm going to guess that the Profile is "Analog Mono input".

If that worked, then on the next tab Input, under "Choose a device for sound input", pick your webcam instead of your computer's built-in audio.  Try yelling at your webcam to see if the little input level bar goes up (make sure it's not muted!).

OK, if those steps went well, then in Skype's Options, under "Sound Devices", your only option for Microphone should be "PulseAudio server (local)", which will use the settings you just set.  Then try calling echo123.

---

### Post by dxtac1 on 2009-11-28
Mazin - you are A-Mazin-G. It works perfectly now!!! 
 
Thanks a TON!!!!!!!
 
Derek

---

