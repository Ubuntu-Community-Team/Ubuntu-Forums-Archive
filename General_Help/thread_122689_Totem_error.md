---
title: "Totem error"
date: 2006-01-28
forum: General Help
---

### Post by Hwoarang on 2006-01-28
Hi everyone, I am a newbie . While I am trying to listen Radio through Internet I am receiving a Totem error ...

something like totem cannot open fd://0 

I ve installed w32codecs and realplayer but still doesnt work. Thanks a lot

---

### Post by Neo Ex on 2006-01-28
I don't know if this can help, but, If you want to use Totem, try install totem-xine-firefox-plugin; it must be better then the normal Totem.
If you don't want to use Totem, try installing mozilla-mplayer (I hadn't never be able to make Totem works; instead, the MPlayer plugin always worked for me).
Or, if you use Konqueror as browser, try using Kaffeine or KMPlayer.

---

### Post by Hwoarang on 2006-01-28
[QUOTE=Neo Ex]I don't know if this can help, but, If you want to use Totem, try install totem-xine-firefox-plugin; it must be better then the normal Totem.
If you don't want to use Totem, try installing mozilla-mplayer (I hadn't never be able to make Totem works; instead, the MPlayer plugin always worked for me).
Or, if you use Konqueror as browser, try using Kaffeine or KMPlayer.[/QUOTE]

tha man. I am a newbie @ Ubuntu and @Linux in general. I appreciate your help

---

### Post by dimension user on 2006-01-29
> something like totem cannot open fd://0

I ve installed w32codecs and realplayer but still doesnt work. 

Hi.  I'm having a similar same problem.  I go to cnn.com and try to watch the streaming videos, but I get that error message.  The weird thing is that I've already installed the mozilla-mplayer plugin.  I thought maybe the problem was that I installed the plugin before the w32 codecs while firefox was running.  I figured that might be the reason so I used synaptic to do a complete uninstall and install of mozilla-mplayer.  I'm still getting the same totem error.   "about:config" in firefox shows both mplayer and totem plugins are installed and enabled for windows media, realplayer, and quicktime files.  Shouldn't I not be getting totem errors if the mplayer plugin is working correctly?  Should I disable the totem plugin somehow?

---

### Post by newlinux on 2006-08-03
> **dimension user said:**
> Hi.  I'm having a similar same problem.  I go to cnn.com and try to watch the streaming videos, but I get that error message.  The weird thing is that I've already installed the mozilla-mplayer plugin.  I thought maybe the problem was that I installed the plugin before the w32 codecs while firefox was running.  I figured that might be the reason so I used synaptic to do a complete uninstall and install of mozilla-mplayer.  I'm still getting the same totem error.   "about:config" in firefox shows both mplayer and totem plugins are installed and enabled for windows media, realplayer, and quicktime files.  Shouldn't I not be getting totem errors if the mplayer plugin is working correctly?  Should I disable the totem plugin somehow?

I had the same problem and uninstalling the totem plugin worked for me. uninstall totem-gstreamer-firefox plugin or totem-xine-firefox-plugin, depending on which one you have installed. I did this and now mplayer takes over and does fine.

---

