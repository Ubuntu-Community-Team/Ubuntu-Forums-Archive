---
title: "SM Player advantages"
date: 2010-09-30
forum: General Help
---

### Post by FahadMKS on 2010-09-30
Is there any advantages for Smplayer compared to the Movie player which comes with Ubuntu by default.
If so, please let me know so that I can keep it/uninstall from my computer.

---

### Post by endotherm on 2010-09-30
I really like SMplayer, as it is a nice frontend, and uses mplayer as it's backend. mplayer seems to be able to deal with high-res stuff better than gstreamer (the backend for the Totem Movie Player).

I see all the video players as having their ups and downs:

Totem: best integrated into the OS, simple to use, with suficcient features. won't play everything however, and has some trouble with highres/bitrate content (varies by codecs used). sometimes stutters or lags on 1080p content

VLC: will play anything, no external codecs needed. if vlc won't play it, likely hood is nothing can. VLC however does a terrible job with picture rendering under certian circumstances. dithering is especially bad, so if you are looking at a very dark scene, the darkenss will look really bad. also it has trouble making dramatic changes (a rapid scene switch from night to day for instance) may cause the picture to become color inverted, and then a green blooby mess. also may have issues with highres/bitrate content.

Mplayer/SMPlayer:
Great backend decoder, wide availability of codecs, and well supported. the only problem with it is that the ubuntu repo maintainers often mix the wrong versions of mplayer and smplayer, or simply fail to update it on any kind of regular basis, so the repo version is usually problematic. I install them from the RVM PPA repos. just search online for "smplayer ppa" and "mplayer PPA". 


hope that helps

---

### Post by FahadMKS on 2010-09-30
So, I do not have to Uninstall the SM player. RIght.

Thank you man

---

