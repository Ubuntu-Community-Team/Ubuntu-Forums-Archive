---
title: "Songbird and GStreamer problems."
date: 2010-03-26
forum: General Help
---

### Post by spillin_dylan on 2010-03-26
Lately I've been having some problems playing music on my laptop running 9.10.  Here's what I know:

```
spillin@Dylans-A300:~$ songbird

(songbird-bin:8609): GLib-WARNING **: g_set_prgname() called multiple times

(songbird-bin:8663): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgsthdvparse.so': /usr/lib64/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:8663): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libresindvd.so': /usr/lib64/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:8663): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstlibvisual.so': /usr/lib64/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:8663): GStreamer-WARNING **: invalid name template bwf_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8663): GStreamer-WARNING **: invalid name template alaw_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8663): GStreamer-WARNING **: invalid name template dv_dif_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8663): GStreamer-WARNING **: invalid name template jpeg2000_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8663): GStreamer-WARNING **: invalid name template mpeg_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8663): GStreamer-WARNING **: invalid name template mpeg_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8663): GStreamer-WARNING **: invalid name template up_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8663): GStreamer-WARNING **: invalid name template vc3_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8663): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdv.so': /usr/lib64/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full

(songbird-bin:8663): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:8663): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstavi.so': /usr/lib64/gstreamer-0.10/libgstavi.so: undefined symbol: _gst_debug_dump_mem
/opt/Songbird/./songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

Banshee and Rhythmbox both work, although they seem to work much slower than they used to.  When using Rhythmbox, my CPU usage ramps right up to 100% on both cores, so that can't be good...  

I'm pretty sure I have GStreamer installed, and I don't know what changed to cause this error.  Any suggestions?

---

### Post by spillin_dylan on 2010-03-31
bump

---

### Post by Spaced on 2010-04-13
I have the same problem. First I've tried the repositories version; it started but then didn't play some files (like aac's). The I've tried the stand-alone version downloaded from the website, and it just doesn't load, giving a series of errors in loading gstreamer plugins.

---

