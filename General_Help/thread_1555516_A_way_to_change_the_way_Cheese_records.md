---
title: "A way to change the way Cheese records"
date: 2010-08-18
forum: General Help
---

### Post by psycho5 on 2010-08-18
Hi,

Is there a way to change the way Cheese records videos? I read from the Cheese help manual that if the video is choppy, one can change the recording mode so that instead of the CPU doing all the work, the video card does it. 

The way they ask to change it: 

```

You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.
    

```

but for my netbook, i don't have such an option when I open gstreamer-properties. Is this because of the netbook's graphic card is not that hefty? Or am I missing something the way to make it smoother? 

I am using a HP Mini 200-1003TU with an intel graphics chipset.

---

### Post by no2498 on 2010-08-18
look in the add/remove program see if you have these installed

gstreamer, good, bad, ugly, and 10 installed

---

### Post by psycho5 on 2010-08-19
yeap they are all installed.

---

### Post by no2498 on 2010-08-19
this program works best for me wxcam it may help you
2 computers 1 804 the other lucid 10.04 i think
works good on both  

read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

### Post by h2sammo on 2011-02-05
> **psycho5 said:**
> Hi,

Is there a way to change the way Cheese records videos? I read from the Cheese help manual that if the video is choppy, one can change the recording mode so that instead of the CPU doing all the work, the video card does it. 

The way they ask to change it: 

```

You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    
      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.
    

```

but for my netbook, i don't have such an option when I open gstreamer-properties. Is this because of the netbook's graphic card is not that hefty? Or am I missing something the way to make it smoother? 

I am using a HP Mini 200-1003TU with an intel graphics chipset.

where is this cheese tutorial given? i would like to try it

---

### Post by psycho5 on 2011-02-05
You just start up cheese and go to Help or Preferences from the menu. Under video.

---

### Post by no2498 on 2011-02-05
you have every thing you need
or its in the cheese FAQ'S

open a terminal type gstreamer-properties click enter
click video
change the top plgin
click the bottom test button

---

### Post by coldraven on 2011-02-06
Have a look at guvcview, it has lots of things to fiddle with and it's in the Software Centre :p

---

