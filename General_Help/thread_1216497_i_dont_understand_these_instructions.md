---
title: "i dont understand these instructions"
date: 2009-07-18
forum: General Help
---

### Post by mr_gourami on 2009-07-18
i just reinstalled a clean version of linux in attempt to get sound working right. i have a creative live soundblaster card. and only time i got it semi working in 5.1 was when i "think" i reinstalled alsa drivers. but i dont understand these directions...

[http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106)

i think this is what i need to do to get the 5.1 working. 

but what is Hg or NB? i try the codes but my terminal doesnt like it. what is a kernal? 

i tried last time the 
"""
    gedit .asoundrc

(You can use vi or nano to edit it if you don't have gedit).

Then add the following:

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}
"""
and that did not work...

---

### Post by NightwishFan on 2009-07-18
I think you can get 5.1 sound in pulseaudio.

Ubuntu Community sound documentation:

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by mr_gourami on 2009-07-18
no those didnt do anything. on the guide you provided i had to stop as the guide talked about codecs listed. that is not mentioned in my config files. so i dont know what to do. i have 2.0 sound. creative live sound card ca0106... no idea how to get 5.1

---

