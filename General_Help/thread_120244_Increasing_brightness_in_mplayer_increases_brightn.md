---
title: "Increasing brightness in mplayer increases brightness in X"
date: 2006-01-21
forum: General Help
---

### Post by Witty Name on 2006-01-21
I'm using the nvidia-glx from the official repositories, and have these video-out drivers:
```

Available video output drivers:
        x11     X11 ( XImage/Shm )
        xover   General X11 driver for overlay capable video output drivers
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        xvidix  X11 (VIDIX)
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame

```

I've built mplayer with --enable-gui and --enable-menu.

EDIT: apt-get install libxv-dev and recompiling helped.

---

