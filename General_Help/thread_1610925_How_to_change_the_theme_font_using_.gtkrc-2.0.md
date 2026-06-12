---
title: "How to change the theme font using .gtkrc-2.0?"
date: 2010-11-01
forum: General Help
---

### Post by Rumtscho on 2010-11-01
I have the bug with the nvidia drivers breaking the theme in 10.10. Solved it as described here: >  I had the same problem with GTK theme: for some reason it defaults to "Raleigh" (instead of "Ambiance") with nvidia drivers. I fixed it by adding the following in my .gtkrc-2.0 :

Code:

include "/usr/share/themes/Ambiance/gtk-2.0/gtkrc"

And if you want proper icons with it then also add:
Code:

gtk-icon-theme-name = "ubuntu-mono-dark"

  
(quote from from [http://ubuntuforums.org/showthread.php?t=1587238&page=2](http://ubuntuforums.org/showthread.php?t=1587238&page=2)) 

Now I have the beautiful theme back for my own user account, but the font is wrong. How do I set the font to the Maverick default (and BTW, how is this font called?)? And where can I learn more about the syntax of the .gtkrc-2.0 file?

---

### Post by TeoBigusGeekus on 2010-11-01
Add this line to the gtkrc file
```
gtk-font-name="Ubuntu 10"
```

---

### Post by hhh on 2010-11-01
> **Rumtscho said:**
> And where can I learn more about the syntax of the .gtkrc-2.0 file?
Under "Properties" and "Property Details"...
[http://library.gnome.org/devel/gtk/unstable/GtkSettings.html](http://library.gnome.org/devel/gtk/unstable/GtkSettings.html)

---

