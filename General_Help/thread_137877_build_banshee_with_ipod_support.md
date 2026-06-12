---
title: "build banshee with ipod support"
date: 2006-02-28
forum: General Help
---

### Post by zachtib on 2006-02-28
I'm trying to build the latest banshee from source from the 0.10.6 tarball under breezy, 
./configure exits fine, but outputs:

```
banshee-0.10.6

    Install Prefix:    /opt
    C Compiler:        gcc
    Mono C# Compiler:  /usr/lib/pkgconfig/../../bin/mcs
    Mono Runtime:      /usr/lib/pkgconfig/../../bin/mono

    Engines:
      GStreamer:       yes, 0.8
      Helix:           yes
      VLC:             no

    Digital Audio Players (DAP):
      iPod:            no
      NJB:             no

    Xing MP3 Encoder:  no
    GStreamer Plugins: /usr/lib/gstreamer-0.8
    DAAP Support:      yes

    Helix/RealPlayer:  no

```

But i want banshee built with ipod support. how to i enable this?

---

### Post by RAOF on 2006-02-28
You'll need "libipoddevice" and "ipod-sharp" (which is called something different in the Ubuntu package - I think it's ipod-cil, or something similar).

Then you'll need to pass "--enable-ipod" to configure.  As a general rule, typing ./configure --help will get you a list of the available options, and their defaults.

---

### Post by zachtib on 2006-02-28
[QUOTE=RAOF]You'll need "libipoddevice" and "ipod-sharp" (which is called something different in the Ubuntu package - I think it's ipod-cil, or something similar).

Then you'll need to pass "--enable-ipod" to configure.  As a general rule, typing ./configure --help will get you a list of the available options, and their defaults.[/QUOTE]
i got it to work, and after setting up and organizing my library, i plugged in my ipod... and the whole thing crashed.  so i tried upgrading some other mono stuff an eventually screwed up mono altogether.  I can't wait for dapper to come out, so i can just wipe this whole thing and do a fresh install...

---

