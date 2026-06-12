---
title: "Kubuntu 9.10 Gstreamer Dependencies Tip"
date: 2009-11-01
forum: General Help
---

### Post by kingbilly on 2009-11-01
Hello, I wanted to share how I went about fixing a problem on Kubuntu 9.10 with Gstreamer-Based applications.


[COLOR="Blue"]Kubuntu 9.10
USB External Soundcard[/COLOR] (internal is blacklisted)

I am not sure if my USB soundcard complicated this(was the fresh install sound system unable to route to a card other than pcm/internal?  I wouldn't know because i really don't understand sound) 

With a fresh install of Kubuntu 9.10, only my KDE applications could play music and videos.  But I prefer Banshee or Listen over Amarok.  Both of my preferred applications gave me gstreamer related errors in the terminal.  After installing all the gstreamer packages I could my sound still would not work in Banshee, Listen, Vlc, etc.  I did some reading on the sound system in KDE 4.3. I became confused about phonon and started tinkering with alsa settings.  This went on for about 5 days.

Finally I read a thread that sparked an idea, some people were reporting success with rhythmbox playing music, so I installed it.  Along with rhythmbox (which I still haven't actually ran once on this new install) were some important dependencies that were installed.

Now all my video and sound problems are fixed!!  

I would never have never guessed that somewhere in this mess: ```
gnome-media gnome-media-common libcanberra-gtk-module libcanberra-gtk0
  libgnome-media0 libpulse-browse0 libpulse-mainloop-glib0 libspeexdsp1 
  media-player-info pulseaudio pulseaudio-esound-compat                 
  pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils         
  python-gconf python-gnome2 python-gnomecanvas python-pyorbit rhythmbox

```

was the missing dependency for my gstreamer/gnome based apps.  If only I knew specifically what was missing I could file a bug report.
[B]
So if anyone else has a fresh Kubuntu 9.10 and is having trouble with Listen or Banshee, try installing rhythmbox [/B](or just the above packages)

Hope someone in my situation finds this helpful.

---

