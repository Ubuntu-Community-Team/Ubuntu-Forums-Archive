---
title: "select mp3 encoding bitrate in juicer"
date: 2005-03-13
forum: General Help
---

### Post by Kymon on 2005-03-13
i tried to follow a thread from the howto section, doing the following on warty warthog:

installed:
liblame0, v 3.96.1-1
gstreamer0.8-lame, v 0.8.2-2
gstreamer-editor, v 0.5.0-4

changed gconf key:
extension mp3
pipeline audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1002

started gst-editor from console.
next you're supposed to look for a "Codec" option in the utility palette, but the only options available are filter, generic, sinc and source.

what am i missing?

---

