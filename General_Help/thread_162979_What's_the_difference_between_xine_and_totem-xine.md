---
title: "What's the difference between xine and totem-xine?"
date: 2006-04-20
forum: General Help
---

### Post by Mishal on 2006-04-20
I am sick of mplayer playing havoc with my sound, so I was desparate to get totem to work properly. But performance on totem was always jerky...

....till I installed totem-xine. So what the magic behind this? And why are there so many versions of xine? gxine, gnome-xine, totem-xine and even kaffeine and amarok have xine versions. I am still confused about whether xine is really a media player or an engine or both.

Will somebody shed some light on this? Thanks:)

---

### Post by aysiu on 2006-04-20
I really can't tell you any more than the descriptions... ```
user@ubuntu:~$ apt-cache search --names-only xine
amarok-xine - xine engine for the amaroK audio player
kaffeine-xine - Xine engine for kaffeine media player
libxine-dev - the xine video player library, development packages
libxine-main1 - the xine video/media player library, binary files
libxinerama-dev - X11 Xinerama extension library (development headers)
libxinerama1 - X11 Xinerama extension library
libxinerama1-dbg - X11 Xinerama extension library (debug package)
x11proto-xinerama-dev - X11 Xinerama extension wire protocol
xinetd - replacement for inetd with many enhancements
gxine - the xine video player, GTK+/Gnome user interface
gxineplugin - the xine video player, GTK+/Gnome; launcher plugin for Mozilla
libarts1-xine - aRts plugin enabling xine support
totem-xine - A simple media player for the Gnome desktop based on xine
totem-xine-firefox-plugin - Totem Firefox Plugin - xine version
xine-ui - the xine video player, user interface
libxine-extracodecs - the xine video/media player library, binary files
libxine1c2 - the xine video/media player library, transitional package
```

---

### Post by Mishal on 2006-04-20
Hmm...maybe someone else can help?

Also, can I make totem-xine play .swf files somehow?

---

### Post by croak77 on 2006-04-20
Google is your friend:)

[http://xinehq.de/](http://xinehq.de/)

No, xine doesn't play swf.

---

### Post by DoktorSeven on 2006-04-20
xine is the engine, all those different versions you see are frontends.

Mystery solved. :)

---

### Post by Mishal on 2006-04-20
Thanks but if let's say totem is nothing but a front-end, how was it running on my PC without the xine engine? And if totem, amarok etc indeed has their own engine (which can be replaced with the xine engine if so wished by the user), what are the benefits/drawbacks of having two alternative engines?

For me, totem was jerky with its playback but became smooth when I installed xine. But WHY is this so? Is totem jerky by default on everyone's computer? If not, why should one install xine in the first place?

I know I have a LOT of questions, but curiousity is in my blood. Forgive me...:)

---

### Post by Gustav on 2006-04-20
the deafault back-end for totem is gstreamer, that can be changed to xine.

Most people agree that xine is better for video (although the idea behind gstreamer is, at least in my opinion, better)

---

### Post by oberoc on 2006-04-20
[QUOTE=Mishal]Hmm...maybe someone else can help?

Also, can I make totem-xine play .swf files somehow?[/QUOTE]

totem-xine can't play swf, but a GNU can, check it out here: [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)

Don't know if it is ready for prime time yet

-Tino

---

### Post by Mishal on 2006-04-20
Thanks for the reference to gnash. Hopefully, it will become the Linux standard player to play flash files in the future. 

Meanwhile, I guess an easy alternative to play flash files is in Firefox.

---

### Post by JohnnyMarr on 2006-04-20
you should be able to play swf files in firefox if you have the flash-plugin installed

---

### Post by az on 2006-04-20
Xine uses the windows codecs for media playback.  They are proprietary, closed-source and pretty much stolen - they are not licenced for use in linux.

Gstreamer is a framework for multimedia.  It is free-libre open-source.  There are several bits currently still lacking, but it will become more useable relatively quickly.  

No, playback is not jerky for everybody.

---

