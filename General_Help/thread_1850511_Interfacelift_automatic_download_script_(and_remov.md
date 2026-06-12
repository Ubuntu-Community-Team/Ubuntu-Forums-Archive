---
title: "Interfacelift automatic download script (and removal after ... )"
date: 2011-09-26
forum: General Help
---

### Post by Boulemans on 2011-09-26
Hi all,

I'm trying to get a hand on the python scripting. I would like to have a program script with following features:

1) runs at startup (menu 'startup programs')
2) downloads any new images from interfacelift with the right resolution. (no old images already downloaded or from a long time ago)
3) deletes the oldest images when (whatever is most easy to program)
   a - the target map exceeds a predefined number of images
   b - the image is older then ... days 

Could someone help me on the way? I've found some python scripts, but they only download all images. My point would be that the wallpapermap content would rotate through time, not just get new images.

For example, I've found the next code from [this blog]("http://chasingdragon.wordpress.com/2011/02/21/interfacelift-download-script/")
```
#!/bin/bash
 for i in {1..$1}
 do
 wget --user-agent="Firefox" -q -O - http://interfacelift.com/wallpaper_beta/downloads/date/widescreen/1920x1080/index$i.html | perl -ne 'if (m#/wallpaper_beta/grab/(\w+.jpg)#) { print qq#wget --user-agent="Firefox" --referer=http://interfacelift.com/ http://interfacelift.com/wallpaper_beta/grab/0$1\n#} ;' | sh -x
 sleep 1
 done
```

furthermore, is it possible to adjust to eg. opera/chrome browser? And, most important: is the above script 'decent'? I mean: does it break any esthetically programming rules?

---

