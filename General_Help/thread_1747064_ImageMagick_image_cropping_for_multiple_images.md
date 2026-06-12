---
title: "ImageMagick image cropping for multiple images"
date: 2011-05-02
forum: General Help
---

### Post by akzouu on 2011-05-02
Hey, I have multiple hundreds of images from where i want to crop from top and bottom. I am looking for a command by how i could do it and for every photo at one time. It's also possible to export as pdf for me. Images are in png-format. All images are same size.

Thanks for replying, if u will find a solution.

---

### Post by oldfred on 2011-05-02
I ran across this on thumbs, but it also discusses framing. I have not used it.

[http://www.imagemagick.org/Usage/thumbnails/#framing](http://www.imagemagick.org/Usage/thumbnails/#framing)

---

### Post by akzouu on 2011-05-02
I found the solution for this situation. Here is an example:

convert *.png -crop 1280x1024-0+87 -crop 1280x1024+0-40 output.pdf

For those who have had a similar problem.

---

