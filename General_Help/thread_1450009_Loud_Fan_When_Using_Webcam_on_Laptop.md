---
title: "Loud Fan When Using Webcam on Laptop"
date: 2010-04-08
forum: General Help
---

### Post by trentscott4 on 2010-04-08
I have an Hp pavilion dm3 laptop/netbook running 10.04 and have noticed that when the webcam is in use (e.g. on a skype call), there's a loud audible fan.  Does anyone know if this is a driver related issue?  Is it the fan on the graphics card most likely?  Inadequate cooling, should I get a cooling pad?

---

### Post by arloth on 2010-04-08
Nothing really wrong here.  The Webcam is using your CPU harder than a normal workload so the fans spin up while it's on.  

However, there are a few things you may want to check to possibly reduce the fan speed.  First off, is the system full of dust? Take a can of compressed air to the vents, you might be suprised. They can collect dust absurdly quick.

Secondly, video drivers can make a difference here as well, displaying webcam images takes some horsepower.  Figure out who makes the video card in your laptop, usually Nvidia or ATI and see if you've got the driver for it going.  Having proper 2D acceleration support will also make a difference in system load.  The easy way to do this is with the Restricted Drivers manager.

edit: oops! 10.04? aren't the restricted drivers for that still broken?  That's probably your problem.  Who makes your video card?

---

### Post by no2498 on 2010-04-08
DO NOT CHANGE THE FAN SPEED YOURSELF let the system do it

ok this comes from the cheese help faq's

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    




cheese has all the settings for the webcams now days 


this is easier to follow


open a terminal type,  gstreamer-properties click enter
click video set the plugin to, x windows system (no xv)

that is cheese

now if you have the new video player, smplayer it says to set it to, xv

try 1 or the other

hope this helps

---

### Post by trentscott4 on 2010-04-08
> 
Nothing really wrong here. The Webcam is using your CPU harder than a normal workload so the fans spin up while it's on. 

However, there are a few things you may want to check to possibly reduce the fan speed. First off, is the system full of dust? Take a can of compressed air to the vents, you might be suprised. They can collect dust absurdly quick.

Secondly, video drivers can make a difference here as well, displaying webcam images takes some horsepower. Figure out who makes the video card in your laptop, usually Nvidia or ATI and see if you've got the driver for it going. Having proper 2D acceleration support will also make a difference in system load. The easy way to do this is with the Restricted Drivers manager.

edit: oops! 10.04? aren't the restricted drivers for that still broken? That's probably your problem. Who makes your video card?


Thanks! It's ATI, would you recommend downgrading to 9.10 to resolve this or is there a way to resolve the Restricted Drivers issue in 10.04 Beta 2?
> **no2498 said:**
> DO NOT CHANGE THE FAN SPEED YOURSELF let the system do it

ok this comes from the cheese help faq's

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    




cheese has all the settings for the webcams now days 


this is easier to follow


open a terminal type,  gstreamer-properties click enter
click video set the plugin to, x windows system (no xv)

that is cheese

now if you have the new video player, smplayer it says to set it to, xv

try 1 or the other

hope this helps

Will this work with Skype?

---

### Post by no2498 on 2010-04-09
sorry i do not use skype
was only trying to help with the fan

---

