---
title: "Sound up/down function keys change wrong sound output mode"
date: 2012-05-12
forum: General Help
---

### Post by kpuz on 2012-05-12
Hi,

After installing xubuntu 12.04 I found that the Fn left/right keys that are used to change volume were actually changing something.  On xubuntu 11.10 they did nothing.  

However they seem to be effecting the HDMI output.  When I have the Volume-Control -> Output Devices tab visible and use these keys, the sound level on the HDMI output changes.  I would like to know how I can switch this so that the volume of the Built-in analog output changes instead.  

Thanks for any help

---

### Post by kpuz on 2012-05-18
After disabling HDMI output device in PulseAudio Volume Control, I was able to get the Fn keys to change laptop speaker audio.  But enabling HDMI output device always sets it as the device that gets controlled by the Fn keys.  I am keeping the HDMI disabled until I am able to figure out how to make the analog audio the default device.

---

