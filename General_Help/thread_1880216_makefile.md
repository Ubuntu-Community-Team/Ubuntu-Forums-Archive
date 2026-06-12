---
title: "makefile"
date: 2011-11-13
forum: General Help
---

### Post by thom_tartu on 2011-11-13
hello,
i need to convert gif files in directory gif/ to pnm files in directory pnm/.How should i do that using makefiles?

---

### Post by Sigma1 on 2011-11-13
Can't you use the convert command (in imagemagick, which you'll have if you've got gimp installed)? i.e. ```
convert imagename.gif imagename.png
``` or, from inside the folder: ```
convert * *.png
``` to do a whole batch of images.

---

