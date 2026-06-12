---
title: "Way to measure GPU utilisation/loading?"
date: 2010-11-06
forum: General Help
---

### Post by DanH860 on 2010-11-06
Hi,

Is there a utility or command to show how 'hard' the GPU is working? 

I have a Radeon 2600xt and I'm sometimes getting jerky playback when playing HD content. After trying various drivers and players, including VLC, I've had no joy but from reading an old thread, some people seem to have an issue with the CPU taking on all the work and not offloading this to the GPU.

I wanted to try and play a movie whilst monitoring how the GPU was performing, so at least I might get some idea as to why I was getting poor playback.

Thanks,
Dan

---

### Post by oldfred on 2010-11-06
If you right click on the top panel you can add a system monitor applet. I have two cpus and it does not really show each.

You could open system monitor in another workspace (bottom right) and easily switch back and forth.

---

### Post by no2498 on 2010-11-07
you may try this it comes from cheese help faq's

5.1 should help you if on a pc 5.2 if on a mac

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    
5.2.&#8195;I have a Mac with iSight and a ATI graphics card, and the colors are weird.


      This is a problem with the ATI graphics card, though there is a work around.
      Change the video-output to custom and insert the following: "ffmpegcolorspace !
      video/x-raw-yuv,format=(fourcc)YV12 ! ffmpegcolorspace ! xvimagesink".
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and select custom from the drop down menu.
    


you cam also change it in the system/preference multimedia systems selector

and if i remember right you need to restart the computer to see it work

---

