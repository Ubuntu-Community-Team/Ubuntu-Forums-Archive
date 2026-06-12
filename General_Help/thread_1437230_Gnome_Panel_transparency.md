---
title: "Gnome Panel transparency?"
date: 2010-03-23
forum: General Help
---

### Post by Cam! on 2010-03-23
How would I go about making my top Panel transparent? I know how to do the basic variation, but things like the Clock, Notification Area, and Gnome menu aren't.

How would I make my panel transparent, almost like Mac OS X's?

---

### Post by linden940 on 2010-03-23
i take it that you got it solved right?

---

### Post by Cam! on 2010-03-23
I accidentally hit SOLVED. -_-

---

### Post by coffeecat on 2010-03-23
> **Cam! said:**
> How would I go about making my top Panel transparent? I know how to do the basic variation, but things like the Clock, Notification Area, and Gnome menu aren't.

How would I make my panel transparent, almost like Mac OS X's?

By "basic", I presume you mean right-click > properties > Background tab > tick solid colour and move slider to desired position.

It depends on the theme. Some themes give you transparency this way which includes the gnome menu, notification area, etc. Others don't and look ugly with half the panel still opaque. All I can suggest is to try different themes. One good source is:

[http://www.bisigi-project.org/?lang=en](http://www.bisigi-project.org/?lang=en)

Some, but not all, of the Bisigi themes look good with transparent panels.

---

### Post by stinkeye on 2010-03-23
I've found some themes have a panel.rc file in the theme's gtk-2.0 folder.
If I go to the theme I'm using in ~/.themes and rename panel.rc (eg panel.rc.bak),
the panel transparency works.

---

### Post by musicman10489 on 2010-07-11
Thanks **stinkeye**! That worked like a charm!

---

### Post by abdusamed on 2010-08-14
> **stinkeye said:**
> I've found some themes have a panel.rc file in the theme's gtk-2.0 folder.
If I go to the theme I'm using in ~/.themes and rename panel.rc (eg panel.rc.bak),
the panel transparency works.

mine is empty.. i don't have compiz enabled...

---

### Post by stinkeye on 2010-08-14
> **abdusamed said:**
> mine is empty.. i don't have compiz enabled...
See this post.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=9629583&postcount=5[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=9629583&postcount=5")

---

