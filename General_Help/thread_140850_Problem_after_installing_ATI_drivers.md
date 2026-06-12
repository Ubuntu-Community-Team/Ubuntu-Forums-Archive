---
title: "Problem after installing ATI drivers"
date: 2006-03-07
forum: General Help
---

### Post by Apuu on 2006-03-07
After installing Ubuntu provided ATI drivers first I wasn't able to watch videos and "select colour" changed to purple.
Tested at the multimedia system panel and got error with Xwindows(x11/XShmXv) and Video for Linux 2 (v4l2)'.
I corrected the first one by adding lines to device section in xorg.conf. 
"Option "VideoOverlay"               "on"
Option "OpenGLOverlay"              "off" 

It corrected the video problem and Xwindows(x11/XShmXv) error, but the second problem still remains. All window titlebars and selected texts are purple.

Any ideas :-|

---

