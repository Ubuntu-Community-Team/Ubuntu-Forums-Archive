---
title: "Why does my VLC look so bad? :)"
date: 2006-03-08
forum: General Help
---

### Post by Phixion on 2006-03-08
Hi there, I downloaded VLC and it looks like some Windows 3.1 program... I know it didn't look this bad before so I'm wondering what I need to change to fix it.

I also seem to be getting "stuttering" sound when playing MP3s and using GNOME, the sounds fine until I use a sound within GNOME (like clicking through the menu) then it seems to make the sound stutter.

Any help appreciated, alot! :)

Thanks

---

### Post by Lord Illidan on 2006-03-08
[quote=Phixion]Hi there, I downloaded VLC and it looks like some Windows 3.1 program... I know it didn't look this bad before so I'm wondering what I need to change to fix it.

I also seem to be getting "stuttering" sound when playing MP3s and using GNOME, the sounds fine until I use a sound within GNOME (like clicking through the menu) then it seems to make the sound stutter.

Any help appreciated, alot! :)

Thanks[/quote]

VLC in Dapper gets much improved, so stick around, and you will have it looking like any normal GTK 2 program, better than Xine, and Mplayer, and as good as Totem, if not better.

I tend to disable these ambient sounds, like menus, etc. One thing might be to enable dma.

First check if it is disabled : ```
sudo hdparm /dev/hd*
``` and post output here.

---

### Post by Phixion on 2006-03-08
Thanks for the quick reply, this is my 2nd install of Ubuntu and I'm 100% sure that VLC never looked like this... it looked like any other GNOME program.

Heres the output btw:

```
/dev/hda:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
```

---

### Post by kaamos on 2006-03-08
Vlc was packaged like that for breezy.. I have .deb of Vlc with gtk2 somewhere, could upload it if you want.

EDIT: better yet, already had it on a server -> [http://tinyurl.com/fwvh9](http://tinyurl.com/fwvh9)

---

### Post by public_void on 2006-03-08
vlc can have skins ([link](http://www.videolan.org/vlc/skins.html)), but I don't think theres many. Launch as vlc -I skins2. I think it starts with a default skin which you can change. TBH I prefer the simple UI anyway.

---

### Post by engla on 2006-03-08
Each and everyone here has their own solution ;-)

I enabled the breezy-backports repository (for more information, see the backports forum here on ubuntuforums.org)

I installed **wxvlc** and it's dependencies -- now vlc looks great.

---

### Post by ice60 on 2006-03-08
i use the skins too :cool:

[img]http://img332.imageshack.us/img332/61/vlc5ve.png[/img]

---

### Post by diskotek on 2007-09-30
how you can make new skin as default?

---

