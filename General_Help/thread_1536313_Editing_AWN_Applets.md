---
title: "Editing AWN Applets"
date: 2010-07-22
forum: General Help
---

### Post by HelloIndustries on 2010-07-22
Avant Window Navigator is great, but there are a couple of bits i'd like to tweak.

**1. YAMA Menu**

[LIST]
[*]I'd like to: Change the icon
[*]Edit the menu icons size, and entry vertical spacing
[/LIST]

**2. Digital Clock**

[LIST]
[*]Change the font / size
[/LIST]

Far as i remember, both these items come in the AWN-Extras package.

If anyone knows how i can make the above changes, and explain it in a n00b-friendly manner, i'd really appreciate it.

---

### Post by kerry_s on 2010-07-22
i don't think you can if theres no right click preferences for it.

it would be nice if you could enter you own style for the digital clock.

---

### Post by HelloIndustries on 2010-07-22
> **kerry_s said:**
> i don't think you can if theres no right click preferences for it.

it would be nice if you could enter you own style for the digital clock.

Maybe i could edit the actual applet?

---

### Post by kerry_s on 2010-07-22
> **HelloIndustries said:**
> Maybe i could edit the actual applet?

:lolflag: okay, go to: /usr/lib/awn/applets & see what you can do.

---

### Post by HelloIndustries on 2010-07-22
> **kerry_s said:**
> :lolflag: okay, go to: /usr/lib/awn/applets & see what you can do.


Wow, y'know, that was so helpful, i feel like donating money to you.

---

### Post by davidmohammed on 2010-07-22
suspect you'll need to learn to compile the awn [source code]("http://wiki.awn-project.org/index.php?title=InstallingFromSource") yourself to undertake these sort of changes you want.

---

### Post by HelloIndustries on 2010-07-22
> **davidmohammed said:**
> suspect you'll need to learn to compile the awn [source code]("http://wiki.awn-project.org/index.php?title=InstallingFromSource") yourself to undertake these sort of changes you want.

Bah!
That's a real shame :(

---

### Post by kerry_s on 2010-07-22
> **HelloIndustries said:**
> Wow, y'know, that was so helpful, i feel like donating money to you.

:lolflag: 
i've looked into it myself a while back & just chalked it up to to much effort, for such a minor thing.

there is also a gconf-editor setting for the fonts, but as far as i can tell it does nothing.

if only it wasn't a compiled *.so file, then there might have been a chance. decompiling & recompiling is just to much effort to put into that.

---

### Post by moonbeam on 2010-07-23
To change the icon just drag and drop the icon you would like to use on the applet icon (this works for _most_ applets).  Note that you need to use the context menu (right click) to change task manager icons.

---

### Post by HelloIndustries on 2010-07-23
> **moonbeam said:**
> To change the icon just drag and drop the icon you would like to use on the applet icon (this works for _most_ applets).  Note that you need to use the context menu (right click) to change task manager icons.

Thanks :)
I'll give that a try next time i use AWN

---

### Post by HelloIndustries on 2010-07-23
Aaaaand: IT WORKS!
Thanks :)

---

