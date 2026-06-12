---
title: "Help Pulseaudio + ALSA"
date: 2011-11-26
forum: General Help
---

### Post by ruzlebiff on 2011-11-26
Hello.

I'm having problems with the shairport-plugin in XBMC (running Ubuntu 10.10)
The script starts, and shaiport is visible on my iPhone.
The problem comes when i try to play a song.
(BTW: AirPlay-plugin is working great for video+pictures)

Starting plugin:

> root@xbmc:/home/xbmc/albertz-shairport# perl shairport.pl
Established under name 'B5DA9C11F9D3@ShairPort 5197 on xbmc'Playing a song: 

> ERROR: Failed to load plugin /usr/lib/ao/plugins-4/libesd.so => dlopen() failed
ALSA lib pcm_dmix.c:1018:sad:snd_pcm_dmix_open) unable to open slave
ao_alsa ERROR: Unable to open ALSA device 'default' for playback => Device or resource busy 			 		

Can somebody please help me with this?
Just let me know if you need more info.

Best Regards,
RuZleBiFf

---

### Post by ruzlebiff on 2011-11-26
.

---

### Post by scarleo on 2011-11-26
If Im not completely wrong I believe this was a feature added very recently to the unstable XBMC. If it is so then it might be just unstable, might being worked on. I think you will anyway get better help with XBMC over at XBMC forums: [http://forum.xbmc.org/](http://forum.xbmc.org/)

---

### Post by ruzlebiff on 2011-11-27
The problem isn't the plugin, but ALSA.
The plugin tries to connect to alsa, but alsa answers "XBMC is already using me, so go away"

---

