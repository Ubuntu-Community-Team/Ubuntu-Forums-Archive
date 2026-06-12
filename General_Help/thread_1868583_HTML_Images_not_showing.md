---
title: "HTML Images not showing"
date: 2011-10-24
forum: General Help
---

### Post by TooNick on 2011-10-24
I made an HTML website with Windows and I'd add some images. I sent the whole map to my laptop with Ubuntu. If I open the html file Firefox shows up but is not showing the images! I used the HTML code: <img src="image.png" WIDTH=160 HEIGHT=70>
please help :)

---

### Post by veggen on 2011-10-24
As long as you placed the images in the same location your html file (because that's where your src attribute is pointing), you should be fine on any system.
You might also try <img src="./image.png" WIDTH=160 HEIGHT=70> without any change to the semantics.

---

