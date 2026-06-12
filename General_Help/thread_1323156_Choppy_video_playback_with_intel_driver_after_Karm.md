---
title: "Choppy video playback with intel driver after Karmic upgrade"
date: 2009-11-11
forum: General Help
---

### Post by fivenote on 2009-11-11
I'm using the intel video driver and upgraded from 9.04 to 9.10. 

Despite Jaunty's intel video problems ([http://ubuntuforums.org/showthread.php?t=1130582&highlight=intel+video+choppy](http://ubuntuforums.org/showthread.php?t=1130582&highlight=intel+video+choppy)), video playback was quite smooth after using fixed-up versions from the the x-swat ppa.

But after upgrading to 9.10, video playback is choppy when there's significant horizontal motion. It's not tearing, but short, quick pauses in the video playback.

I tried applying the xorg.conf options from the above thread, but these should all be defaults now (uxa accelleration, etc...) and make no difference when I do apply them.

Anybody share this problem or know what can be done to correct?

---

### Post by fivenote on 2009-11-16
I think I found a solution for the problem I'm seeing...

[http://linux.digitalsp.com/2009/08/improving-stuttering-during-flash-video.html]("http://linux.digitalsp.com/2009/08/improving-stuttering-during-flash-video.html")

I observed the problem not only with flash, but also mythtv, mplayer, vlc, and totem.

To test this I added the "CPU Frequency Scaling Monitor" to the gnome panel for each of my 2 2.0GHZ processors. If I force the CPUs to 1.0GHZ, the stuttering and choppiness becomes very pronounced. By default, it's set to "ondemand". The processors scale up as needed, but when playing video it's a case of "too little too late" and I think the scaling didn't happen until the CPUs were being pushed hard by the HD video playback. 

The fix described in the above link lowers the threshold at which the scale-up takes place. It suggests 40%. I may go lower, maybe 25-30%.

I Hope this helps others seeing the same problem.

---

### Post by kozjegyzo on 2009-12-28
The above fix didn't help. I'm still seeing the same choppy video in all sources and all players. I hope someone comes up with a fix...

---

### Post by jbeamz on 2010-08-04
Thanks! It solved my video issue perfectly, AMD 32bit 2.4ghz Karmic fyi.

---

### Post by no2498 on 2010-08-05
see if this helps it comes from the cheese help faq's

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

