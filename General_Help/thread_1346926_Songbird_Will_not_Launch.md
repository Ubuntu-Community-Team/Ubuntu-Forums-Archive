---
title: "Songbird Will not Launch"
date: 2009-12-05
forum: General Help
---

### Post by Joseph Schwenker on 2009-12-05
I have been having nothing but problems with Ubuntu 9.10.  If I leave anything open when I shut down my computer, my computer will have some new problem when I turn it on again.  For some reason, Songbird will not launch.  It used to, and now it doesn't.  I uninstalled it, then tried to use a .deb to reinstall it, but the .deb didn't work.  I ended up downloading a tar.gz of it, and that wouldn't even work.  When I tried to launch it, the terminal said that it needed "libjemalloc.so" or something, so I dragged that file into /lib.  Now, the terminal will output ```
(songbird-bin:2710): GStreamer-WARNING **: invalid name template bwf_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:2710): GStreamer-WARNING **: invalid name template alaw_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:2710): GStreamer-WARNING **: invalid name template dv_dif_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:2710): GStreamer-WARNING **: invalid name template jpeg2000_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:2710): GStreamer-WARNING **: invalid name template mpeg_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:2710): GStreamer-WARNING **: invalid name template mpeg_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:2710): GStreamer-WARNING **: invalid name template up_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:2710): GStreamer-WARNING **: invalid name template vc3_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:2710): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:2710): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: gst_adapter_masked_scan_uint32
/home/joseph/Songbird/songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

``` when I try to launch Songbird.  I was using Songbird fine last night, and now it won't work at all!  I need help!  Yes, the file has permissions to be executable.

---

### Post by Joseph Schwenker on 2009-12-05
Come on!  I really need this solved!

---

### Post by Joseph Schwenker on 2009-12-05
Well, I just decided to switch back to Ubuntu 9.04.  Golly, Ubuntu 9.10 is the worst release of Ubuntu EVER!  I have never seen such a step backward in terms of stability.

---

### Post by shyam.s on 2009-12-24
Even I had the problem.

But gave the following command and it worked but had some UI Issues.

Export LD_BIND_NOW = 1
songbird

---

### Post by arnab_das on 2010-01-11
facing same prob. need a solution urgently.

---

### Post by arnab_das on 2010-01-11
here's what i did. i removed the Songbird and .songbird2 directories. and reinstalled songbird from the synaptic. running like a breeze now!

---

### Post by neeraj2608 on 2010-01-28
> **shyam.s said:**
> Even I had the problem.

But gave the following command and it worked but had some UI Issues.

Export LD_BIND_NOW = 1
songbird
Yup, that works for me too.

---

