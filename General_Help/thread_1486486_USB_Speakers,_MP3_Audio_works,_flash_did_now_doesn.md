---
title: "USB Speakers, MP3 Audio works, flash did now doesn't"
date: 2010-05-17
forum: General Help
---

### Post by Matt-P on 2010-05-17
I am currently running Ubuntu 9.04 and have a JVC stereo system that I connect to my computer via a usb cord. For a long time now it has worked flawlessly and even now I can still play audio and video files off of my hard drive with no problem. 

The only issue I have now is with any flash video (liveleak, youtube etc) will now play fine but there will be no audio. For the longest times these videos would play with no problem. Now I checked in Volume Control and it would show two streams one being nVidia nForce2 which when selected would give no audio. The other would be a USB option which, when selected, would work just fine. 

However now the option to select that USB setting is gone, I think I may have hit terminate stream by accident. I'm not sure how to retrieve that stream or even if that would be the issue as to why flash audio suddenly stopped working.

Any help is gladly appreciated, thanks.

---

### Post by Cotopaxi on 2010-06-22
Actually I am having the same problem.

I am trying to connect a set of USB speakers.

In > System Settings > Multimedia, the USB audio output is recognized, I select "prefer this device" and make a sound test, everything fine.

But I have absolutely no sound output, except system sound!

Thanks for your help.:popcorn:

---

### Post by Cotopaxi on 2010-08-06
Sorry guys, can anyone help on this one?

Thanks!:popcorn:

---

### Post by Cotopaxi on 2011-01-06
Ok, I managed to solve it:

I downloaded and installed “PulseAudio” (it is in the repositories) and I also installed 
“PulseAudio Volume Control” (“pavucontrol” in the repositories).

In PulseAudio Volume Control, as soon as you open up an application, on the first tab called “Playback” a selection box is clickable and on this selection box you can choose your USB sound device.

Afterwards you select the tab “Output Devices” and, on your USB sound device you select a checkbox: “Select as fallback” and you should be done.

I remember, I de-installed PulseAudio, because it did not work with Skype, but with this PulseAudio Volume Control you can select the Input Device and the Output Device once Skype started up. 

Right now, this PulseAudio Volume Control is doing a great job! :D

---

