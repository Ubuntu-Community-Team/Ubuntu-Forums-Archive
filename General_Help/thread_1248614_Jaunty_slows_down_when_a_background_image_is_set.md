---
title: "Jaunty slows down when a background image is set"
date: 2009-08-24
forum: General Help
---

### Post by rswoods on 2009-08-24
I've been having this issue since Jaunty was first made available, but just recently have been able to narrow down the cause of it.

When I have a background image set, the window manager appears to slow down to a crawl.  Minimized windows' titlebars hang for a few seconds after the rest of the window has already been minimized, and desktop icons take quite a few seconds to redraw.  Dragging a window over the desktop icons also causes them to disappear and take their sweet time reappearing.  This occurs whether the background image is stretched or tiled.  Setting a solid color for the background makes everything run swell again.

This problem puzzled me because it persisted across both metacity AND openbox, as well with both nautilus AND pcmanfm.  Switching to different and more "lightweight" components didn't help at all.  I just happened to have a plain background set just now and was surprised to see openbox behaving as its usual self.  Setting a background restores the slowness.

As a side, somehow compiz works just great.  The window decorations are snappy and the desktop icons are redrawn before the window even reaches the taskbar.  That had puzzeled me since compiz is considered more demanding than metacity or openbox, now I can see that it is a software issue.

Has anyone else experienced this problem?  I assume it's a common one since I've had it over every machine I've tried jaunty on, though I haven't found much on it in searches.  For the time being I am running with a solid background since I don't care much, but I thought this issue would have gotten more attention by now.

---

