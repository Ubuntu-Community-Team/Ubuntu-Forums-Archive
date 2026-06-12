---
title: "Songbird question"
date: 2010-12-03
forum: General Help
---

### Post by Adrienk on 2010-12-03
I love songbird more then any other media player on ubuntu or Linux for that fact. Their descion to take it out of linux because "no one uses it" is retarded

that aside I downloaded the latest nightly build for 686 (32 bit) which is [Songbird_1.10.0a-1913_linux-i686.tar.gz]("http://developer.songbirdnest.com/builds/trunk/latest/Songbird_1.10.0a-1913_linux-i686.tar.gz")

Had some issues running it from the terminal so i followed some forums and did the following:

**Note I am running ubuntu 10.10**

```


adam@adam-pc:~$ sudo apt-get remove libvisual-0.4-plugins
[sudo] password for adam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libvisual-0.4-plugins
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 557kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 152750 files and directories currently installed.)
Removing libvisual-0.4-plugins ...
adam@adam-pc:~$ '/home/adam/Desktop/Songbird_build-1913/songbird-bin' 

(songbird-bin:2987): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': /usr/lib/gstreamer-0.10/libgstffmpeg.so: undefined symbol: gst_caps_set_value

(songbird-bin:2987): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libfsfunnel.so': /usr/lib/gstreamer-0.10/libfsfunnel.so: undefined symbol: gst_pad_peer_get_caps_reffed

(songbird-bin:2987): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstjpegformat.so': /usr/lib/gstreamer-0.10/libgstjpegformat.so: undefined symbol: gst_byte_writer_put_uint8

(songbird-bin:2987): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstaiff.so': /usr/lib/gstreamer-0.10/libgstaiff.so: undefined symbol: gst_byte_writer_put_uint32_be

(songbird-bin:2987): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgnl.so': /usr/lib/gstreamer-0.10/libgnl.so: undefined symbol: gst_pad_link_full

(songbird-bin:2987): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstcog.so': /usr/lib/gstreamer-0.10/libgstcog.so: undefined symbol: gst_video_parse_caps_color_matrix

(songbird-bin:2987): GLib-GObject-WARNING **: cannot register existing type `GstVideoBalance'

(songbird-bin:2987): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(songbird-bin:2987): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(songbird-bin:2987): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(songbird-bin:2987): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

(songbird-bin:2987): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsth264parse.so': /usr/lib/gstreamer-0.10/libgsth264parse.so: undefined symbol: gst_byte_writer_init_with_size

(songbird-bin:2987): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmpegdemux.so': /usr/lib/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: gst_tag_get_language_code_iso_639_1

ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstaasink.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal



```

Are there any known fixes for this?

---

### Post by Adrienk on 2010-12-03
any one got the answer?

---

### Post by Adrienk on 2010-12-03
bump

---

### Post by Adrienk on 2010-12-03
to the top you go

---

