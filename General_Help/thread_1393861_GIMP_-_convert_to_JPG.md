---
title: "GIMP - convert to JPG??"
date: 2010-01-29
forum: General Help
---

### Post by jimmyUT on 2010-01-29
How do I convert a bitmap to jpg with gimp.  If I use save as and then choose .jpg ext, it always saves with .xcf extension instead

What am I doing wrong?

Thanks for the help!!!

---

### Post by howefield on 2010-01-29
> **jimmyUT said:**
> What am I doing wrong?

You sure you are selecting the .jpg extension properly, there isn't much to do wrong ;)

Save As > Click on Select File Type (By Extension) > Scroll down and highlight JPEG image > Press Save button > Press Export button in the dialogue box that pops up ? > Press Save button on the quality dialogue box that comes up next. Bingo - job done.

Another method is to convert with the commandline, open a terminal and type

```
convert image.bmp image.jpg
```

where "image" is the file name you have/want.

---

### Post by jimmyUT on 2010-01-30
I was using the wrong file selection box, I figured it out..
Thanks!!!

---

### Post by blueshiftoverwatch on 2010-01-30
> **howefield said:**
> Another method is to convert with the commandline, open a terminal and type
Here's a [full list]("http://www.imagemagick.org/script/convert.php") of the commands.

---

### Post by pbrane on 2010-01-30
You can also just give the file a .jpg extension in the **name** edit box. That's what I do. No need to use the *Select file type*. GIMP will honor the extension you give the image.

---

