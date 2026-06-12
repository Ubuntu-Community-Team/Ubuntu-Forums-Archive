---
title: "gif animation"
date: 2009-10-17
forum: General Help
---

### Post by homer_j17 on 2009-10-17
Hello people, im a new member and totally new at linux. i need to know how to make a .gif animation that will run on firefox.

i have a series of .jpg files (from paraView). im guessing that there is a really simple way of just having each one of them as a frame and make a gif animation directly(preferably from CLI?). the files are sequentially numbered: u.00.jpg, u.01.jpg and so on...

please help. 
Thanks

Farhan

---

### Post by StuartN on 2009-10-17
> **homer_j17 said:**
> i have a series of .jpg files (from paraView). im guessing that there is a really simple way of just having each one of them as a frame and make a gif animation directly(preferably from CLI?).

The two easiest ways I can think of are either:

a) Open all the files in Gimp, "using open as layers". You will need to fiddle a bit with the layer transparency modes and frame replacement modes, but look in Filters->Animation and the Gimp help pages.

b) ImageMagick tools do command line animation, with a lengthy tutorial at [http://www.imagemagick.org/Usage/anim_basics/](http://www.imagemagick.org/Usage/anim_basics/)

---

### Post by Arabica Bean on 2009-10-17
There is a plugin for GIMP (The main image editing software), called GAP. Have a look for it in the repositries. When it's installed, there is an extra menu for animation/video. If you have done gif animations in Photoshop before, you may be familiar. It may be too much for you though if you just want a very simple gif animation.

Try to create an image with each layer, a part of the animation that you want, and then export to gif. I think it gives you the option of saving as animation. That should solve it.

---

### Post by fragos on 2009-10-17
You may find [http://www.getdeb.net/app/LiVES](http://www.getdeb.net/app/LiVES) helpful. It's a video editor that accepts jpeg images as single frames, provide transition effects and will save as animated GIF. GIMP gives you the ability to edit individual frames and even set a different frame rate for each frame. I find both useful.

---

### Post by kaibob on 2009-10-17
As noted by StuartN, the Imagemagick convert utility will do what you want. To see how this works, try the following command:

```
convert -delay 100 -loop 0 *.jpg output.gif
```

---

