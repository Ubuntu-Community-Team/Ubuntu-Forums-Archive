---
title: "Thinkpad T400 sound is very soft"
date: 2009-09-22
forum: General Help
---

### Post by Ingenium on 2009-09-22
Hi. I just got a new Thinkpad T400 and did a fresh install of Ubuntu 9.04, but the sound is unacceptably low, even when it's turned up all the way. I've went into the sound settings and both PCM and Master are up all the way, yet the sound is so soft that with even the slightest bit of background noise I can't hear any conversation in a video. It's not application specific; flash video, VLC, Totem, and general system sounds all do it.

Is there some other way to increase the sound volume? My previous laptop had the same issue where max volume wasn't very loud, but it was still louder than on my Thinkpad. 

Thanks.

---

### Post by tgeer43 on 2009-09-23
There are other device sliders which may be limiting your sound oiutput. They vary by the hardware you are running and the device you are using for playback. Go back into the volume control and first make sure that the device you are controlling matches the device you have selected for playback in System->Preferences->Sound. Next select 'Preferences' and make sure that everything has a checkmark next to it. Now go back to the mixer and crank everything up.

---

### Post by Ingenium on 2009-09-23
Thanks for the suggestion. I think you meant to right click on the sound applet, select Volume Control, and then click Preferences, since there isn't anything where you said to go other than selecting the default device and testing it. I already tried this though. Everything is checked and all the sliders are at the top. Master and PCM are the only options for output devices. Others are 3 microphones and 2 switches for IEC958, but toggling those has no effect. I've tried it with all the different devices listed as well. 

I also tried installing different pulse audio tools to adjust the sound but they all have the volume all the way up as well.

---

### Post by tgeer43 on 2009-09-23
No I said it right, you just mis-read. I said to make sure that the device you have selected for playback in System->Preferences->Sound matches the device that you are controlling in the volume mixer, that's all.

So you don't have volume sliders for headphone or front? The one for front, which is not visible by default was the one that was keeping my notebook from playing at full volume.

What device are you using for playback? With only master and pcm sliders it sounds like you are using OSS which is old technology and should be avoided IMO. If so then try Pulseaudio or better yet, Alsa. This is the default device you select in System->Preferences->Sound. *Then* make sure you are adjusting the same device in the volume mixer.

tgeer

---

### Post by Ingenium on 2009-09-23
Ah. Yeah, I had it set to autodetect in the sound preferences. However, the device is set to HDA Intel (Alsa mixer). Now that I think about it, my previous laptop did have headphone and Front checkboxes and sliders...but this laptop doesn't. ALSA shows PCM, Master, the Mics, and the switches, but Pulseaudio only shows Master. 

I tried loading alsamixer and it also only shows PCM, Master, the 3 Mics, and the two switches. PCM and Master are at 100%.

---

### Post by tgeer43 on 2009-09-26
> **Ingenium said:**
> Ah. Yeah, I had it set to autodetect in the sound preferences. However, the device is set to HDA Intel (Alsa mixer). Now that I think about it, my previous laptop did have headphone and Front checkboxes and sliders...but this laptop doesn't. ALSA shows PCM, Master, the Mics, and the switches, but Pulseaudio only shows Master. 

I tried loading alsamixer and it also only shows PCM, Master, the 3 Mics, and the two switches. PCM and Master are at 100%.Sorry - I've been tied up for a couple of days.
I'm really not coming up with any concrete suggestions at the moment. Nearly every low audio issue that I've been involved with has in one way or another boiled down to the mixer settings.

Until you get things sorted out the only consolation I can offer is for playing audio files. If you install Xmms (not to be confused with Xmms2), it has a nice preamp that can add up to 20dB of audio output and should make it at least listenable.

tgeer

---

