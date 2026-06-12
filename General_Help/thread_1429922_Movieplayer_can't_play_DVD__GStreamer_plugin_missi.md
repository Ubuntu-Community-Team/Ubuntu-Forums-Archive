---
title: "Movieplayer can't play DVD : GStreamer plugin missing"
date: 2010-03-14
forum: General Help
---

### Post by Pott on 2010-03-14
So I installed a bunch of gstreamer packages but none made it work. Funny... it was working fine before I tried to get XFCE and had to delete it all using Psychocats' tutorial but I can't find which packages I may accidentally have gotten rid of... :/

The message I get is 'Your GStreamer installation is missing a plugin' 

Thanks!

---

### Post by Wrinkliez on 2010-03-14
did you install ubuntu restricted extras?

---

### Post by colobix on 2010-03-14
The gstreamer plugins are available in synaptic.
What you need is gstreamer0.10-ffmpeg and gstreamer0.10-plugins-base.
But install ubuntu restricted extras instead. That will give you everything you need.
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by lidex on 2010-03-14
You may want to add the medibuntu repository:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Detailed info:
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Pott on 2010-03-15
Repo already added and I already re-installed restricted extras... problem still there :(

---

### Post by lidex on 2010-03-15
Try this:
>     *

      Install the libdvdread4 package (no need to add third party repositories) via Synaptic or command line: 

 sudo apt-get install libdvdread4

    * Then open a terminal window and execute: 

 sudo /usr/share/doc/libdvdread4/install-css.sh

---

### Post by Pott on 2010-03-15
Still nothing. Jesus that's weird.

---

### Post by Pott on 2010-03-15
I reinstalled movie player and still nothing. None of these instructions changed anything at all...

I'd use VLC but it really sucks for DVD playback and so does mplayer. Movie player was my best choice and I have no idea what broke it :/

EDIT:

a quick look at this here thread [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683), re-entry of the appropriate apt command et voila, all back as it should :) Thanks everyone!

---

### Post by lidex on 2010-03-15
Glad you got it working. I never liked the totem interface so I gravitated to xine for dvds. It does a good job with menus. You may want to install the libdvdnav4 package.

---

