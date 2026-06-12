---
title: "Screen shot of specific area?"
date: 2009-11-21
forum: General Help
---

### Post by hcker2000 on 2009-11-21
I am wondering if there is any way (command line or other) to take a screen shot of an area by specifying the top left corner (x,y) and a width and a height for the screen shot?

In windows this is easy enough to do with the program cropper but I have yet to figure out how to get it to work in wine or mono.

---

### Post by fiveacez on 2009-11-22
Go to

Applications > Accessories > "Take Screenshot"

You also have the option of taking a screenshot of the entire window as well.

---

### Post by kaibob on 2009-11-22
> **hcker2000 said:**
> I am wondering if there is any way (command line or other) to take a screen shot of an area by specifying the top left corner (x,y) and a width and a height for the screen shot?

In windows this is easy enough to do with the program cropper but I have yet to figure out how to get it to work in wine or mono.

The import command-line utility, which is in the Imagemagick suite, will do what I think you want. For example,

```
import -window root -crop 640x640+10+10 output.png
```

For more detail see:

[http://www.imagemagick.org/script/import.php](http://www.imagemagick.org/script/import.php)

If you want to select the screenshot area with a mouse, then a great many utilities will do what you want.

---

### Post by Bonster on 2009-11-22
install Shutter, u can make a box of the thing u want to take screenshot of

---

### Post by hcker2000 on 2009-11-22
> **kaibob said:**
> The import command-line utility, which is in the Imagemagick suite, will do what I think you want. For example,

```
import -window root -crop 640x640+10+10 output.png
```

For more detail see:

[http://www.imagemagick.org/script/import.php](http://www.imagemagick.org/script/import.php)

If you want to select the screen shot area with a mouse, then a great many utilities will do what you want.

Thanks I will give this a go as it sounds like the only one that does what I want. 

I need to be able to specify the size and area of capture repeatedly not just use shutters click and drag to capture an area as that would not be very accurate.

---

### Post by Bag-O-Stuff on 2009-11-22
Gimp also has the ability to acquire a screen shot and can use a timer.  It's one of the only utilities I've found that lets you grab the context menus on the Desktop when you right click.  It even grabs the actual mouse cursor where some of the others don't.

---

### Post by mbeach on 2009-11-22
> **hcker2000 said:**
> 
I need to be able to specify the size and area of capture repeatedly not just use shutters click and drag to capture an area as that would not be very accurate.
For naming the files, you may be interested in:
[http://ubuntuforums.org/showpost.php?p=7543441&postcount=6](http://ubuntuforums.org/showpost.php?p=7543441&postcount=6)

import's "-delay" image setting is also one that can be helpful, see
"man import"

---

