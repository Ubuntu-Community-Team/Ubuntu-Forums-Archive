---
title: "Enlarge image canvas using ImageMagic"
date: 2010-12-28
forum: General Help
---

### Post by U2XS on 2010-12-28
I've been learning about ImageMagick & it's great!  The one thing that I can't learn to do is to expand the canvas size.  So if the ratio is 3x2, I want to add extra white space to make it 3x3.  If I use the -geometry function, it enlarges the image to the proportions I want, but it loses the aspect ratio.

If you turn to page 377 (or 388 in PDF) of the [User Manual]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBMQFjAA&url=http%3A%2F%2Fwww.imagefolio.com%2FImageMagick%2FImageMagick.pdf&rct=j&q=imagemagick%20pdf%20manual&ei=cH8ZTc6RBcL58AaRmdyBDg&usg=AFQjCNHrmcp0jEfLfMqUjVVej_2m1Lq5Sw&cad=rja"), under "Montage", you'll see that ImageMagic can do what I want.  The thumbnails in the example image are all of different proportions but the alloted space is 1x1 for all.

However the documentation on this function is pretty bad!  Does anyone know how to do this?

---

### Post by U2XS on 2010-12-28
I found it in the documentation here: [http://www.imagemagick.org/Usage/crop/#border]("http://www.imagemagick.org/Usage/crop/#border")

My code
```
convert sand.jpg -bordercolor white -border 0x50 sand.jpg
```

I still need to read the height/width to determine how much more it needs, but it's a good solution.

---

