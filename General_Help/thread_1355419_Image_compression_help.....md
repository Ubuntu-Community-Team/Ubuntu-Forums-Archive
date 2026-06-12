---
title: "Image compression help...."
date: 2009-12-14
forum: General Help
---

### Post by Enigmapond on 2009-12-14
Hi!  I'm trying to find either a programme or terminal command to "loss-less"  batch compress .jpg files. For instance I used to use xat Image Optimizer when I was using Windoze. If I had a .jpg that was 1mb I could compress it to 250kb without changing the dimensions or quality of the photo. Is there a programme or command I can use to achieve this with Ubuntu?


 Thank you in advance!;)

---

### Post by llamabr on 2009-12-14
depends on what you want to do.  I'm not familiar with xat optimizer.

Do you want to compress them (that is, like zip them for storage)?  Or just make them smaller, but still usable?

If the former, I'm surprised that there's a windows program to do that.  jpg files are already extremely compressed images (it's what it was designed for).

If the latter, you want imagemagick

[http://www.imagemagick.org/Usage/resize/](http://www.imagemagick.org/Usage/resize/)

---

### Post by Enigmapond on 2009-12-14
Wow...that was quick. Thank you, however I'm looking to keep the same dimensions yet decrease how large (kb's) the image actually is, i.e. 1mb to 250kb. So I guess it would be re-sampling I'm looking to do. What would the command be to batch a folder of pictures and re-sample them to 50%? I know there would be some loss in quality...I hope that clarifies.:)

---

### Post by Enigmapond on 2009-12-15
Thank you for pointing me to Imagemagick. I have solved this problem with the "mogrify" command. Simply opening the folder in the terminal and:

```
mogrify -resample 50 *.jpg
```This resampled all the large images by 50% with little to no loss in quality. Thank You Again!!!

Cheers! :D

---

### Post by llamabr on 2009-12-15
Yes, mogrify is very useful for changing the size, geometry, and format of an image.

The gimp is just a gigantic gui frontend for imagemagick.  You could spend years learning its functions, and still not know half.

Glad to help.

---

