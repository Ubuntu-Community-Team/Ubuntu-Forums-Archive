---
title: "Sound settings in Karmic Remix"
date: 2010-03-23
forum: General Help
---

### Post by logico on 2010-03-23
I have Ubuntu Netbook Remix (9.10) on my Asus 1005HA.  (I installed it inside Windows with Wubi.)

I like to keep my computer in mute most of the time.  However,  the sound settings default to about 80% volume when the computer resumes from suspend mode.  Is there way to get it to remember my settings?

Thanks.

---

### Post by logico on 2010-03-24
Bumping because I have new information and no one has responded.  I tried using the alsamixer command and saving with alsactl store, with no luck.  I can save settings temporarily (I tested this with alsactl restore), but once I suspend/resume the stored settings themselves are reset.

When I try alsactl init I get "Unknown hardware."  More specifically:

```
Unknown hardware: "HDA-Intel" "Realtek ALC269" "HDA:10ec0269,104383ce,00100004" "0x1043" "0x83ce"
Hardware is initialized using a guess method
/usr/share/alsa/init/default:51: control element not found
/usr/share/alsa/init/default:52: missing closing brace for format
/usr/share/alsa/init/default:52: error parsing CTL attribute
/usr/share/alsa/init/default:52: invalid rule
```Sound works fine otherwise...  All I want is for my laptop to start up in mute when I turn it on or resume from suspend.  Is there no way for me to do this?

---

