---
title: "Ways to increase the ventilation of my laptop"
date: 2010-09-19
forum: General Help
---

### Post by kolo-01 on 2010-09-19
Is there any way of cooling the CPU down by easily increasing the ventilation of my toshiba laptop, hardware or software fixes.. as my CPU heats up and runs at stupidly slow speeds when i do something like video flash and the internet is mainly what i use my computer for (no games) but this is a bit much for it. can i do something like alter the fan speed or anything?

---

### Post by mr_luksom on 2010-09-19
It may not be practical for you, but I have a deskbound laptop (cracked screen) that was having similar issues. After taking it apart and vacuuming the dust/lint out, I've put it on 'blocks' so the fan has less resistance (more airflow). Raising it by only 20mm has reduced the fan workload easily in half.

---

### Post by mike555 on 2010-09-19
There are fan controlling softwares ,like "speedfan" for Windows  or just point a small fan it it or buy one of those coolers they sell for that.

---

### Post by kolo-01 on 2010-09-19
> **mr_luksom said:**
> It may not be practical for you, but I have a deskbound laptop (cracked screen) that was having similar issues. After taking it apart and vacuuming the dust/lint out, I've put it on 'blocks' so the fan has less resistance (more airflow). Raising it by only 20mm has reduced the fan workload easily in half.

I thought about blocks, mine is usually on a book or other flat surface which is pretty bad for retaining heat. reducing by half is definitely worth it then, cheers

---

### Post by no2498 on 2010-09-20
install htop and see what is running to make it hot
just type htop in a terminal it tells you how to install it
type htop in a terminal
what is running ?

cheese has a nice help file look in its faq's

this is a cheese help file

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

### Post by efflandt on 2010-09-20
There are cooling devices that you can place under a laptop with fans, often powered by USB and with extra USB ports.

I have no issues at all with anything in Ubuntu for my older Satellite from 2006.  But many people with new Toshiba laptops seem to have power or heat issues.  So you might search for your model on the forums, or mention what specific model you have, and maybe someone would have suggestions.

---

