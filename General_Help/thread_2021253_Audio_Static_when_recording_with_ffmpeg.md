---
title: "Audio Static when recording with ffmpeg"
date: 2012-07-08
forum: General Help
---

### Post by nankura on 2012-07-08
well i finally got my ffmpeg issue sorted, now whenever recording with ffmpeg i recieve major static on voice recording. and i cant figure out why, ive tried playing with sound levels, checking codecs, using -i pulse and plughw 

cant figure out why im getting static. im using a decent plantronics headset with audio jack plugs, and it works great on mumble, vent, skype. no issues

---

### Post by FakeOutdoorsman on 2012-07-09
Please show your ffmpeg command and there complete console output.

---

### Post by nankura on 2012-07-10
ive tried the program for recording called "kazam" so i dont think the output will make any difference. it seems to be an issue with my sound drivers and audio jack. i have heard of older mics having issues with the new sound drivers

Heres what ive noticed

- The static only happens with this headset, i tried my broken headset ( its tapped up, literally ) in which the mic still works. and its USB, and it works like an absolute charm - no static at all, then i switched back to my main headset ( using the old audio jacks ), and i recieved epic static

- I cant believe im going to say this. but, the mic works absolutely fine  ( the audio jack one ) on windows. no static at all and no issues

So i have narrowed it down to which ever audio driver im using having issues with a headset that uses the old audio jacks to run

The problem is, figuring out exactly what driver is causing the issue, whether its PulseAudio or Alsa. and figuring how to actually test it, and find out

But i definatly think its something to do with the sound drivers and my audio jack

---

