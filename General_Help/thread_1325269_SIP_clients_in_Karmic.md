---
title: "SIP clients in Karmic?"
date: 2009-11-13
forum: General Help
---

### Post by landtuna on 2009-11-13
Are there any pulseaudio-compatible SIP clients for Karmic? Ekiga and Gizmo5 don't support pulseaudio, and I don't see any SIP support in Empthy.

I'm running 9.10 x86_64.

---

### Post by 6205 on 2009-11-13
Empathy is replacement for Ekiga and Pidgin. And you can also use Skype.

---

### Post by aslam on 2009-11-23
Try Twinkle and let me know if its working in karmic , Its working very well in jaunty

---

### Post by landtuna on 2009-11-23
It seems to work fine, even though it doesn't use PulseAudio. I guess the ALSA wrapper makes it work. Thanks!

---

### Post by kaapstorm on 2009-11-26
> **6205 said:**
> Empathy is replacement for Ekiga and Pidgin. And you can also use Skype.

I found that the required SIP library for Empathy was not installed by default on my clean install of Karmic. You can install it like so:

```
sudo apt-get install telepathy-sofiasip
```

Then log out and log in again in order to add your SIP account to Empathy.

---

### Post by santhust on 2009-11-28
Thanks Kappstorm!

---

