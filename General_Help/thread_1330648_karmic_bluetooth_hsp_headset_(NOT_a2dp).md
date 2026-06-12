---
title: "karmic bluetooth hsp headset (NOT a2dp)"
date: 2009-11-18
forum: General Help
---

### Post by awry on 2009-11-18
Hi,

I just upgraded to karmic, and I want to be able to use my jabra bluetooth headset, NOT to listen to music (a2dp profile) but to make voip calls (hsp or hfp).

I've searched the forums and wiki, but all I can find is outdated info (instructing use of deprecated snd-bt-sco module) or info about a2dp (using pulseaudio).

That's another thing. I refuse to use pulse.

Anybody? How do I set up a headset using hsp or hfp bluetooth profile under karmic?

---

### Post by EyesOnFire on 2009-11-22
When I installed Karmic and connected my Motorola HT820 Stereo headset, I was elated and blown away by the fact that it paired so easily (like an Apple). However, it was only set to output Mono (HSP). 

Simply go to SYSTEM > PREFERENCES > SOUND > HARDWARE Tab and select the bluetooth audio device (In my case Motorola HT820).

On the bottom, there is a PROFILE dropdown which should allow you to switch between High Fidelity Playback (A2DP) and Telephony Duplex (HSP/HFP). 

If you're not using pulse, you should stop fighting it. It's here to stay and it's making life a little easier and Ubuntu more flexible (In my opinion). I had problems with it in 9.04, but I think I've made my peace with it, now that stuff actually works.

---

