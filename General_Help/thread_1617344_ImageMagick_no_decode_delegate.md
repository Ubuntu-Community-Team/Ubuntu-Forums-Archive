---
title: "ImageMagick no decode delegate"
date: 2010-11-09
forum: General Help
---

### Post by guadaatenea on 2010-11-09
I keep trying to convert a bunch of jpg files into pdf, but ImageMagick just seems to keep failing there. 
Well well, after three thousand fix and reinstall attempts (seriously, I've been trying to fix it for the last month or so), this is what I'm getting today:

```
convert: no decode delegate for this image format `IMG_9.jpg' @ error/constitute.c/ReadImage/532.
convert: missing an image filename `back.pdf' @ error/convert.c/ConvertImageCommand/2949.

```

As it seems there's no other way to do this save for this program, and I need it badly, any ideas?

---

### Post by searchfgold6789 on 2010-11-09
Try installing Ubuntu Restricted Extras and libjpeg.
Or you could [code]convert pdf <filename> :-| <pdf filename>

---

### Post by SeijiSensei on 2010-11-09
You might have better luck asking this question at [ImageMagick's site]("http://www.imagemagick.org/discourse-server/").

---

### Post by bashologist on 2010-11-09
I'm very familiar with imagemagick. What was the exact command and did you try on another jpeg file?

Have a look at this and see if it helps:
[http://www.wizards-toolkit.org/discourse-server/viewtopic.php?f=1&t=7013&start=0&st=0&sk=t&sd=a](http://www.wizards-toolkit.org/discourse-server/viewtopic.php?f=1&t=7013&start=0&st=0&sk=t&sd=a)

Are you not using the imagemagick from the repositories? You're compiling this yourself why?

Are you not able to do this command?
```
convert test.jpg test.pdf
```

Usually I will have both restricted extras and the medibuntu repository installed, what do you have? Maybe the medibuntu has a better version.

---

