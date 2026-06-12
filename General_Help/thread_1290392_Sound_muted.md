---
title: "Sound muted"
date: 2009-10-13
forum: General Help
---

### Post by vigalance on 2009-10-13
every time I boot ubuntu the sound is spontaniously muted. anybody know how to stop this from happening?

---

### Post by ibuclaw on 2009-10-13
I wrote a [blog]("http://iainbuclaw.wordpress.com/2009/09/15/howto-save-and-restore-alsa-settings-on-startupshutdown/") on this. :)

Run:
```

sudo mv /etc/rc0.d/K50alsa-utils /etc/rc0.d/S50alsa-utils
sudo mv /etc/rc6.d/K50alsa-utils /etc/rc6.d/S50alsa-utils

```
And this will add the ALSA save/restore settings to the startup/shutdown routine.

Regards
Iain

---

