---
title: "Slideshow screensaver?"
date: 2011-11-13
forum: General Help
---

### Post by fixerdave on 2011-11-13
I have what amounts to a media server (among other things) running lubuntu 10.10.  It's a PPC mini-mac and didn't like 11.10 so I back-peddled to what worked...  

Anyway, I have a very large collection of photos in a well-organised folder tree, some of which are specifically tagged.  I want a screensaver that will scan this tree, identify a particular tag, and display those images.  No fancy pan/fade/transition stuff.  Just show me the pictures.

I've searched and come up, well, annoyed.  I could import my photos into something like shotwell, but the old version I'm stuck with doesn't have a screensaver.  Gthumb, which I used to use, is now stuck in v2.11 no-slideshow limbo - between what worked great before and now works okay but I can't use with 10.10.

There has to be something that won't muck up my well-crafted photo archive and give a basic slideshow of specifically-tagged images.  I mean, I could write a perl script to do it... I just need to recurse the folder tree and make a list of all tagged images, then start displaying the list from a random point as a screensaver.  It can't be that hard.

I just find it hard to believe that it's not already done - it seems like such a basic thing to do.  I feel like I'm missing some really obvious app - but I can't find it.

Before I waste a bunch of time, can anyone point me in the right direction?

---

### Post by raja.genupula on 2011-11-13
may be this can help you 

[http://ubuntuforums.org/showthread.php?t=838456](http://ubuntuforums.org/showthread.php?t=838456)
[http://ubuntuforums.org/showthread.php?t=1534840](http://ubuntuforums.org/showthread.php?t=1534840)

---

### Post by hwttdz on 2011-11-13
You could use the glslideshow, the only catch is you need to have a directory which contains all the images which you want to show.  I'd assume glsideshow plays nice with links, so what I'd do is make a folder with no images in it, and run find on your pictures directory for those with the tag of interest, and then make links from the folder to the real image.  Space used will be negligible and it doesn't sound much harder than a well crafted find (exiftool might be helpful as well).  Good luck.

---

### Post by hansdown on 2011-11-13
Hi, fixerdave.

For 1010, try...

```
PhotoFilmStrip
```

It's in the repos.

---

### Post by fixerdave on 2011-11-13
> **hwttdz said:**
> ..., and then make links from the folder to the real image...

See... now that's why I asked.  My Windows background is showing through... I never think of using links.  What a perfectly simple solution.  Thank you!

---

