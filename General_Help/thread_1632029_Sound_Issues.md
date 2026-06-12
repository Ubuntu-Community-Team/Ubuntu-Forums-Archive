---
title: "Sound Issues"
date: 2010-11-27
forum: General Help
---

### Post by ajtwin on 2010-11-27
Alright guys, I've been having some issues with my sound for a few weeks. Every time I reboot, my sound is muted. I have to open up alsamixer every time and unmute it manually. It is not the "master volume" that is muted but instead the "speaker" volume is the one that is muted. This started when i started up my computer and the ubuntu log-in sound started playing extremely loud. I quickly tried to turn down the volume while it was still booting and ever since then, i have been having this issue. Also, the volume control on my laptop no longer works, even after i adjust the volume with alsamixer. It still shows on the screen that the volume is being adjusted, but it does nothing. I hoped i explained this well enough for someone to be able to help me with this issue. Also, sorry if this issue has been posted before.

P.S. - I'm using Ubuntu 10.10 64bit desktop edition

Thanks, 
ajtwin

---

### Post by dino99 on 2010-11-27
try:

sudo dpkg-reconfigure alsa-base
sudo dpkg-reconfigure pulseaudio
sudo dpkg-reconfigure alsa-utils


if that dont work, using synaptic: remove/purge then reinstall pulseaudio

---

### Post by ajtwin on 2010-11-27
Thanks for the speedy reply dino99, unfortunately neither of the two solutions worked. Perhaps I am doing something wrong? When you say purge, does that mean just click the option "completely remove" ? While I know what purge means, I'm not exactly sure how to go about doing it in synaptic.

---

