---
title: "How do I make my top panel transparent?(Elementary)"
date: 2010-08-23
forum: General Help
---

### Post by TheNerdAL on 2010-08-23
So I use the Elementary theme and the top panel doesn't really go transparent. How do I do it? 

Thanks. :)

---

### Post by vlamnire on 2010-08-23
> **TheNerdAL said:**
> So I use the Elementary theme and the top panel doesn't really go transparent. How do I do it? 

Thanks. :)

Well judging by the amount of beans you have my below tip should help much :)

Well the top panel I'm not exactly sure how to make it all transparent but if you right click the panel and click Properties then click the Background tab you can select Solid Color then put slider to transparent, however, that does not make the system notification icon area transparent nor the menu area transparent.

---

### Post by TheNerdAL on 2010-08-23
> **vlamnire said:**
> Well judging by the amount of beans you have my below tip should help much :)

Well the top panel I'm not exactly sure how to make it all transparent but if you right click the panel and click Properties then click the Background tab you can select Solid Color then put slider to transparent, however, that does not make the system notification icon area transparent nor the menu area transparent.

I would like the whole panel to be somewhat transparent.

---

### Post by TheNerdAL on 2010-08-24
bump

---

### Post by Jesus_Valdez on 2010-08-24
Is easy.

Just need to change Opacity on Compiz setting manager, the opacity brigth and saturation menu.

Add new and

```
class=Gnome-panel
```

Then changes the level.

You can also cheat and put a transparent PNG as panel background.

More detailed explanation:
[http://www.webupd8.org/2009/12/true-transparency-for-gnome-panel.html](http://www.webupd8.org/2009/12/true-transparency-for-gnome-panel.html)

---

### Post by scouser73 on 2010-08-24
I think you can do this by right clicking, going to properties or is it preferences and setting the transparency from there. I have done this, but it was quite a while ago, and I no longer use panels.

---

### Post by Jesus_Valdez on 2010-08-24
> **scouser73 said:**
> I think you can do this by right clicking, going to properties or is it preferences and setting the transparency from there. I have done this, but it was quite a while ago, and I no longer use panels.
You can do this opnly if you select a solid colour (if you change theme you won't have the "whole experience"), also You end up with untransparent zones, wich are disgusting.


In my experience the Compiz way is the best solution.

---

### Post by Slowey_Joey on 2010-08-25
> **Jesus_Valdez said:**
> You can do this opnly if you select a solid colour (if you change theme you won't have the "whole experience"), also You end up with untransparent zones, wich are disgusting.


In my experience the Compiz way is the best solution.

The compiz solution also worked fine for me (thank you very much), although it does really make everything transparent about the panel (including the menus). 

Entering 
```
(class=Gnome-panel) & !(type=Menu | PopupMenu | Dialog | DropdownMenu)
```instead creates the same  effect on the panel without making the menus transparent (I found it here: [http://www.webupd8.org/2009/12/true-transparency-for-gnome-panel.html](http://www.webupd8.org/2009/12/true-transparency-for-gnome-panel.html)).

---

