---
title: "CPU problem"
date: 2010-09-06
forum: General Help
---

### Post by Vistz on 2010-09-06
This problem just started recently for me. I'm on a laptop and whenever I start watching a video, the CPU will gradually inch up to 100% (the system monitor is on my panel). At this point, the video becomes laggy and my browser freezes. This happens even when I'm just browsing online. Also, my laptop becomes warm/hot during when this is happening. Is there any way to fix this?

---

### Post by no2498 on 2010-09-06
this helps me so i hope it helps you
write your settings down so you can set them back if needed

this comes from the program cheese


&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

### Post by Vistz on 2010-10-29
> **no2498 said:**
> this helps me so i hope it helps you
write your settings down so you can set them back if needed

this comes from the program cheese


&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

I realize that this post was made awhile ago but I tried your method and the cpu still creeps towards 100%. Then my entire computer starts to get laggy. I'm not sure if this is a bug for my specific kernel or my computer. But this is what I got from the terminal

```
uname -r
2.6.32-25-generic

```

---

### Post by no2498 on 2010-10-29
did you restart the computer yet ?

try the same video with the epiphany web browser
i also use opera web browser

[http://www.opera.com/download/](http://www.opera.com/download/)

---

### Post by Vistz on 2010-10-29
> **no2498 said:**
> did you restart the computer yet ?

try the same video with the epiphany web browser
i also use opera web browser

[http://www.opera.com/download/](http://www.opera.com/download/)

Yes, I restarted the computer. This problem has shown up in Firefox as well as Chrome. I'm not sure what using another browser will do though.

---

### Post by Omnomnom on 2010-10-29
Are you sure that no dust is getting in your fans? You should get a professional to open up your laptop and clean it, as often dust can cause the computer to overheat and cause problems, as well as impact performance.

---

### Post by matt_symes on 2010-10-29
Hi

What type of video? Flash etc ?

Kind regards

---

