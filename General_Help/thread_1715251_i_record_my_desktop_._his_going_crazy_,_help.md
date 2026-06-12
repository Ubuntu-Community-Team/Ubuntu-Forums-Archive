---
title: "i record my desktop . his going crazy , help"
date: 2011-03-26
forum: General Help
---

### Post by dara jihan on 2011-03-26
hello every one

when i record my desktop with desktop recorder (recordmydesktop) software it's going crazy :(  i don't know why . 

i recorded my desktop to show you how is it . 

format video is .ovg 

video size 900 kb  

pleas download it to see it 

[http://www.kurdmoon.com/up//uploads/files/kurd-moon12fd461d6f.ogv]("http://www.kurdmoon.com/up//uploads/files/kurd-moon12fd461d6f.ogv")

thanks to all

---

### Post by dara jihan on 2011-03-27
pleas help

---

### Post by HermanAB on 2011-03-27
Yeah well, recording your desktop is an almost trivial one liner with LibAV ffmpeg:
ffmpeg -an -s 1200x900 -r 25 -f x11grab -i :0.0 \
 -s 1200x900 -r 25 -vcodec libxvid \
 -aspect 1.3333 -sameq mydesktop.avi

...or you can use any number of complicated GUI programs with varying degrees of success.

---

### Post by FakeOutdoorsman on 2011-03-27
> **dara jihan said:**
> pleas help
Does it work normally if desktop effects/Compiz are turned off? What video card do you have?

> **HermanAB said:**
> Yeah well, recording your desktop is an almost trivial one liner with LibAV ffmpeg:
ffmpeg -an -s 1200x900 -r 25 -f x11grab -i :0.0 \
 -s 1200x900 -r 25 -vcodec libxvid \
 -aspect 1.3333 -sameq mydesktop.avi

...or you can use any number of complicated GUI programs with varying degrees of success.
Why suggest libav? It's not in the repos.

You'll probably get better performance and possibly a nicer looking output with this guide:

[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026)

---

### Post by dara jihan on 2011-04-20
***_Does it work normally if desktop effects/Compiz are turned off? What video card do you have?_***
thanks all 
but what can i do , i want record my screen bot it go wrong 

thanks all

---

