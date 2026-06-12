---
title: "Logitech webcam"
date: 2010-09-23
forum: General Help
---

### Post by Eric-A on 2010-09-23
I'm running ubuntu 10.04 and have a logitech webcam that's a few years old. When I run "cheese" all I see are wavy lines. Has anyone fixed this?

---

### Post by no2498 on 2010-09-23
you may need to make the pic smaller in cheese 

if no help look in the cheese help FAQ"S
? 5.1 should help you

---

### Post by Eric-A on 2010-09-23
I read the faq and did as it said, "qcset /dev/video0 compat=dblbuf" and it didn't help.

---

### Post by no2498 on 2010-09-24
this is ? 5.1

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    



this may help too




gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

---

