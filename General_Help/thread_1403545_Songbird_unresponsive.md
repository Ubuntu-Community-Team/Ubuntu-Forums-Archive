---
title: "Songbird unresponsive"
date: 2010-02-10
forum: General Help
---

### Post by sbelz79 on 2010-02-10
I'm running Ubuntu 9.10 x64 on a system that has an AMD Phenom II x4 and 4 GB DDR3 RAM.

Songbird was working fine until last night, when it became unresponsive.  rebooting seemed to fix the problem, but today, Songbird is totally unresponsive as soon as I open it.  It doesn't matter if I leave it alone to give it time to load- it's DOA every time.

I installed it by downloading from getsongbird.com, and extracting the Songbird folder to my home folder.  I then simply created a launcher to open it that uses the command Songbird/songbird to start it.  I tried removing my songbird folder, downloading a new player, and installing it using the same method, but I had the same problem again.

I know I can just use banshee or rhythm box, but they're lacking features that songbird has (especially the duplicate track removal tool- for some reason, when I imported my media library into banshee, it created duplicates of numerous tracks, despite the fact that there aren't duplicate files in my music folder)

---

### Post by n0dix on 2010-02-10
Run the problem in console, and post the output, please.

---

### Post by sbelz79 on 2010-02-10
> **n0dix said:**
> Run the problem in console, and post the output, please.

I'll do it late tonight when I get home, or possibly tomorrow morning.

---

### Post by sbelz79 on 2010-02-11
OK, I ran songbird in the terminal and had the same problem.  I clicked on the playlist a couple time, tried to close with the 'x' a couple times, then killed it by r clicking the songbird tab on the bottom panel, and selected "force quit" when prompted.  Here's the output:

```
me@computer:~$ Songbird/songbird

(songbird-bin:30764): GLib-WARNING **: g_set_prgname() called multiple times

(songbird-bin:30775): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstavi.so': /usr/lib64/gstreamer-0.10/libgstavi.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:30775): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdv.so': /usr/lib64/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full

(songbird-bin:30775): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstschro.so': /usr/lib64/gstreamer-0.10/libgstschro.so: undefined symbol: gst_adapter_masked_scan_uint32

(songbird-bin:30775): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstlibvisual.so': /usr/lib64/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:30775): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstrawparse.so': /usr/lib64/gstreamer-0.10/libgstrawparse.so: undefined symbol: gst_video_format_new_caps_interlaced

(songbird-bin:30775): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdeinterlace.so': /usr/lib64/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced

(songbird-bin:30775): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgsthdvparse.so': /usr/lib64/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:30775): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libresindvd.so': /usr/lib64/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:30775): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmatroska.so': /usr/lib64/gstreamer-0.10/libgstmatroska.so: undefined symbol: gst_util_array_binary_search

(songbird-bin:30775): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmpegdemux.so': /usr/lib64/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:30775): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:30764): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:30764): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:30764): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:30764): Gdk-WARNING **: gdk_window_set_icon_list: icons too large
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Properties::read() -- Could not find a valid first MPEG frame in the stream.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.

(songbird-bin:30764): Gtk-CRITICAL **: gtk_drag_set_icon_default: assertion `GDK_IS_DRAG_CONTEXT (context)' failed
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
Killed
me@computer:~$
```

---

### Post by n0dix on 2010-02-11
Do you have the gstreamer-python plugin?

---

### Post by sbelz79 on 2010-02-11
I don't seem to have the gstreamer-python plugin.  I looked in Synaptic, and there are several different gstreamer and python packages installed, but nothing matches "gstreamer-python" (installed or not) when I type it in the quick search field.

Incidentally I fixed the problem I was having.  I remembered today that I had turned on the option "automatically watch for changes in the following folder" in Songbird's Tools>Options>Media Importer>Watch Folders tab, and had set it to a folder in which completed bittorrents arrive.  I thought that it would just overlook video and iso files, or at the worst deliver an error message stating that those files couldn't be imported.  When I removed all of the files from this folder and started up Songbird, I had no problems at all.  I was then able to turn off this option (I'll just have to manually import completed bittorrents).

In any case, if the gstreamer-python plugin is something I should have, let me know how I can install it.  If it's not that important, let me know too.  Though technically this problem is solved, I want to wait until I hear back about the gstreamer-python plugin before I label it as such.

Thanks!

---

### Post by n0dix on 2010-02-11
I find something related the gstreamer-python plugin, but, if you solved your problem, it wouldn't be necessary.

---

