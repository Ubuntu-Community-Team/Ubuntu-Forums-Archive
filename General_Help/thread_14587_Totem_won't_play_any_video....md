---
title: "Totem won't play any video..."
date: 2005-02-08
forum: General Help
---

### Post by sharkzf6 on 2005-02-08
Totem just won't play any video files. I usually get an error message like: “There were no decoders found to handle the stream... you might need to install the corresponding plugins.” The problem is, according to Synaptic, all the plugins for gstreamer are installed! Can someone please tell me how to get this program to do what it's suppose to do? Thanks.

---

### Post by ubuntu UsER on 2005-02-08
[QUOTE=sharkzf6]Totem just won't play any video files. I usually get an error message like: “There were no decoders found to handle the stream... you might need to install the corresponding plugins.” The problem is, according to Synaptic, all the plugins for gstreamer are installed! Can someone please tell me how to get this program to do what it's suppose to do? Thanks.[/QUOTE]

Install w32codecs from 3rd party repository (go to [www.ubuntuguide.org](www.ubuntuguide.org) there is an example how to do it).

---

### Post by sharkzf6 on 2005-02-08
[QUOTE=ubuntu UsER]Install w32codecs from 3rd party repository (go to [www.ubuntuguide.org](www.ubuntuguide.org) there is an example how to do it).[/QUOTE]
Thanks, I'll give it a try....

---

### Post by landotter on 2005-02-08
[QUOTE=ubuntu UsER]Install w32codecs from 3rd party repository (go to [www.ubuntuguide.org](www.ubuntuguide.org) there is an example how to do it).[/QUOTE]

Do that and install totem-xine (a better back end) with synaptic and you're set.

---

### Post by macewan on 2005-02-08
if you install the xine flavor it will tell you that it has to remove ubuntu desktop - don't worry - it will not hurt anything

---

### Post by sharkzf6 on 2005-02-08
[QUOTE=landotter]Do that and install totem-xine (a better back end) with synaptic and you're set.[/QUOTE]
OK, great, hope this works...it's the last thing I need to get goin  :D   I think ...

---

### Post by Jad on 2005-02-08
gzine and xine it self + mplayer works fine! why we need totem and why its the default player?

---

### Post by landotter on 2005-02-09
[QUOTE=Jad]gzine and xine it self + mplayer works fine! why we need totem and why its the default player?[/QUOTE]
 
 Totem is just a gui for Xine and it fits with the Gnome HIG much better. In essence, it is Xine, but with lipstick.

---

