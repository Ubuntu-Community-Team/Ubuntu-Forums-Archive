---
title: "Hey, where did my subpixel font rendering go?"
date: 2010-10-12
forum: General Help
---

### Post by Quicksand on 2010-10-12
Maybe this is somehow related to the frequently-discussed nvidia performance regression that showed up prior to release, I don't know, but for some reason I'm not getting ANY subpixel font rendering right now.  (Well, ALMOST none, but more on that in a minute.)

I'm running 10.10 final (fully updated as of now), 64-bit, with the current version of the nvidia proprietary driver (260.19.06-0ubuntu1).

In Appearance Preferences, there is no difference whatsoever when I switch between "Grayscale" and "Subpixel" smoothing.  It's all grayscale, blotchy and blurry.  If I toggle between "None" and "Grayscale," or try the different hinting options, I can clearly see changes occurring.  But for whatever reason, there is NO effect when changing to Subpixel smoothing.  Strange!

This used to work, and now it doesn't.

But here are the exceptions:

Firefox is smoothed, and looks good -- it must be getting its settings from somewhere else.

And QT apps look great too.  Thanks to a .fonts.conf file I set up, the text in those looks fantastic.  Rendering there is absolutely 100% correct.

But GTK/Gnome apps just don't look good.

Lucid and prior versions looked great!  This appears to be a regression following my upgrade to Maverick.

Any thoughts?

---

