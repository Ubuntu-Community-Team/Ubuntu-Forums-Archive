---
title: "Compiz affecting GIMP brush outline rendering"
date: 2009-09-05
forum: General Help
---

### Post by AwesomeTux on 2009-09-05
Hello,

Today I noticed that Compiz is triggering a rendering glitch in GIMP, it includes the GIMP paint brush tool outlining.

When Compiz is enabled, if I use the paint brush to draw I notice a glitch happens, the outlining of the brush is duplicated and left rendered with the image I'm editing. It doesn't become physically rendered with the image, though it is displayed over the image until I redraw on the area of the image. This happens when the brush is moved too fast.

I believe it has something to do with the Tile Cache in GIMP, example, the rendering falls behind the pointer position.

Here's a video of what happens:
[http://www.youtube.com/watch?v=X9wdkeS__Xc](http://www.youtube.com/watch?v=X9wdkeS__Xc)

---

