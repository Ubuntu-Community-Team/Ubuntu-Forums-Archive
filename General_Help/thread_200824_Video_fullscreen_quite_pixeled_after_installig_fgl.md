---
title: "Video fullscreen quite pixeled after installig fglrx drivers."
date: 2006-06-20
forum: General Help
---

### Post by Cerealz on 2006-06-20
Hey,
I have this major problem in dapper 6.06 ... i installed the fglrx drivers ..and everything is fine..except.. when i fullscreen videos (totem..vlc..etc).
In window mode the movie its fine..but when it gets fullscreen.. it gets all "pixelise".. quality down.. 
If i change the driver on xorg.conf to "ati".. the fullscreen gets fine.. but with fglrx..i get this problem..
Does anyone know how can i get this right?
Tks..

---

### Post by Cerealz on 2006-06-26
no one did get this problem??:-?

---

### Post by Anduu on 2006-06-26
With mplayer and vlc you can select different video outputs...try some different ones.

---

### Post by kanem on 2006-08-01
> **Anduu said:**
> With mplayer and vlc you can select different video outputs...try some different ones.
Yes. I had this problem, but setting VLC to use openGL video output fixed it.

---

### Post by bender888 on 2006-08-01
Add this to Device section of /etc/X11/xorg.conf

Option "VideoOverlay" "on"

Hope this fixes your problem.

---

