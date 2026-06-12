---
title: "xorg-server compilation"
date: 2010-01-12
forum: General Help
---

### Post by shariefbe on 2010-01-12
Hello. I am trying to compile xorg-server for arm board. By that time i got a erro as 
```
checking for GL... configure: error: Package requirements (glproto >= 1.4.9 gl >= 7.1.0) were not met:

No package 'gl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

```

So i googled then i found that gl and mesa is same. sp i compiled mesa. by that time i got an error as 
```

tex-a8 -mfloat-abi=softfp -mfpu=vfp3 -ftree-vectorize -funroll-all-loops -Wall -Wmissing-prototypes -std=c99 -ffast-math -fno-strict-aliasing  -fPIC   -D_GNU_SOURCE -DPTHREADS -DHAVE_POSIX_MEMALIGN -DUSE_XSHM  glx_api.c -o glx_api.o
In file included from glx_api.c:34:
../../../../../include/GL/glx.h:38: fatal error: X11/Xlib.h: No such file or directory
compilation terminated.
make[5]: *** [glx_api.o] Error 1

```
 Now can anyone help me how to fix this problem

---

### Post by shariefbe on 2010-01-12
i already installed glproto.eventhogh getting the error
```

sharief@sharief-desktop:/mnt/freescale/nfs-develop/usr/local/lib/pkgconfig$ ls
alsa.pc                   gstreamer-base-0.10.pc          gstreamer-rtp-0.10.pc    shout.pc          xcb.pc              xcb-xinerama.pc
dri2proto.pc              gstreamer-cdda-0.10.pc          gstreamer-rtsp-0.10.pc   sm.pc             xcb-proto.pc        xcb-xprint.pc
gio-2.0.pc                gstreamer-check-0.10.pc         gstreamer-sdp-0.10.pc    vorbisenc.pc      xcb-randr.pc        xcb-xtest.pc
gio-unix-2.0.pc           gstreamer-controller-0.10.pc    gstreamer-tag-0.10.pc    vorbisfile.pc     xcb-record.pc       xcb-xvmc.pc
glib-2.0.pc               gstreamer-dataprotocol-0.10.pc  gstreamer-video-0.10.pc  vorbis.pc         xcb-render.pc       xcb-xv.pc
glproto.pc                gstreamer-fft-0.10.pc           gthread-2.0.pc           x11.pc            xcb-res.pc          xext.pc
gmodule-2.0.pc            gstreamer-floatcast-0.10.pc     ice.pc                   x11-xcb.pc        xcb-screensaver.pc  xextproto.pc
gmodule-export-2.0.pc     gstreamer-interfaces-0.10.pc    inputproto.pc            xau.pc            xcb-shape.pc        xproto.pc
gmodule-no-export-2.0.pc  gstreamer-net-0.10.pc           kbproto.pc               xcb-composite.pc  xcb-shm.pc          xt.pc
gobject-2.0.pc            gstreamer-netbuffer-0.10.pc     liboil-0.3.pc            xcb-damage.pc     xcb-sync.pc         xtrans.pc
gstreamer-0.10.pc         gstreamer-pbutils-0.10.pc       libxml-2.0.pc            xcb-dpms.pc       xcb-xevie.pc
gstreamer-app-0.10.pc     gstreamer-plugins-base-0.10.pc  ogg.pc                   xcb-dri2.pc       xcb-xf86dri.pc
gstreamer-audio-0.10.pc   gstreamer-riff-0.10.pc          pthread-stubs.pc         xcb-glx.pc        xcb-xfixes.pc
sharief@sharief-desktop:/mnt/freescale/nfs-develop/usr/local/lib/pkgconfig$ 

```

---

