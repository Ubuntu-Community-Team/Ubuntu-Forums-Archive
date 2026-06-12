---
title: "Ubuntu 9.10 32 won't play this radio station"
date: 2010-03-31
forum: General Help
---

### Post by AgentZ86 on 2010-03-31
Hi

The radio station is located here

[[COLOR="Blue"]Click Here:[/COLOR]]("http://www.wmal.com/article.asp?id=632848")

Then click to listen

But when it comes up there it does not play for some reason.

It was working fine with ubuntu 8.10 no problem at all.

What did I do wrong here ?

Please advise
Thanks
:popcorn:

---

### Post by conradin on 2010-03-31
Do you have the Gstreamer ffmpeg plugin it requests? I'm thinking its a plugin problem. Also, the volume (on site) was initially set to 0 try clicking on the little speaker icon, and turning it up.

---

### Post by conradin on 2010-03-31
Am I now listening to Glen Beck?? (Keels over and vomits on floor)

---

### Post by ron999 on 2010-03-31
@AgentZ86
It's playing OK for me too.
If you're using Firefox look in Tools > Add-ons > Plugins
Check that you have got a suitable plugin installed.
The one that I'm using is **gecko-mediaplayer** from the Ubuntu repository.

That radio stream is **[http://citadelcc-WMAL-AM.wm.llnwd.net/citadelcc_WMAL_AM](http://citadelcc-WMAL-AM.wm.llnwd.net/citadelcc_WMAL_AM)**
So it can be added to Rhythmbox or played with mplayer or VLC.
Like this:-
```
mplayer http://citadelcc-WMAL-AM.wm.llnwd.net/citadelcc_WMAL_AM
```
```
vlc http://citadelcc-WMAL-AM.wm.llnwd.net/citadelcc_WMAL_AM
```

EDIT Pass me the sickbag conradin.;)

---

### Post by AgentZ86 on 2010-03-31
Hi 

Thanks for the replies

> Gstreamer ffmpeg plugin
Yep this is installed

> @AgentZ86
It's playing OK for me too.
If you're using Firefox look in Tools > Add-ons > Plugins
Check that you have got a suitable plugin installed.
The one that I'm using is gecko-mediaplayer from the Ubuntu repository.
No this is not installed I'll play with this next thanks

---

### Post by AgentZ86 on 2010-03-31
I installed the GnomePlayer and gecko-media and fooled with the plugin setting and but won't play it

Also even when the gecko-media is installed it does not appear in the firefox tools/addon/plugin

But I do have mplayer plugin installed which is appearantly now gecko so perhaps I will uninstall the mplayer one and reinstall the gecko and try that

I'll post back thanks

---

### Post by AgentZ86 on 2010-03-31
Thanks all

I got it working

I did play with installing the gecko but it never did work for playing this station

I re-installed gstreamer plugin for mms,wavepack,quicktime,musepack

And it works

Appearantly when I uninstalled the gecko-media it uninstalled the gstreamer for and GnomePlayer for some reason anyhow after re-installing the gstreamer it plays 

Thanks for the help.

---

### Post by AgentZ86 on 2010-04-21
I had another question, but I found it, and don't know how to delete my response, so anyhow disregard this last post LOL

---

### Post by AgentZ86 on 2010-06-16
Darn thing doesn't work again ?

I think I have the URL correct, but it appears to be some sort of flash thing now ?

Anyway to make it work in rhythmbox ? 

Please advise
Thanks

---

### Post by dino99 on 2010-06-16
install radio tray, its fine

[http://radiotray.sourceforge.net/](http://radiotray.sourceforge.net/)

---

