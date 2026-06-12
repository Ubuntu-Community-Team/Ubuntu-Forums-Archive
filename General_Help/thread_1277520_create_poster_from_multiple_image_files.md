---
title: "create poster from multiple image files"
date: 2009-09-28
forum: General Help
---

### Post by DrScum on 2009-09-28
What software can I use to put lets say 4 letter sized scans created with Xsane multipage project together into one file and one document, that can be viewed either scaled down or by scrolling.

---

### Post by sancho panza on 2009-09-28
I do not know what format the scans are in, but can you not use Gimp?
If not, try Hugin, which is also in the repositories.
Tutorial on [hugin here]("http://hugin.sourceforge.net/tutorials/multi-row/en.shtml").

---

### Post by DrScum on 2009-09-28
The formats are tiff. I know GIMP but how can I put together multiple scans. I tried to do it but wasn't successful.

---

### Post by StuartN on 2009-09-28
> **DrScum said:**
> The formats are tiff. I know GIMP but how can I put together multiple scans. I tried to do it but wasn't successful.

**1. Old school:**

You have to plan ahead by mentally noting which component image is top-left, top-right etc. In an ideal world all the scans will be exactly aligned with the horizontal and vertical, but in a real world you probably need to rotate a little and resave them.

Open a new, blank image in Gimp which is big enough (i.e. a little bit more than twice the height and twice the width) of the components. Open each component in turn and copy it, then "paste as new layer" into your big picture, then slide it to approximately the correct position. When all four components are in place in four separate layers you can hide all except the bottom two components and start with one component (the bottom one) placed exactly in a corner and reduce the transparency of the one above so you can see both as you align the upper one.

Move up the stack unhiding and aligning all the layers. When you have finished you might want to softly erase the edges where the images overlap to hide any lap marks.

It sounds like a pain in the rear, but is actually much easier than doing the same thing with paper (no glue, no mess, no tears, infinite undo...). My biggest collage like this is many hundred of overlapping sections.

**2. Cheat:**

Download a panoramic stitcher like Hugin. It will seamlessly blend the edges, rotate and align the components, and cover up any distortions. To be honest the first gives a better result if you have a photo or painting, but Hugin is really good with even-toned photographs that have a big overlap.

---

### Post by DrScum on 2009-09-28
Thanks StuartN. The part with "opening a new image twice the size" was the hint I needed. I was prepared to have it to be a little bit of a hassle but I need the "big picture".

---

### Post by geirha on 2009-09-28
There's also the montage command which is part of [imagemagick](apt://imagemagick). Lots of examples on how to use it here: [http://www.imagemagick.org/Usage/montage/](http://www.imagemagick.org/Usage/montage/)

---

### Post by P4man on 2009-09-28
Google Picasa makes it trivially easy to make montages like that. just select the images, click "collage" and chose any of the templates.

---

### Post by StuartN on 2009-09-28
Only a slight tangent, this [http://gigapan.org/gigapans/fullscreen/15374/](http://gigapan.org/gigapans/fullscreen/15374/) is a stitched panorama of 200+ images of the crowd at Barack Obama's inauguration created by GigaPan.org

It is absolutely stunning.

---

### Post by jocko on 2009-09-28
Inkscape would do the trick nicely. It's similar to adobe illustrator, so you can use it to make posters or collages from images, add text and line/box drawings and stuff like that...

---

### Post by DrScum on 2009-09-29
Thanks again, everyone, this is the real advantage of Ubuntu over another OS, the fast and high quality feedback from the community when you have a problem.

---

