---
title: "font/tab colors in Adobe Reader"
date: 2012-07-21
forum: General Help
---

### Post by coverup1128 on 2012-07-21
In Adobe Reader, the background of inactive tabs has the same color as the text. Both the font and background use a dark grey color; see the attached image. In Ubuntu 10.04 I was able to fix this by making the font color darker, but I forgot how I did that (-:. Can anybody help with this? I am using Ubuntu 12.04, Gnome Classic (without effects).

---

### Post by coverup1128 on 2012-07-22
I now recall that in 10.04 I was able to customize the theme by making the fonts darker. Does 12.04 allow themes to be customized?

---

### Post by coverup1128 on 2012-07-28
Solved. If you have this problem, open file /usr/share/themes/ambiance/gtk-2.0/gtkrc using an editor, and change fg_color from #4c4c4c to #000000.

---

### Post by Diegol83 on 2013-01-23
> **coverup1128 said:**
> Solved. If you have this problem, open file /usr/share/themes/ambiance/gtk-2.0/gtkrc using an editor, and change fg_color from #4c4c4c to #000000.

HI Dear All.
I tried the suggested solution but I could not solve the problem. I did this:

Ambiance theme:
cd /usr/share/themes/Ambiance/gtk-2.0
sudo gedit gtkrc
>>>change fg_color from #4c4c4c to #000000
 
Radiance theme:
cd /usr/share/themes/Radiance/gtk-2.0
sudo gedit gtkrc
>>>change fg_color from #4c4c4c to #000000

In fact, what we need to change is in the first line in both cases:
gtk-color-scheme = "base_color:#ffffff\nfg_color:#000000

I use the Adobe Reader 8.1.7 because it is the last version in spanish, and Ubuntu 12.10.

I tried even restarting Ubuntu, but there is not solution.

May you help me please?

---

