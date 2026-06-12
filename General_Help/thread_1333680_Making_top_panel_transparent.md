---
title: "Making top panel transparent?"
date: 2009-11-21
forum: General Help
---

### Post by Cam! on 2009-11-21
Is there any way I can make the top panel be slightly transparent, like in Mac OS X?

---

### Post by Psycho.mario on 2009-11-21
Right click on it, click properties, then the Background tab, check the "Solid Colour" radio button, then change the slider as to your choice

---

### Post by Cam! on 2009-11-21
That only applies for the middle chunk of the bar. I was talking about keeping the same background (Mine's eGTK, so it's a gradient), and having the whole thing transparent.

---

### Post by Flying caveman on 2009-11-21
It depends on the theme you have installed.  It does that if your theme is supposed to have a certain color.  Some themes are more customisable and you can have your panel all transparent if you want.

---

### Post by OpSecShellshock on 2009-11-21
What you'll want to do is create an image file in an image editor (probably gimp) that is 24 pixels tall and [monitor resolution width] pixels wide. It should just be a rectangle. Make it transparent and then save it (mine is saved as a .png and scales just fine).  Remember the location of the file when you save it.  Right click the panel, select Properties. In the dialog, go to the Background tab. Click the radio button next to Image, browse to the location of the transparent rectangle, and select it. There you go.  The active window on the Window List panel application will still be gray, but everything else will be transparent. You'll need to tweak the font color in the gconf-editor to something that will stand out, and then you're good.

---

### Post by Earl_Maroon on 2011-01-16
There is a gconf setting you can use to make the entire panel transparent. I can't remember what it is though, unfortunately. Maybe you can find it with Google.

You can also add an entry to the Compiz opacity/brightness/saturation, which will make everything except the Menu applet (on the left) transparent. It's the next best. The object class for the panel is "dock" (no quotes).

---

