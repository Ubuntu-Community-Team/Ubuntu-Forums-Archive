---
title: "I want my &quot;wallpaper&quot; back"
date: 2010-05-27
forum: General Help
---

### Post by mbeierl on 2010-05-27
There used to be a gnome setting for wallpaper pictures, simply called "wallpaper" (vs. scaled, span, center, etc) which would start the display of the image at 0,0 (upper, left corner)

I had a wonderful script that used montage to blend two images into a single image that I could then cause to be displayed across both my monitors as if there were a different image per monitor.

This appears to be gone.  None of the image settings for background that I have come across allow me to force the upper left corner of the image to align with the upper left corner of the desktop, and then display the remainder of the picture unscaled.

Help?

I really would like my different picture per monitor feature back  :(

---

### Post by ibuclaw on 2010-05-27
> **mbeierl said:**
> There used to be a gnome setting for wallpaper pictures, simply called "wallpaper" (vs. scaled, span, center, etc) which would start the display of the image at 0,0 (upper, left corner)

I had a wonderful script that used montage to blend two images into a single image that I could then cause to be displayed across both my monitors as if there were a different image per monitor.

This appears to be gone.  None of the image settings for background that I have come across allow me to force the upper left corner of the image to align with the upper left corner of the desktop, and then display the remainder of the picture unscaled.

Help?

I really would like my different picture per monitor feature back  :(

Hi.

The style '**Tile**' should give the exact effect you want.

And if you aren't convinced, open up gconf-editor, and browse to
```
/desktop/gnome/background/picture_options
```

Regards
Iain

---

### Post by mbeierl on 2010-05-27
tile: close, but not quite.  It tiles within the single monitor, effectively scaling the picture down to the dimensions of the one monitor and repeating the same image on the second monitor.

---

### Post by mbeierl on 2010-05-31
Tile still tiles within the single monitor, not across both.  Is there no way to restore the original behaviour?

---

### Post by mbeierl on 2010-08-05
Still have not determined any method of re-enabling the original behaviour of a single jpeg image spanning both monitors without scaling.  Too bad, as my wallpaper was a thing of envy amongst the MS users at work.  They could never figure out how I did that.

Guess it's a lost feature of the desktop.  Too bad :(

---

### Post by QIII on 2010-08-05
I may have some time to experiment when I get home, but I think you still may be able to do that with Compiz.  You can set parameters for each monitor such as cube rotation, etc.  You may be able to set backgrounds independently as well.

If I have a chance, I'll putter around.

---

### Post by mbeierl on 2010-08-05
I use compiz, so that would be great.  I've done a bit of poking around with the compiz wallpaper but it seemed to behave differently than what I wanted (ie: setting paper per cube side, which then comsumed a large amount of video memory) but that was 2-3 releases ago.  It also seemed to conflict with Gnome as to who wins in drawing the desktop.

Thanks in advance for anything you can drum up!

---

