---
title: "Where is the terminal located? (folder)"
date: 2011-12-01
forum: General Help
---

### Post by iosuna86 on 2011-12-01
So here is my problem (running Ubuntu 11.10).

I was trying to **remove the "Universal Access" shell extension** from my system as stated in: [http://ubuntuforums.org/showthread.php?p=11411427](http://ubuntuforums.org/showthread.php?p=11411427). Well, **it did not work**. It actually removed all the panels and **now I cannot use the ALT + F2 or CTRL + ALT + T shortcut to open a terminal **and switch that file to its default settings.

I need to locate the **FOLDER where I can see the terminal**. I am looking for something like an icon that I can double click in order for the terminal to pop up. But I can't find any.

So no shortcuts, no "Aplications" menu, just the wallpaper and a couple of folders, thanks to which I can navigate through the whole file system with nautilus.

Do any of you know where is this terminal located?

**Thanks** in advance!

---

### Post by Larkspur on 2011-12-01
Look in /usr/share/applications/

---

### Post by iosuna86 on 2011-12-01
> **Larkspur said:**
> Look in /usr/share/applications/

Thank you so much Larkspur!

That was it! ;)

---

### Post by haqking on 2011-12-01
havent got 11.10 up and running right now.

But i doubt it has changed

```
/usr/bin/gnome-terminal
```

---

### Post by iosuna86 on 2011-12-01
> **haqking said:**
> havent got 11.10 up and running right now.

But i doubt it has changed

```
/usr/bin/gnome-terminal
```

Yeah, that works too.

Thanks!

---

