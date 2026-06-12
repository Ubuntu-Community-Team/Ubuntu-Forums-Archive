---
title: "batch crop images of different sizes"
date: 2012-09-04
forum: General Help
---

### Post by spiritech on 2012-09-04
is there a way of batch cropping a set of images that are of different sizes?

i have had a look at imagemagick -crop program. it only really works on images all of the same size.

i am trying to crop the first few lines from the bottom of the image.

spiritech

---

### Post by papibe on 2012-09-04
Hi spiritech.

If you use only offsets on the geometry parameter, the cropping is independent of the image's size. For instance, this would crop 20 pixels of the bottom of a picture:
```
convert original.jpg -crop [COLOR="Red"]**+0-20**[/COLOR] bottom_cropped.jpg
```
Let us know how it goes.
Regards.

---

### Post by spiritech on 2012-09-04
> **papibe said:**
> Hi spiritech.

If you use only offsets on the geometry parameter, the cropping is independent of the image's size. For instance, this would crop 20 pixels of the bottom of a picture:
```
convert original.jpg -crop [COLOR=Red]**+0-20**[/COLOR] bottom_cropped.jpg
```Let us know how it goes.
Regards.

yes that worked fine. thank you.

---

### Post by papibe on 2012-09-04
:D Great!

Please mark this thread as solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), when you have the chance.

Regards.

---

