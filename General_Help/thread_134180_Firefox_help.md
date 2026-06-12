---
title: "Firefox help"
date: 2006-02-21
forum: General Help
---

### Post by shigs on 2006-02-21
Can anyone suggest a reason why firefox freazes 1 second into any video? If i press the refresh button it crashes completely. Here is the dump from the terminal when i go onto [http://www.break.com/index/celebrateearly.html](http://www.break.com/index/celebrateearly.html) (just an example)

NP_Initialize
totem_plugin_new_instance
Init scriptable instance
mode 1
argv[0] type application/x-mplayer2
argv[1] pluginspage [http://www.microsoft.com/Windows/MediaPlayer/](http://www.microsoft.com/Windows/MediaPlayer/)
argv[2] src [http://media1.break.com/dnet/media/content/celebrateearly.wmv](http://media1.break.com/dnet/media/content/celebrateearly.wmv)
argv[3] autostart 1
argv[4] showcontrols 1
argv[5] volume -20
argv[6] height 330
argv[7] width 440
plugin_get_value 14
plugin_set_window
about to fork
Launching: /usr/lib/totem/totem-mozilla-viewer --xid 39848875 --width 440 --heig ht 330 --url [http://media1.break.com/dnet/media/content/celebrateearly.wmv](http://media1.break.com/dnet/media/content/celebrateearly.wmv) fd:// 0
waiting for signal org.totem_9158.MozillaPluginService
Received notification for :1.7
Received notification for :1.7
Received notification for org.totem_9158.MozillaPluginService
Received notification for org.totem_9158.MozillaPluginService
Done forking, new proxy=0x8a5a660
leaving plugin_set_window
plugin_set_window
existing window
resize
leaving plugin_set_window
plugin_set_window
existing window
resize
leaving plugin_set_window
CMD line: /usr/lib/totem/totem-mozilla-viewer --xid 39848875 --width 440 --heigh t 330 --url [http://media1.break.com/dnet/media/content/celebrateearly.wmv](http://media1.break.com/dnet/media/content/celebrateearly.wmv) fd://0 
plugin_new_stream
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
** Message: ret -1
plugin_destroy_stream
** Message: totem_embedded_open 'fd://0'
Using DirectShow codec: wmv8ds32.ax
Decoder supports the following YUV formats: YUY2 IYUV UYVY YV12 YVYU I420 YVU9
Decoder is capable of YUV output (flags 0x7f)
plugin_destroy
** Message: stop
Die scriptable instance
Segmentation fault
shigs@Fingolfin:~$


Much love :xx

---

### Post by kaamos on 2006-02-21
Since totem seems to be causing trouble for a lot of people, you could try to remove the totem plugin for mozilla and install vlc- or mplayer-plugin.

Use synaptic for the removal/installation.

---

### Post by shigs on 2006-02-21
lol i've just noticed the video is ironically called "Dont Celebrate Too Soon" :( which i did.

---

### Post by shigs on 2006-02-21
ok willdo.

---

### Post by shigs on 2006-02-21
Thanks man, VLC works fine. Its a shame as i quite liked Totem to play DVDs in.

---

### Post by kaamos on 2006-02-21
You can still use totem for dvd's. :) Keep either totem-gstreamer or totem-xine (often works better) installed.

---

