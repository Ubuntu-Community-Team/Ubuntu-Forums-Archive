---
title: "No sound in 9.04 after reboot"
date: 2009-07-02
forum: General Help
---

### Post by woolgatherer on 2009-07-02
Hi everyone, this is my first post to ubuntu forums....
I'm using ubuntu 9.04 64 bit, it all happened yesterday that ubuntu was taking time to shutdown, so I shut it down manually by holding the cpu button while ubuntu had already logged out. Today morning, I start the system to find out that not even the start-up sound turn up. I've also tested the sound in system-preferences->sound but I didn't hear anything. Then, I installed pusleaudio to check through the volume meter. It shows signal levels while playing any media but I get no sound. Help Please!!

---

### Post by internalkernel on 2009-07-02
I've had this happen a couple times to me... Open the volume control through the volume applet on the desk bar, I don't know where else to access this. Maybe through an Alsa mixer. When you right click on the volume control, select Open Volume Control. At the top there is a drop down menu, labeled Device: 

It's probably set to the PulseAudio mixer. In my case, I had to select the HDA Intel (Alsa mixer) - which is the Alsa mixer for my hardware device. Depending on your setup, this may be different. 

It was a simple fix... The PCM volume control was - for some unknown reason - muted. This has happened to me several times now, and I have absolutely no freaking idea why...

Hope this helps...

---

### Post by woolgatherer on 2009-07-02
Thanks a lot mate! It worked, PCM control was muted :p. Ne'er thought I'd get a reply so soon.

---

