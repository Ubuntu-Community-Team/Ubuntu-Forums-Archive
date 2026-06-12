---
title: "find current background image location"
date: 2012-08-08
forum: General Help
---

### Post by hyfanious on 2012-08-08
Hi,
who can let me know how can I find the path of the picture that is showing as a background in my system?
I have a lot of backgrounds stored in my "background image list" and some of them is not looking interesting anymore and I wanna pick them out from the list every time one of them shows
the property of background must stored somewhere and I need to get access to its value.
running OS: Ubuntu 12.04
thanks in advance.

---

### Post by black veils on 2012-08-08
if i understand correctly..

go to filesystem in your file manager, have a look in /usr/share/backgrounds

---

### Post by hyfanious on 2012-08-08
> **black veils said:**
> if i understand correctly..

go to filesystem in your file manager, have a look in /usr/share/backgrounds

I'm afraid U r not,
see, the background's image is a "property", and each property has a "value", that value determines which picture must be shown as a background,
consider if the value of background would be "null" u have nothing to show in ur desktop as a background, otherwise , if u have a picture shown as a background, definitely u have an non-null value in ur background's property. AND this value would be the path address of that related picture.
this property and its own value somewhere must been saved, I need to find it.
is it clear enough now?

---

### Post by Vaphell on 2012-08-08
```
gsettings get org.gnome.desktop.background picture-uri
```
if you want to use gui tool to check various settings, use *dconf-editor*

---

### Post by hyfanious on 2012-08-09
> **Vaphell said:**
> ```
gsettings get org.gnome.desktop.background picture-uri
```
if you want to use gui tool to check various settings, use *dconf-editor*

the result is : ```
'file:///home/hyfanious/Pictures/Wallpapers/backgrounds.xml'
```
this XML file is the one that I've created and my mentioning of "background image list" is just exactly related to this file
I need to know which node of this xml file is reading by now
Tnx again.

---

### Post by Vaphell on 2012-08-09
looks like it's not trivial, i don't think the system stores that info in plain text anywhere.
Had you used some wallpaper changer app mimicking manual switching, you would see that key changing.

---

