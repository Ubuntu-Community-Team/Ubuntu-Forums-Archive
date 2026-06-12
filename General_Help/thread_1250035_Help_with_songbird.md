---
title: "Help with songbird"
date: 2009-08-26
forum: General Help
---

### Post by t4ggs on 2009-08-26
when i try launching songbird it doesnt work so i tried launching it from the terminal and thats what i get

```
(songbird-bin:7121): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:7121): GStreamer-WARNING **: invalid name template bwf_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:7121): GStreamer-WARNING **: invalid name template alaw_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:7121): GStreamer-WARNING **: invalid name template dv_dif_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:7121): GStreamer-WARNING **: invalid name template jpeg2000_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:7121): GStreamer-WARNING **: invalid name template mpeg_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:7121): GStreamer-WARNING **: invalid name template mpeg_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:7121): GStreamer-WARNING **: invalid name template up_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:7121): GStreamer-WARNING **: invalid name template vc3_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:7121): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstlibvisual.so': /usr/lib/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:7121): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libresindvd.so': /usr/lib/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:7121): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsthdvparse.so': /usr/lib/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:7121): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdeinterlace.so': /usr/lib/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

i really dont understand what should i do with this gstreamer error?? anyone here knows???

---

### Post by invader_dag on 2009-08-26
I too am having the same problem. I believe it is due to a new version of GStreamer

---

### Post by invader_dag on 2009-08-26
Just found directions on a blog, though not in English, for installing Songbird 1.4 on Karmic Koala. I replace Karmic with Jaunty and the latest release works without problems for me now. Here is the site, with google translation link below:

[http://weblogs.inf.udp.cl/nboettcher/25/07/2009/instalar-songbird-14-en-ubuntu-910-karmic-koala/](http://weblogs.inf.udp.cl/nboettcher/25/07/2009/instalar-songbird-14-en-ubuntu-910-karmic-koala/)

[http://translate.google.com/translate?hl=en&sl=es&u=http://weblogs.inf.udp.cl/nboettcher/25/07/2009/instalar-songbird-14-en-ubuntu-910-karmic-koala/&ei=-lCVStuuCN7ktgeZxLBM&sa=X&oi=translate&resnum=6&ct=result&prev=/search%3Fq%3Dconversion%2Bspecification%2Bmust%2Bbe%2Bof%2Btype%2B%2527%2525d%2527%2Bor%2B%2527%2525s%2527%2Bfor%2BGST_PAD_REQUEST%2Bpadtemplate%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26hs%3DZbK](http://translate.google.com/translate?hl=en&sl=es&u=http://weblogs.inf.udp.cl/nboettcher/25/07/2009/instalar-songbird-14-en-ubuntu-910-karmic-koala/&ei=-lCVStuuCN7ktgeZxLBM&sa=X&oi=translate&resnum=6&ct=result&prev=/search%3Fq%3Dconversion%2Bspecification%2Bmust%2Bbe%2Bof%2Btype%2B%2527%2525d%2527%2Bor%2B%2527%2525s%2527%2Bfor%2BGST_PAD_REQUEST%2Bpadtemplate%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26hs%3DZbK)

---

### Post by t4ggs on 2009-08-26
thanks ill try it and let u know if it worked....and btw i speak spanish so thank u for finding it in spanish haha

---

### Post by t4ggs on 2009-08-26
well it worked, so thank u very much...the only downside is that most of my addons are not supported

---

