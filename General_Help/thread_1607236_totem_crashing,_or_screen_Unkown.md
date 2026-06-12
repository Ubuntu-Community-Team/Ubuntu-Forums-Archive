---
title: "totem crashing, or screen Unkown"
date: 2010-10-27
forum: General Help
---

### Post by grizato on 2010-10-27
I upgraded my PC from Jaunty to Maverick, and I've run into a complicated problem.

When I upgraded, and went to System > Preferences > Monitors (to change the screen resolution), it said Unknown as the screen name and I couldn't change the resolution, refresh rate, or rotation.

So, this morning I booted the computer into a terminal and ran:
[FONT=Courier New][SIZE=3]
Xorg -configure

cp xorg.conf.new /etc/X11/xorg.conf [/SIZE][/FONT]

I ran these commands from advice on one or two forum posts and my own experience. So now the monitor options are easily adjustable, but totem crashes when I open any .flv, or .avi file(I haven't tried any other formats). When I delete xorg.conf; the two problems swap over again.

I can't do with one or the other, because I obviously need to watch videos and on the other hand i like turning the resolution down to watch iplayer.

---

### Post by no2498 on 2010-10-27
put your xorg back

this is what i have done to fix totem
it comes from the cheese help faq's

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    



hope it helps you

---

### Post by grizato on 2010-10-27
Thanks for your help and quick reply. I followed your instructions and It didn't work. Back to square 1 ](*,)

---

