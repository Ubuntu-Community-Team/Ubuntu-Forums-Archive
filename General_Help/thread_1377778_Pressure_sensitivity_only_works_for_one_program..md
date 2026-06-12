---
title: "Pressure sensitivity only works for one program."
date: 2010-01-10
forum: General Help
---

### Post by VisionaryVanGogh on 2010-01-10
Hi everyone, I'm a new Ubuntu user.
I have a Wacom Bamboo Fun tablet, which as far as I know, is supported. The pressure sensitivity works well on GIMP, then I noticed that it doesn't seem to work in any of the other graphics programs I tried using. Like Pencil animation. (which I know supports pressure sensitivity)

Could anyone tell me what I can do to fix this problem? 

Thanks!

---

### Post by Favux on 2010-01-10
Hi VisionaryVanGogh,

Welcome to Ubuntu!

I haven't played too much with Pencil.  Did you check 'Size with pressure' and look in prefrences?  I've got pressure in it but it doesn't seem to be as sensitive as Gimp.  But I haven't really looked at it.

Do you know if Pencil like Blender is hardcoded to want to see stylus?  To check if you have stylus:
```
xinput --list
```
and
```
xsetwacom list
```
should return stylus, eraser, etc.

If so you may need a modified wacom.fdi.  You could check out the ones in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

Hope this helps.

---

