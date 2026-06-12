---
title: "xfishtank Anyone?"
date: 2009-09-06
forum: General Help
---

### Post by klausner on 2009-09-06
Has anyone ever figured out how to run xfishtank as the wallpaper on a Gnome desktop?

---

### Post by klausner on 2010-03-05
Belated BUMP!

---

### Post by klausner on 2010-03-13
Bump

---

### Post by tgalati4 on 2010-03-13
xfishtank has been around a long time.  My guess is that it doesn't have the proper hooks to plug into the gnome-screensaver framework.  I couldn't get xfishtank to work.  It appears that the gnome-screensaver writes over it immediately.  So, I have fish, I just can't see them.

I don't think you can shut off gnome-screensaver without breaking the desktop.

So, no fish for you, unfortunately.

There is shermans-aquarium.  It has a few issues:

[http://ubuntuforums.org/showthread.php?t=1187367&highlight=shermans+aquarium](http://ubuntuforums.org/showthread.php?t=1187367&highlight=shermans+aquarium)

---

### Post by klausner on 2010-03-13
> **tgalati4 said:**
> xfishtank has been around a long time.  My guess is that it doesn't have the proper hooks to plug into the gnome-screensaver framework.  I couldn't get xfishtank to work.  It appears that the gnome-screensaver writes over it immediately.  So, I have fish, I just can't see them.

I don't think you can shut off gnome-screensaver without breaking the desktop.

So, no fish for you, unfortunately.

I'm not trying to use it as a screensaver. I'd like to run it as wallpaper, which is how it was originally used. The trick is I need to somehow suppress Gnome's wallpaper, either graphic or plain color.

---

### Post by gmargo on 2010-03-14
Nautilus is interfering.  Open the gconf-editor and navigate to /apps/nautilus/preferences and uncheck "show_desktop".  Now xfishtank will work (tested on 9.10 Karmic Gnome.)

(Found through google on an old mailing list: [http://osdir.com/ml/gnome.general/2003-05/msg00056.html](http://osdir.com/ml/gnome.general/2003-05/msg00056.html)).

---

### Post by klausner on 2010-03-14
> **gmargo said:**
> Nautilus is interfering.  Open the gconf-editor and navigate to /apps/nautilus/preferences and uncheck "show_desktop".  Now xfishtank will work (tested on 9.10 Karmic Gnome.)

(Found through google on an old mailing list: [http://osdir.com/ml/gnome.general/2003-05/msg00056.html](http://osdir.com/ml/gnome.general/2003-05/msg00056.html)).

Wow! I knew I could get xfish running, but the system wallpaper always blocked it from view. Never knew it would be that simple to get it to show.

Thanks!

---

### Post by klausner on 2010-03-14
> **gmargo said:**
> Nautilus is interfering.  Open the gconf-editor and navigate to /apps/nautilus/preferences and uncheck "show_desktop".  Now xfishtank will work (tested on 9.10 Karmic Gnome.)

(Found through google on an old mailing list: [http://osdir.com/ml/gnome.general/2003-05/msg00056.html](http://osdir.com/ml/gnome.general/2003-05/msg00056.html)).

*Almost* perfect :( After playing with it for a bit, I realized that my desktop icons were buried. In older days you could use xfishtank as the bottom layer, and then have icons and such on top.

So I'm back to suspecting that the answer is to somehow supress the Gnome wallpaper.

Good try though.

---

### Post by klausner on 2010-04-08
Bump.

---

