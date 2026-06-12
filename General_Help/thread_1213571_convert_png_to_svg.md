---
title: "convert png to svg??"
date: 2009-07-15
forum: General Help
---

### Post by abhilashm86 on 2009-07-15
is there any method of converting png image to svg, if we do so, will the generated svg image will have same resolution?? how can i convert??

---

### Post by alphacrucis2 on 2009-07-15
> **abhilashm86 said:**
> is there any method of converting png image to svg, if we do so, will the generated svg image will have same resolution?? how can i convert??

I don't know but I would guess that software to do that would be quite tricky as you are converting from what is essentially an image to a line drawing. Going the other way is of course easy.

Found this site by googling:

[http://vectormagic.com/home]("http://vectormagic.com/home")

---

### Post by alphacrucis2 on 2009-07-15
> **alphacrucis2 said:**
> I don't know but I would guess that software to do that would be quite tricky as you are converting from what is essentially an image to a line drawing. Going the other way is of course easy.

Found this site by googling:

[http://vectormagic.com/home]("http://vectormagic.com/home")

Found an open source possibility:

[http://potrace.sourceforge.net/#description](http://potrace.sourceforge.net/#description)

Even better I see potrace and potracegui are in the repo's

---

### Post by Tux Aubrey on 2009-07-15
For one-off conversions, you can load a png into Inkscape and use the Path>Trace Bitmap function.  You have a range of options re line rendering, colors etc.

Milage will vary. It is great for line drawings but photos stink - I do find it greatly helps to do a thorough cleanup of the image first in GIMP - especially fuzzy edges and blends/bleeds.  Even posterizing complex png images first can make the svg more acceptable.

---

### Post by abhilashm86 on 2009-07-15
i'd lot of component widgets in .png, so wanted to convert them, i got a overview, i'll try with gimp and that software, i'd also try searching direct .svg files, as those are basic widgets, maybe i'll find them!!

---

