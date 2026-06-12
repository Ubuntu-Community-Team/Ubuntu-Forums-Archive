---
title: "Totem not playing video"
date: 2012-03-19
forum: General Help
---

### Post by cscj01 on 2012-03-19
I have Ubuntu 11.10 x64 and Totem 3.3.90 that uses GStreamer 0.10.35.  I can no longer play videos (at least not wmv videos).  When I double-click the file, the first frame of the video is displayed.  The audio begins to play and the progress bar moves across the screen, but the image never changes.

I am not sure if this is related, but I had an issue with getting Gimp 2.7.5 installed and had to add two PPA's to get a dependency satisfied:```
[http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu)
[http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu)
```  I left these two sources active and began to get many (daily) updates.  I decided to uncheck the two PPA's.  When I noticed that Totem was not working properly, I tried to delete it and re-install it, but I had dependencies that could not be satisfied unless I re-activated the two sources.  I tried to install Totem with the command ```
sudo apt-get install totem-gstreamer
``` but I got the following message ```
Package totem-gstreamer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  totem-plugins-extra:i386 totem-plugins-extra

```

  If the above is the problem, how can I get back to the Totem and GStreamer that came with Oneiric?

---

### Post by cscj01 on 2012-03-20
bump

---

### Post by cscj01 on 2012-03-21
bump

---

### Post by cscj01 on 2012-03-28
I just discovered today that the Totem Firefox plugin plays video.  Yet, my desktop Totem does not play videos.  It only shows the first frame and the progress bar moves across the window until it reaches the end.  I can also now say that Totem does not play any videos, not just .wmv.  Additionally, the audio plays correctly in all videos.

If no one has any ideas, I'll file a bug report.

---

### Post by cscj01 on 2012-03-28
Can anyone tell me what any of this output of the command ```
GST_DEBUG_NO_COLOR=1 GST_DEBUG=*:2 totem 2> log
``` is indicating:
```
(totem:11721): Totem-WARNING **: Tried to set sidebar page 'properties' but it does not exist

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-added' is invalid for instance `0x7fe77c16dd10'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-removed' is invalid for instance `0x7fe77c16dd10'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-added' is invalid for instance `0x7fe77c3580b0'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-removed' is invalid for instance `0x7fe77c3580b0'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-added' is invalid for instance `0x7fe77c3582c0'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-removed' is invalid for instance `0x7fe77c3582c0'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-added' is invalid for instance `0x7fe77c3584d0'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-removed' is invalid for instance `0x7fe77c3584d0'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-added' is invalid for instance `0x7fe77c3586e0'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-removed' is invalid for instance `0x7fe77c3586e0'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-added' is invalid for instance `0x7fe77c3588f0'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-removed' is invalid for instance `0x7fe77c3588f0'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-added' is invalid for instance `0x7fe77c358b00'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-removed' is invalid for instance `0x7fe77c358b00'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-added' is invalid for instance `0x7fe77c358d10'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-removed' is invalid for instance `0x7fe77c358d10'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-added' is invalid for instance `0x7fe77c358f20'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-removed' is invalid for instance `0x7fe77c358f20'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-added' is invalid for instance `0x7fe77c359130'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-removed' is invalid for instance `0x7fe77c359130'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-added' is invalid for instance `0x7fe77c359340'

(totem:11721): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.23+git20120319.322c6e93/./gobject/gsignal.c:2455: signal `child-removed' is invalid for instance `0x7fe77c359340'

(totem:11721): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
0:00:13.743871846 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:209:gst_ogg_stream_get_packet_duration: Failed to determine packet duration
0:00:13.744070187 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggdemux.c:2666:gst_ogg_demux_read_chain:<oggdemux0> page is not BOS page
0:00:13.744086833 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggdemux.c:746:gst_ogg_pad_submit_packet:<oggdemux0> got skeleton packet for stream 0x1814b5a8
0:00:13.744098919 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:209:gst_ogg_stream_get_packet_duration: Failed to determine packet duration
0:00:13.744537471 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:1095:gst_ogg_map_parse_fisbone: small fisbone packet of size 0, ignoring
0:00:13.744550949 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:209:gst_ogg_stream_get_packet_duration: Failed to determine packet duration
0:00:13.744919362 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggdemux.c:2662:gst_ogg_demux_read_chain:<oggdemux0> problem reading BOS page: ret=-3
0:00:13.748142985 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:209:gst_ogg_stream_get_packet_duration: Failed to determine packet duration
0:00:13.748171936 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:209:gst_ogg_stream_get_packet_duration: Failed to determine packet duration
0:00:13.748182248 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:209:gst_ogg_stream_get_packet_duration: Failed to determine packet duration
0:00:13.748280728 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:209:gst_ogg_stream_get_packet_duration: Failed to determine packet duration
0:00:13.748304574 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggdemux.c:746:gst_ogg_pad_submit_packet:<oggdemux0> got skeleton packet for stream 0x1814b5a8
0:00:13.748317157 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:209:gst_ogg_stream_get_packet_duration: Failed to determine packet duration
0:00:13.748360160 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:1095:gst_ogg_map_parse_fisbone: small fisbone packet of size 0, ignoring
0:00:13.748372258 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:209:gst_ogg_stream_get_packet_duration: Failed to determine packet duration
0:00:13.810362489 11721 0x7fe77bdf4aa0 WARN                   totem bacon-video-widget-gst-0.10.c:1437:bvw_handle_element_message: Unhandled element message playbin2-stream-changed from play: element message from element 'play': playbin2-stream-changed, uri=(string)file:///home/butch/utweakactions.ogv;
0:00:13.810771425 11721 0x7fe77cbe92d0 WARN                     bin gstbin.c:2380:gst_bin_do_latency_func:<play> did not really configure latency of 0:00:00.000000000
0:00:50.682346432 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:209:gst_ogg_stream_get_packet_duration: Failed to determine packet duration
0:00:50.682699436 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggdemux.c:746:gst_ogg_pad_submit_packet:<oggdemux0> got skeleton packet for stream 0x1814b5a8
0:00:50.682723932 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:209:gst_ogg_stream_get_packet_duration: Failed to determine packet duration
0:00:50.682795988 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:1095:gst_ogg_map_parse_fisbone: small fisbone packet of size 0, ignoring
0:00:50.682815999 11721 0x7fe77cbd2ad0 WARN                oggdemux gstoggstream.c:209:gst_ogg_stream_get_packet_duration: Failed to determine packet duration
```

---

### Post by cscj01 on 2012-06-25
bump

I am now on 12.04 with the same problem.

---

