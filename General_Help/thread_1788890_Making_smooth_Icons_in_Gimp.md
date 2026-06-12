---
title: "Making smooth Icons in Gimp"
date: 2011-06-23
forum: General Help
---

### Post by CrusaderAD on 2011-06-23
How do I achieve this? I know how to get the design and everything working... but if I add some rounded corners for instance... the pixels stick out and look horrible. Any advice? Maybe a higher resolution?

---

### Post by Vaphell on 2011-06-23
care to show any example of the problem? what is the target size of the icon?

---

### Post by CrusaderAD on 2011-06-23
Sure. See the attached picture. The inside corners get grainy. Any tips?

---

### Post by SeijiSensei on 2011-06-23
What if you use a transparent background?

---

### Post by CrusaderAD on 2011-06-23
I think I figured it out... start big, like 250x250px... do your work then resize to 75x75px for a much smoother effect. Works great.

---

### Post by Vaphell on 2011-06-23
if it's going to be an icon full of clean geometric shapes, consider working with vector graphics.
in case of raster graphics you can work with 2 or 4 times larger picture and scale down to export the finished icon.
What was the workflow to achieve that shape? 1. Fill whole area with dark blue, 2. select rectangle area with rounded corners, fill the selection with light blue, 3. select slightly smaller rectangle area and fill it with dark blue?
If so, look for checkboxes responsible for smoothing edges and radius of smoothing in selection tool options, that should take care of jagged edges and antialias them instead.

---

