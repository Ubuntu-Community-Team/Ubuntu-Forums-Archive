---
title: "Gimp problem with GIFs"
date: 2011-01-06
forum: General Help
---

### Post by hakermania on 2011-01-06
Hello all.

When I create a new gif with gimp, layers1 continue existing after the showing of layer2 and layer1 and 2 after showing layer3 and so on. The loop cleans on the 1st layer again.
This has as result something like this:
[CENTER][IMG]http://i53.tinypic.com/14t0bjb.gif[/IMG]

[LEFT]How can I avoid ti?
[/LEFT]
[/CENTER]

---

### Post by lykeion on 2011-01-06
Open the image in GIMP, go to File-> Save As. Insert a name for your image, then go down to "Select File Type." Make it a .gif image, and then click save. 

GIMP should tell you that you have to export the image, and will ask you to flatten it or create an animated gif. Click the button that says "Save as Animation", and then click export. 

You’ll get yet another dialogue box asking you some more specifics. Here you can set the frame rate (a higher number makes the animation go faster), and add a comment. Where it says "Frame Disposal where Unspecified," click on the "One frame per layer (replace)" option, then click Save.

---

