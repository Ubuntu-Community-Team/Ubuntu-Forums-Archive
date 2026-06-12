---
title: "No Sound after Alsa Upgrade on Ubuntu 9.04 Januty"
date: 2009-12-27
forum: General Help
---

### Post by mac666 on 2009-12-27
Hey
I have sound over NVIDIA Hdmi from my Mobo.
It worked for some programs with the preinstalled version of Alsa on Jaunty, but not for all ( I couldnt get the Nvidia HDMI as default PCM).

So i upgraded ALSA with the popluar Alsa upgrade script from this forum.

After that i didnt get any sound at all, everything looked great on the screen but no sound is ever outputted. 
I could select the soundcard in alsaconf and in System > Pref > Sound, exaktly like i had it before but still no sound...

Then i tried to remove all with alsa from synaptic and run a restore on my alsa, but that didnt help.
Now i have No soundcards to choose from in System > Pref > Sound...

Anyone? :|

---

### Post by christophski on 2009-12-27
Have you tried upgrading to 9.10? There is an updated version of pulseaudio I believe, that might solve it.

---

