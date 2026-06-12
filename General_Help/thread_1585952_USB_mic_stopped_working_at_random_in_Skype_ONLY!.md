---
title: "USB mic stopped working at random in Skype ONLY!"
date: 2010-10-01
forum: General Help
---

### Post by Bucky Ball on 2010-10-01
Hi all,

Here's a weird one and hoping there will be a fix. It took an age to get Skype working with Pulseaudio and a USB headset but I got there. Still can't get it to ring through the speakers but use the headset for a call, which you can with ALSA, but there you go. I sometimes wonder if Pulse as default was a step forward or back. 

Anyway, current prob. All working fine for about four months. The machine is regularly unplugged and moved no drama. I take it out one day, come home, plug in, make a test call, get no error messages about playback or input device, I can hear the test call fine, but my recorded message playback is dead air. Nothing. Silence.

Hmm. I check absolutely everything obvious then open 'Pulseaudio Volume (recording)' find the mic is working fine (I could also hear it through the headset but this told me the audio path for the mic was through Pulseaudio for sure). So I make another test call with the volume window up and there is a level while I am recording my Skype test call message, but on playback there is again silence!

I'm bamboozled for the moment. This seems to have happened at random. Used Sound Recorder to record with the mic and no problem. Working fine. Just Skype seems to be not hearing the mic at all, even though Sound Devices is set to Pulseaudio (you have no choice with Pulse).

Hoping someone might have an inkling about the strange anomaly.

ps: It is my wife's machine and I don't tweak with it at all unless she asks me to or lets me know something is misbehaving (very rare) so no, I have not recently made any changes; it was/is a totally stable uni/entertainment workhorse.

---

### Post by Bucky Ball on 2010-10-03
Any takers? Getting nowhere here.

---

### Post by Bucky Ball on 2010-10-05
Think I'll just remove Pulse Audio and install ALSA next week when I have some time again. Never could get the ring through the external speakers and the call through the headphones which is a piece of cake in ALSA (one of the desktops using ALSA has been doing so faultlessly with a USB handset for the last two years).

---

