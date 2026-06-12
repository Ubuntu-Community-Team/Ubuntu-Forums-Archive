---
title: "Resolution"
date: 2011-08-05
forum: General Help
---

### Post by nankura on 2011-08-05
Hey guys

i have a nice 19" LCD Samsung Syncmaster 172x Monitor with a GTX 460 Nvidia graphics card, ofcourse im on the latest drivers from X Updates, version 280

Now in the nvidia control panel. i have 1280x1024x75 set, for 75Hz refresh rate and im not sure if its running at that, because i cant tell the looks/feel difference, but thats set like that

But when i go to the XFCE settings menu > display, it only shows 50 to 51 to 52 Refresh rates, now ive tried additions to the xorg.conf and checking my vertical/horiz refresh settings and changing them to the monitor's capabilitys but that didnt work

though on 1024x768 i can get 65, but that resolution is fugly

so im curious how to get that to show 60-75Hertz

---

### Post by realzippy on 2011-08-05
You should run your monitor at it 's panel's native resolution to get the best image quality.
Use the nvidia-settings tool for resolution and refresh rate.
..the gnome "Monitors" tool simply is lying (when using the nvidia-driver) about the reported refresh rate (50 Hz) as xrandr also does.
See:
[http://ubuntuforums.org/showpost.php?p=11107756&postcount=71](http://ubuntuforums.org/showpost.php?p=11107756&postcount=71)


..btw,there are a few discussions about running a LCD panel about 60 Hz in the web.
[Wiki]("http://en.wikipedia.org/wiki/Refresh_rate"):
[I]However, this does not apply to LCD monitors. The closest equivalent to a refresh rate on an LCD monitor is its frame rate, which is often locked at 60 frame/s. But this is rarely a problem, because the only part of an LCD monitor that could produce CRT-like flicker&#8212;its backlight&#8212;typically operates at around 200 Hz.
[/I]

---

### Post by nankura on 2011-08-05
thankyou that guide fixed it ^^

---

### Post by realzippy on 2011-08-05
Fine...please set thread as solved (threadtools)

---

