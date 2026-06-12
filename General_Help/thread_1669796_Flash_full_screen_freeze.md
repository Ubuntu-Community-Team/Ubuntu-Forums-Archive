---
title: "Flash full screen freeze"
date: 2011-01-18
forum: General Help
---

### Post by Hippytaff on 2011-01-18
I've seen a number of post for this, but none work, does anyone know of a fix. Whenever a streaming flash video (you tube etc) is toggled to full screen the picture freezes. The sound doesn't. It's not a driver issue as video from DVD works fine.
 
Any ideas greatly appreciated, no fix I've found on the forums works.
 
Cheers

---

### Post by praveenthivari on 2011-01-18
Have the same problem here. Didn't get fix for tht though

---

### Post by Hippytaff on 2011-01-18
This seems to be an ongoing issue - a shame when the natty is going to be using unity targeted at users new to linux, and with an aim to be more inuative, and a simple full screen funcionality doesn't work for streaming (Devs - ;-) )
 
I don't even think there is a bug registered for this is there?

---

### Post by Taijitu on 2011-01-18
My maverick installation plays full screen flash fine (well, not fine... Laggy, but it plays...), using nvidias's graphics drivers.

What version of the flash player are you using?

---

### Post by Hippytaff on 2011-01-18
> **Taijitu said:**
> My maverick installation plays full screen flash fine (well, not fine... Laggy, but it plays...), using nvidias's graphics drivers.
 
What version of the flash player are you using?
 
The Latest one 10xxx the exact version I can't check right now, in work....Also a mate of mine has the same issue using Nvidia. odd

---

### Post by pl@yer on 2011-01-18
If you are not arlready, I would use adobe's flash player. Just grab the tarball (.tar.gz) from here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) 

from the download dir:
```

tar -zxf install_flash_player_10_linux.tar.gz
[ -d ~/.mozilla/plugins/ ]||mkdir ~/.mozilla/plugins;cp libflashplayer.so ~/.mozilla/plugins/

```

---

### Post by Hippytaff on 2011-01-19
I am already using Adobe Flash ;-)
 
Reinstalled it - no luck, my mate had better luck with mint 10 though. odd

---

### Post by Jack432130 on 2011-01-19
[SIZE=6][SIZE=4]When I tried to watch a full screen flash video, I got a flash crashed error message in Ubuntu 10.04 and adobe 10.0. When watching a small flash video, I right clicked on properties, then unchecked hardware acceleration. This solved the problem for me. Full screen videos now work, although a little choppy.:p[/SIZE]
[/SIZE]

---

### Post by Hippytaff on 2011-01-20
Thanks for that, I've tried this though and numerous other 'fixes' with no success...mint 10 works fine though ;-)

---

### Post by Hippytaff on 2011-01-20
Double post

---

### Post by Hippytaff on 2011-02-04
[This]("http://www.linuxjournal.com/content/flashvideoreplacer-continues-improve?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+linuxjournalcom+%28Linux+Journal+-+The+Original+Magazine+of+the+Linux+Community%29") is an article about [FlashVidoeRplacer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/") which looks to be looks like a promising alternative to flash that will allow full screen without being rubbish for anyone having this issue too. I haven't tried it yet though :?

---

