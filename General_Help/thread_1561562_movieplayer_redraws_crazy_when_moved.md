---
title: "movieplayer redraws crazy when moved"
date: 2010-08-26
forum: General Help
---

### Post by locoHost on 2010-08-26
Something seems to be wrong with the form redraw. When I open a movie in movieplayer, it looks Ok until I try to resize the window or move it. Then it draws crazy, repeats elements in the form, and kills the movie image. You can still hear it, but it's black. Something is up with the software that draws apps on the screen. Have you seen this or have an idea what might be going on?

Thanks guys :-)

---

### Post by no2498 on 2010-08-26
wright down your settings before you change them so you can set them back if need to. and try this

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

### Post by locoHost on 2010-09-07
Turns out it was the desktop visual effects. I had them set on high which worked fine for pretty much all windows except for the movie player. I guess the vid card isn't buff enuff to handle the jello effects and a running video.

:D

---

