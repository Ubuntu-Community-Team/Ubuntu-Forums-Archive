---
title: "analyize jpeg brightness script"
date: 2011-06-28
forum: General Help
---

### Post by frente69 on 2011-06-28
Hi,

I am trying to make a script which will analyze jpeg images taken from a webcam. i can get a image easily enough but i can't figure out a way to get the images average brightness as a number. Any suggestions?

Thanks

---

### Post by frente69 on 2011-06-28
After many hours with my head stuck in google i stumbled across a single reference that does what i want to do:
[http://stackoverflow.com/questions/4240775/generate-a-value-to-reflect-the-average-brightness-of-an-image](http://stackoverflow.com/questions/4240775/generate-a-value-to-reflect-the-average-brightness-of-an-image)

The command is:
```
convert /path/imagename.jpg -colorspace gray -format "%[fx:100*mean]%%" info:
```

A black JPEG:
user@ubox:~$ convert /data/downloads/black.jpg -colorspace gray -format "%[fx:100*mean]%%" info:
0%
A white JPEG:
user@ubox:~$ convert /data/downloads/white.jpg -colorspace gray -format "%[fx:100*mean]%%" info:
100%
The following was a grey JPEG
user@ubox:~$ convert /data/downloads/test.jpg -colorspace gray -format "%[fx:100*mean]%%" info:
49.8039%

I have no idea exactly how the command works (feel free to explain it to me :-)) but it works so i'm happy.

---

