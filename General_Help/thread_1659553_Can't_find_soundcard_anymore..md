---
title: "Can't find soundcard anymore."
date: 2011-01-04
forum: General Help
---

### Post by gdpt on 2011-01-04
Hi there guys,

my sound was working perfectly on my Gateway NV 52 running Ubuntu 11.04 64 bit. I had the alsa driver linuxant 1.0.23 running. 

The problem was, every time I installed something in the software center, I had this message saying it was unable to remove or install package because it was unable to mount alsa-driver-linuxant (or something similar as far as I remember). This was just an error message because the software did install.

Now I've had problems with my sound before. But nothing that worked for me before did it now. I've been looking around on this forums, but again, nothing worked so far.

I then proceeded to uninstall all ALSA drivers and Pulse audio, also in Computer Janitor. I reinstalled ALSA, but still, no hardware device is detected.

What am I doing wrong?

Thanks for your time :)

---

### Post by mastablasta on 2011-01-04
try with:
 
sudo alsaconf
 
 
to configure the card.
 
and also if you upgraded/reinstalled alsa that was working before make sure you lock packages.
 
also if you are really using 11.04 which is testing alpha undeveloped whatever version you should post in different part of forums.

---

### Post by gdpt on 2011-01-04
Thanks for the reply. 
Sorry for posting in the wrong section. I'll keep it in mind for the future.

The command you mentioned, doesn't do anything, though :(
(Command not found)

---

### Post by mastablasta on 2011-01-04
hmm what alsa is in 11.04? this command works with 1.0.23. it's probably still the same version. are you sure you have the whole alsa installed?

should be drivers, libraries and utils i huess. 

 i dont' know much about this but i fiddled quite a lot with alsa to get my card working. used this tutorial to upgrade it:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

you could follow it to install it as well. just leave out the removal part in the beginning. :-)

but there is also a script.

anyway final command in tutorial configures the sound card (you select it and it configures it9. kind of like sound card setup in those old DOS games :-)

---

### Post by davidgutu on 2011-01-17
Just run the following command
```

sudo apt-get install alsa-firmware-loaders 
```

worked for me

---

