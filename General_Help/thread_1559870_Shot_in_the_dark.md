---
title: "Shot in the dark"
date: 2010-08-24
forum: General Help
---

### Post by jv2112 on 2010-08-24
I know this is the worst phrased question ever but.....


After most recent update (don't recall what was updated) the codecs playing video (Totem,VLC) seem choppy. 

Anybody experiencing that ? :confused:


Running Linux Mint 9 64 Bit.

---

### Post by inameiname on 2010-08-24
Perhaps as a way to see what was updated, so you may then figure out what was the culprit, do this in the terminal:

apt-history


It should give you details in the terminal of all that was done last. 

Other than that, I haven't noticed anything that made my Lucid's Totem choppy, and I use it all the time, as well as having updates installed always. Another interesting idea is to see if it's choppy in Mplayer or it's frontends, as Mplayer uses mencoder, not what Totem or VLC uses, I think. I've noticed when one has issues, the other doesn't. Helps me narrow down things when an issue arises.

What about 3rd party repositories....do you have any of those in your sources.list? Sometimes issues come with something downloaded from them. If you do, AND 'apt-history' gives you a readout of something, do this in the terminal just to see what versions and where the apps came from so you can further figure things out:

sudo apt-cache policy (whatever the package might be)

Other than that, I'm not sure what to tell you.

---

### Post by no2498 on 2010-08-24
this comes from the cheese help files faq's
it worked for me
wright down your setting first so you can set it back if needed

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


hope it helps you

---

### Post by jv2112 on 2010-08-24
no2498 ,

Dead on !!

Thanks a lot !!:guitar:

---

### Post by no2498 on 2010-08-25
your welcome glad it helped you

---

