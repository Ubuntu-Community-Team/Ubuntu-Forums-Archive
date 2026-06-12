---
title: "DGP becomes Noisy"
date: 2010-12-13
forum: General Help
---

### Post by hyfanious on 2010-12-13
Hi
I converted some of my AVI movies to DPG by dpgconv
but their sounds become noisy!
what should I do?
tnx.

---

### Post by regor210 on 2011-03-27
If your avi's are good I don't know what might be wrong, here's my notes on the way I convert to dpg. 

-------------------------------
#Converts vids to avi
$ ffmpeg -i name.flv name.avi
$ ffmpeg -i name.mkv  name.avi
--------------------------------------------------
#makes widescreen vids fit ds
$ ffmpeg -i name.avi -s 320x180 -padtop 30 -padbottom 30 new-name.avi
---------------------------------------------------
#This way is 4 times faster + works much better, power off save state & F>F>.
#You need to put mpeg_stat in usr/bin

$ python dpgconv-10.py name.avi

[http://theli.is-a-geek.org/blog/static/dpgconv](http://theli.is-a-geek.org/blog/static/dpgconv)
[http://rpmfind.net/linux/rpm2html/search.php?query=mpeg-stat](http://rpmfind.net/linux/rpm2html/search.php?query=mpeg-stat)
------------------------------------------------------------
#old way no mpeg_stat needed 
$ python dpgconv-0.3.py name.avi

# update not needed in 10.10
#needed to put an unstripped ffmpeg in usr/bin #for codec.
[http://www.ffmpeg.org/download.html](http://www.ffmpeg.org/download.html)
----------------------------------------



Better late then never?

---

