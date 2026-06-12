---
title: "&quot;Mood light&quot; or &quot;Light box&quot;..."
date: 2010-10-25
forum: General Help
---

### Post by tada on 2010-10-25
Is there a simple way to persuade Ubuntu to display the same colour across the whole of the screen (without a window)?

I'd like to use such on my laptop to convert it into a rudimentary light box for viewing photograph negatives and other transparencies.

I'd prefer an elegant solution that did not require me to make an image of the required colour and/or set the desktop and hide the menus/icons.

I'm sure there must be a trick using imagemagick but I can't bend it to my will.

The command below creates and displays an on-the-fly image but I can't see how to persuade display to cover the OS menus (at the top and bottom of the screen) or to not paint a window border.

    display -size 2000x2000 -geometry +0+0 xc:white

Any help much appreciated

---

### Post by uRock on 2010-10-25
Use GIMP or MTPaint to make an all white square picture, then set it as the background.

---

### Post by tada on 2010-10-25
> **uRock said:**
> Use GIMP or MTPaint to make an all white square picture, then set it as the background.

Thanks for looking and trying to help but this is precisely the 'solution' I wanted to avoid by being so explicit in my original post.

---

### Post by uRock on 2010-10-25
Open the image with the default image viewer, then click the view menu and select full screen. You might have to adjust the dimensions of the image so that it fills the screen when you open it in full screen mode, but that is easy to do in Gimp.

---

### Post by tada on 2010-10-25
Ok, uRock, we're getting there(ish)...

I can get the geometry of the screen:
GEOMETRY=$(xwininfo -root | sed -n -e 's/^.*geometry \([^+]*\)+.*/\1/p')

And make a blank image of that size with ImageMagick:
convert -size $GEOMETRY xc:white <file name>

But I cannot, programmatically, launch eog (default image viewer) to nicely display that <file name>

- eog takes a -f parameter but shows the 'exit full screen' banner across the top :-(

Is there something else out there that will display a full screen image?

---

