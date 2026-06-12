---
title: "imagemagick batch convert"
date: 2010-06-18
forum: General Help
---

### Post by cotcot on 2010-06-18
I want to convert a batch of pictures with a command like this :
```
convert foto_???.JPG -gravity east -resize 1920x1080 -background black -splice 100x0 -extent 1920x1080 foto_???.PNG
```
The file name is for instance foto_067.JPG. After conversion I want the file name foto_067.PNG. The batch contains more foto with the same name except that the number is different. The numbers are not all in a sequence. This means that I have foto_013.JPG, foto_014.JPG, foto_023.JPG, foto_033.JPG etc...
Can somebody help me with the code line so that it will do the conversion and keep the file name before PNG ?

Thanks

---

### Post by apmcd47 on 2010-06-18
Isn't mogrify the batch convertion program if IM? e.g.```
mogrify -format png -gravity east -resize 1920x1080 -background black -splice 100x0 -extent 1920x1080 foto_???.JPG
```

Andrew

---

### Post by cotcot on 2010-06-20
Thanks Andrew.
With mogrify it is doing what I want except for the -splice option that is not recognized. This seems to be a known bug. I solved it by using [COLOR="Blue"]-border 100 -borderline [/COLOR]black instead of [COLOR="blue"]-splice 100x0[/COLOR]

---

