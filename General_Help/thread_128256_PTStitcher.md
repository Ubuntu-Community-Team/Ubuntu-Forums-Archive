---
title: "PTStitcher"
date: 2006-02-11
forum: General Help
---

### Post by cotcot on 2006-02-11
I am still trying to use hugin. It runs when i select the control point (autopanog.exe does not work to make them automatic)  myself and when i use nona as stitcher.

What package supplies PTStitcher.exe. I would expect libpano12 where i got PTOptimizer from but i do not have PTStitcher.

---

### Post by curley_sue on 2007-09-18
> **cotcot said:**
> I am still trying to use hugin. It runs when i select the control point (autopanog.exe does not work to make them automatic)  myself and when i use nona as stitcher.

What package supplies PTStitcher.exe. I would expect libpano12 where i got PTOptimizer from but i do not have PTStitcher.

as for the automatic control point it seems to be an error in the installation defaults on ubuntu. in hugin go to:
File -> Preferences -> Autopano 
erase the ".exe" part (leave only "autopanog")
you obviously have to have autopano installed to use it...

as for the rest - I am having difficulties myself (this is how I got to your post... ;-) )

---

### Post by curley_sue on 2007-09-18
> **cotcot said:**
> 
What package supplies PTStitcher.exe. I would expect libpano12 where i got PTOptimizer from but i do not have PTStitcher.

as far I as i understand PTStitcher is not in the packages of the ubuntu repos. the only solution I have found by now is either use nona as the engine or change the prefererences (as in my previous post):


File -> Preferences -> Panotools

tick the "use alternative..." box.
enter "PTmender" instead of "PTStitcher"

u might want to have a look at
[http://gentoo-wiki.com/HOWTO_Panorama_photography_tools]("http://gentoo-wiki.com/HOWTO_Panorama_photography_tools")

good luck!

---

