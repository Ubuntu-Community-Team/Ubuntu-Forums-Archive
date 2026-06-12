---
title: "Songbird does not work after upgrade to 1.4.3"
date: 2010-01-18
forum: General Help
---

### Post by Hugh Mulqueen on 2010-01-18
My problem is simple songbird doesn't start after I applied the upgrade to 1.4.3. 

heres the output I get when I run it in terminal:

```
(songbird-bin:3596): GLib-WARNING **: g_set_prgname() called multiple times

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmpegdemux.so': /usr/lib64/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstschro.so': /usr/lib64/gstreamer-0.10/libgstschro.so: undefined symbol: g(songbird-bin:3596): GLib-WARNING **: g_set_prgname() called multiple times

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmpegdemux.so': /usr/lib64/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstschro.so': /usr/lib64/gstreamer-0.10/libgstschro.so: undefined symbol: gst_adapter_masked_scan_uint32

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libresindvd.so': /usr/lib64/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstlibvisual.so': /usr/lib64/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmatroska.so': /usr/lib64/gstreamer-0.10/libgstmatroska.so: undefined symbol: gst_util_array_binary_search

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstrawparse.so': /usr/lib64/gstreamer-0.10/libgstrawparse.so: undefined symbol: gst_video_format_new_caps_interlaced

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdv.so': /usr/lib64/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdeinterlace.so': /usr/lib64/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgsthdvparse.so': /usr/lib64/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstavi.so': /usr/lib64/gstreamer-0.10/libgstavi.so: undefined symbol: _gst_debug_dump_mem
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal
st_adapter_masked_scan_uint32

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libresindvd.so': /usr/lib64/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstlibvisual.so': /usr/lib64/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmatroska.so': /usr/lib64/gstreamer-0.10/libgstmatroska.so: undefined symbol: gst_util_array_binary_search

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstrawparse.so': /usr/lib64/gstreamer-0.10/libgstrawparse.so: undefined symbol: gst_video_format_new_caps_interlaced

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdv.so': /usr/lib64/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdeinterlace.so': /usr/lib64/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgsthdvparse.so': /usr/lib64/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstavi.so': /usr/lib64/gstreamer-0.10/libgstavi.so: undefined symbol: _gst_debug_dump_mem
././songbird-bin: symbol lookup error: /us(songbird-bin:3596): GLib-WARNING **: g_set_prgname() called multiple times

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmpegdemux.so': /usr/lib64/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstschro.so': /usr/lib64/gstreamer-0.10/libgstschro.so: undefined symbol: g(songbird-bin:3596): GLib-WARNING **: g_set_prgname() called multiple times

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmpegdemux.so': /usr/lib64/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstschro.so': /usr/lib64/gstreamer-0.10/libgstschro.so: undefined symbol: gst_adapter_masked_scan_uint32

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libresindvd.so': /usr/lib64/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstlibvisual.so': /usr/lib64/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmatroska.so': /usr/lib64/gstreamer-0.10/libgstmatroska.so: undefined symbol: gst_util_array_binary_search

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstrawparse.so': /usr/lib64/gstreamer-0.10/libgstrawparse.so: undefined symbol: gst_video_format_new_caps_interlaced

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdv.so': /usr/lib64/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdeinterlace.so': /usr/lib64/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgsthdvparse.so': /usr/lib64/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstavi.so': /usr/lib64/gstreamer-0.10/libgstavi.so: undefined symbol: _gst_debug_dump_mem
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal
st_adapter_masked_scan_uint32

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libresindvd.so': /usr/lib64/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstlibvisual.so': /usr/lib64/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmatroska.so': /usr/lib64/gstreamer-0.10/libgstmatroska.so: undefined symbol: gst_util_array_binary_search

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstrawparse.so': /usr/lib64/gstreamer-0.10/libgstrawparse.so: undefined symbol: gst_video_format_new_caps_interlaced

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdv.so': /usr/lib64/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdeinterlace.so': /usr/lib64/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgsthdvparse.so': /usr/lib64/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:3600): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstavi.so': /usr/lib64/gstreamer-0.10/libgstavi.so: undefined symbol: _gst_debug_dump_mem
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal
r/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

Anybody have any ideas whats going on???

I'm sick and tired of the songbird community they're not deadicated to the linux community at all. Its just one set back after another with them. I for one am sick of it. CD rip is just one problem (Windows only) and now there stopping the development of the [ipod plugin]("http://blog.songbirdnest.com/2009/08/05/open-sourcing-the-ipod-add-on/") aswell. Its ****.

Anybody having the same problem.

---

### Post by Hugh Mulqueen on 2010-03-12
Lads any update on this problem???

Still having the same issues.

going to try sorting it with lucid and the upstream kernal.

see whats what will update tommorrow. good luck...

---

### Post by ubunterooster on 2010-03-12
Uninstall song bird, then install it again via synaptic. (Don't just select "reinstall" )

---

### Post by metaphorm on 2010-04-01
did that - complete removal, reinstalled. doesn't work still. same glib called multiple times error... :(

---

### Post by ubunterooster on 2010-04-01
Are you sure the problem is with songbird and not Gstreamer? try another player such as exaile to check.

---

### Post by conceptrat on 2010-05-20
Okay so I did a search around for you (and me :) ) and found this [[http://www.jonathanmoeller.com/screed/?p=1228]](http://www.jonathanmoeller.com/screed/?p=1228]).  The link mentioned on there is no longer valid but the instructions that Brent has quoted work for me.  Give it a try :)

---

