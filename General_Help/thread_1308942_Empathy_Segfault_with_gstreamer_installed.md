---
title: "Empathy Segfault with gstreamer installed"
date: 2009-11-01
forum: General Help
---

### Post by mpp on 2009-11-01
Hello Hello,

I've just upgraded my desktop PC from jaunty to karmic (32-bit Ubuntu) but can't get empathy to work:

```
$ empathy
(empathy:9718): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: schro_virt_frame_new_vert_downsample
Segmentation fault (core dumped)

```

I've found some [discussion]("http://ubuntuforums.org/showthread.php?t=1300203") suggesting the removal of gstreamer-ffmpeg, but I don't want to remove that because I use it for other things.  The official FAQ also suggests removing gstreamer [http://live.gnome.org/Empathy/FAQ#head-0cf7b08b5a6dd38484cb692f72da4475997aa008]("http://live.gnome.org/Empathy/FAQ#head-0cf7b08b5a6dd38484cb692f72da4475997aa008").

Can anyone suggest a workaround, perhaps to disable this plugin before empathy starts up??  Or will I just have to wait for the bug fix to be applied??

have fun()
mike

---

### Post by mpp on 2009-11-06
Looks like there's been a fix, as with the latest updates I can now run empathy with the ffmpeg libraries installed.

have fun()
mike

---

