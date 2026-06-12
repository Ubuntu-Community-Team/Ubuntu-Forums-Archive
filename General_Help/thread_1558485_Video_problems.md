---
title: "Video problems"
date: 2010-08-22
forum: General Help
---

### Post by Kajmak on 2010-08-22
Hello. I'm having problems with video files, when i try to watch them on VLC player or Movie player or any other software, its spoiling my picture, colors are fuzzy, it is like, gray color is shown as yellow, white as blue and stuff like that. 
Any suggestions how to solve that?

---

### Post by Kajmak on 2010-08-22
Bump!

---

### Post by no2498 on 2010-08-22
open totem click edit preference video move the sliders some then try reset to default

should help you

---

### Post by Kajmak on 2010-08-22
Hmm, it doesn't seems to be working. I realized if i restart my computer and start movie after that, the picture will be ok, but if i play some song via VLC or some other movie player, it all gets spoiled and fuzzy.

---

### Post by partloer on 2010-08-22
Hi Kajmak,

I would check to see if there are any hardware drivers for your video card.  This can be done by going to System->Administration->Hardware Drivers.  If there are none you can search and post up your systems hardware and see if other people are having similar problems.

---

### Post by no2498 on 2010-08-22
this comes from the cheese help file faq's

it may or may not help you wright down what it is set to so you can set it back if need to

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

---

### Post by blackmail on 2010-08-22
Try to edit the video rendering thing... Go to VLC and see the video options, there should be something, When i get home from work I will check on my PC and tell you exactly, just posted this if you figure it out in the mean time. Also please check your video drivers, If you are the happy owner of an nVidia or ATI V-card install Envy and pls install the drivers with the help of Envy.

---

### Post by Kajmak on 2010-08-22
Success! Seems like Partloer's proposition was working, it was set up on the wrong driver, (not on the recommended one). I'm sorry that i made all this fuzz about a simple problem as it seems now , but I'm new to the ubuntu.
Thanks again guys for your help and effort!

---

