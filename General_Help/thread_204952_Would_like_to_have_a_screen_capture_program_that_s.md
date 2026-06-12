---
title: "Would like to have a screen capture program that saves to video file"
date: 2006-06-27
forum: General Help
---

### Post by JanHammer on 2006-06-27
Alrighty, so I just got XGL installed and it is **very cool**. So cool that I want to make a video of me playing with it and showing it to some of my friends who use windows xD. So far I keep getting programs that only record actions (like WINK or vnc2swf). So will someone please enlighten me on the program I want?

---

### Post by matrooswolf on 2006-06-27
Try Istanbul session recorder

---

### Post by JanHammer on 2006-06-27
That still didn't do a complete video file of it. Just when I clicked and some mouse motions. I really just want something that takes real-time video of what's going on.

---

### Post by matrooswolf on 2006-06-28
Did you try this:
> "Recommended Settings
Set your Xorg server display to use 800x600. You can't just set this resolution via gnome's support for xrandr yet. To make sure you get a proper screen capture you need to make sure that the X server itself is set to 800x600 (with system-config-display for instance) and that the gnome desktop is configured to use the default X resolution and refresh rate. If you attempt to lower your desktop resolution using xrandr for your desktop you will most likely see artifacts in the videos.

Set istanbul framerate to 1.0 frames per second. This should be fast enough to record most human interactions with the desktop and will be slow enough to prevent egregious problems with frames being dropped. Upstream is currently working on fixing the performance issues with capturing the x display image. The recommended framerate will be adjusted as performance improvements to gstreamer's display capture plugin are made available.

Set the istanbul encode image size to be 240x192 for a web friendly video size. This is 1/4 the area of the desktop and text should still be legible. If you shrink the image too much as part of the encoding process small text can become obscured. "

Or else try xvidcap (but I have never tried that one ...)

Good luck!

---

