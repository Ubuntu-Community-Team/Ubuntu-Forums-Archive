---
title: "GraphicsMagick limits images to 8 bits per pixel"
date: 2011-05-15
forum: General Help
---

### Post by Chethan S on 2011-05-15
When I run GNU Octave and try to use the command 'imshow' to display an image, I get the following warning:

```
warning: your version of GraphicsMagick limits images to 8 bits per pixel
```

The image displays fine but I am not able to understand what is this limitation due to. I run Ubuntu 11.04 64-bit and Octave 3.4.0 installed from sources.

---

### Post by floomby on 2011-06-16
Yes, I came across this as well.

Running Octave 3.4.1 compiled from source and Ubuntu 11.04 64 bit.

Perhaps the packaged version of graphicsmagick is compile with some limitation?

---

