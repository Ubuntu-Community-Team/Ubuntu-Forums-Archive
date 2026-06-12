---
title: "Loading ALSA sound driver modules: (none to load)"
date: 2009-11-17
forum: General Help
---

### Post by minasmorath on 2009-11-17
Hello Ubuntu folk,

I have an interesting issue with my sound setup, and the error is in the title of this post. I have had sound for ages on my Debian testing laptop, but I got greedy and wanted to see if my HSF modem would work with the Linuxant proprietary drivers (that'll teach me to use prop drivers again), and lo and behold I have lost all sound. Funny thing is the drivers actually failed to install through dpkg, so i purged them and thought all would be fine on reboot... nope, alsa is refusing to load a driver, and quite honestly I can't figure out what to modprobe. I know my card is supported:

```
mitchell@alexandria:~$ lspci | grep -i "audio"
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

It's a very standard card, and I've never had issues in any distro until now. This is quite the bothersome issue. I absolutely must have sound on this system, I work with Audacity quite a bit for school.

Any suggestions are welcome, although I have run the gamut of the forums looking for solutions already. If all else fails could someone point me to the alsa driver loading/configuring docs? I know I have to either insmod or modprobe something, I can't seem to find what, even with google.

Thanks ahead of time,

Mitch

PS - This is a Debian testing box, which is ubuntu without the artwork and special customizations, and no I do not have that POS known as PulseAudio. Thanks again!

---

### Post by minasmorath on 2009-11-17
*bump*

I really need to get this fixed, preferably without a reinstall.

---

