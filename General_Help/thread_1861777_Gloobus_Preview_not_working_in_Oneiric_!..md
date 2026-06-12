---
title: "Gloobus Preview not working in Oneiric !\."
date: 2011-10-16
forum: General Help
---

### Post by Bubble32 on 2011-10-16
Hey there,
After I upgraded to 11.10, Gloobus Preview which worked nicely on natty isn't functioning anymore. I was using it along nautilus-elementary but now when I press SPACE on a file or folder nothing happens!!
By the way, when I run gloobus-preview from terminal (or from dash) it shows my home directory in preview, but none when I press SPACE on a file/folder.
Any help would be appreciated since I was thoroughly enjoying gloobus' handy features! :)\.

---

### Post by sant on 2011-10-16
You could test Sushi , is  the previewer what I am using in Oneiric since Nautilus no longer previews audio files.Sushi is capable of previewing sound and video files ,pictures and some documents.
( Features are less than Gloobus Preview , but it could be useful )

---

### Post by Qwerty_ls on 2011-10-27
I have Sushi installed in my brand new ubuntu 11.10 but it's not working with any .doc .odt .xls etc files. Only .txt videos and music.
Any idea??

Thanks for you attention

---

### Post by koohyar on 2011-10-29
I think the problem with Gloobus Preview is it's not compatible with nautilus 3.2 -upgraded form 2.x from natty..
I have the same problem and I think "downgrading" nautilus is sth we could try...haven't done it though, but I'll let you know if it worked! ;)\.

---

### Post by koohyar on 2011-12-12
I hope it's not too late and still haven't done any serious damages while trying to downgrade your nautilus!!
But Gloobus Preview's newer version is available which works very well and stably under nautilus 3.2..
Simply try:
```

sudo add-apt-repository ppa:gloobus-dev/gloobus-preview
sudo apt-get update
sudo apt-get install gloobus-preview gloobus-sushi libgdk-pixbuf2.0-dev

```
Take Care\.

---

### Post by Bubble32 on 2011-12-12
Thanks a lot koohyar!
Worked like a charm and you made my life in nautilus much easier! :)

---

### Post by AbhishekGupta0693 on 2012-10-18
THanx For this solution

---

