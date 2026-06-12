---
title: "change the background-image with parameters(style, color)"
date: 2010-05-31
forum: General Help
---

### Post by refreegrata on 2010-05-31
Hello guys

I have a question

I need to do a script to change the background image.
I can do this with this command
[PHP]gconftool-2 -t str -s /desktop/gnome/background/picture_filename image_rute[/PHP]that work's fine but i need send some parameters to the background image

1)I need to set the style(mosaic, center, etc)
2)I need to set a color(because the image is smaller than the resolution)

I can't find how set this two parameters

Somebody know what is the solution?

that's all, thanks for read, and sorry for my poor english

---

### Post by StuartN on 2010-05-31
> **refreegrata said:**
> [PHP]gconftool-2 -t str -s /desktop/gnome/background/picture_filename image_rute[/PHP]

You would use the same command, setting /desktop/gnome/background/picture_options (to zoom, centered, scaled etc) and /desktop/gnome/background/primary_color, /desktop/gnome/background/secondary_color, etc. Open the gnome configuration editor to see the parameter names and values.

Incidentally, you could just set the background image name and then recreate the image, using Imagemagick or some elaborate command - for instance the R statistics package could write a graph into the image file.

---

### Post by refreegrata on 2010-05-31
[LEFT]Thanks, finally i understand.
You're the best
[/LEFT]

---

