---
title: "WGet Help"
date: 2009-12-04
forum: General Help
---

### Post by mylesmadness on 2009-12-04
Why does this download Broken files?
```
wget --referer=http://interfacelift.com/ -i images.txt
```Heres just a couple lines from images.txt, there is over 1800
> http://interfacelift.com/wallpaper_beta/dl/00004_trueaquablue_1280x800.jpg
http://interfacelift.com/wallpaper_beta/dl/00006_smiley2_1280x800.jpg
http://interfacelift.com/wallpaper_beta/dl/00007_bluesky_1280x800.jpg
http://interfacelift.com/wallpaper_beta/dl/00010_waxinggibbousmoon_1280x800.jpg
http://interfacelift.com/wallpaper_beta/dl/00016_windcatchers_1280x800.jpg
http://interfacelift.com/wallpaper_beta/dl/00019_learningtheropes_1280x800.jpg
http://interfacelift.com/wallpaper_beta/dl/00020_blueblocks_1280x800.jpg
http://interfacelift.com/wallpaper_beta/dl/00022_stamfordcone_1280x800.jpg
http://interfacelift.com/wallpaper_beta/dl/00023_seasidegranite_1280x800.jpg
http://interfacelift.com/wallpaper_beta/dl/00024_haitianchurch_1280x800.jpg

---

### Post by andrew.46 on 2009-12-05
Hi mylesmadness,

Looks like this site blocks wget which is actually not all that uncommon, but the following seems to work well enough:

```
wget --user-agent='Firefox/3.0.3' -i images.txt
```

But just have a look at the site's terms of use to see if there is a problem mass downloading in this way...

All the best,

Andrew

---

### Post by mylesmadness on 2009-12-06
Thanks,

That worked perfectly. And it makes sense that they would cut off people mass downloading there images.

---

### Post by andrew.46 on 2009-12-07
Hi mylesmadness,

> **mylesmadness said:**
> That worked perfectly.

Excellent news :). You may be interested to know that you can make this a more permanent setting by placing it in a $HOME/.wgetrc file.

All the best,

Andrew

---

