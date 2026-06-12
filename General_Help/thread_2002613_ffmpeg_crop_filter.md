---
title: "ffmpeg crop filter"
date: 2012-06-12
forum: General Help
---

### Post by spiritech on 2012-06-12
am i right in saying that if i want to crop 40 pixels fro the top of a video and 60 pixels from the bottom, i would have to do it over two different conversions.

my understanding is this would crop the top. crop 40 pixels from position y=0

-vf crop=in_w-0:in_h-40:0:0

and this would crop the bottom. crop 60 pixels from position y=516

-vf crop=in_w-0:in_h-60:0:516

is this correct???

also is it possible to crop from right to left,bottom to top rather than left to right, top to bottom?

---

### Post by FakeOutdoorsman on 2012-06-13
You should be able to do this in one step with:
```
-vf crop=iw:ih-100:0:40
```
(You should double-check this.)

---

### Post by spiritech on 2013-03-08
> **FakeOutdoorsman said:**
> You should be able to do this in one step with:
```
-vf crop=iw:ih-100:0:40
```
(You should double-check this.)

i have done alot of research on this command and have found that the iw:ih part is not needed.

-vf crop=value:value:value:value  is adequate.

so would look like this.

```
-vf crop=640:320:0:40
```

as to my original question it seems to use this command you need to know your original resolution and then deduct the amount you want to crop from this.

maybe the -vf crop filter can crop images regardless of size like the crop filter for convert

```
-crop -0+60
```

---

### Post by FakeOutdoorsman on 2013-03-08
> **spiritech said:**
> i have done alot of research on this command and have found that the iw:ih part is not needed.
I find using *iw* and *ih* instead of manually declaring values to be more flexible: especially when adding more filters to the filterchain, but the good thing is that either method works.

> **spiritech said:**
> as to my original question it seems to use this command you need to know your original resolution and then deduct the amount you want to crop from this.

maybe the -vf crop filter can crop images regardless of size like the crop filter for convert
If you know how much you want to crop, (for example 40 pixels from height) and you want to the crop to be the same for top and bottom (in this example 20 pixels from top and 20 pixels from bottom), you only need:
```
crop=iw:ih-40
```
If you need to offset, then you'll need the additional values for *x* and/or *y*. See the [crop filter](https://ffmpeg.org/ffmpeg-filters.html#crop) documentation for more info.

---

### Post by spiritech on 2013-03-15
> If you know how much you want to crop, (for example 40 pixels from  height) and you want to the crop to be the same for top and bottom (in  this example 20 pixels from top and 20 pixels from bottom), you only  need:
     Code:

     
```
crop=iw:ih-40 
```

If you need to offset, then you'll need the additional values for *x* and/or *y*. See the [crop filter]("https://ffmpeg.org/ffmpeg-filters.html#crop") documentation for more info.                 

so does ```
crop=iw:ih
```    tell the crop filter to use original image size? and if so your original answer is correct.


```
-vf crop=iw:ih-100:0:40
```

---

