---
title: "HOW TO: Make your Ubuntu desktop slick and clean"
date: 2011-08-10
forum: General Help
---

### Post by Spyderkid on 2011-08-10
[COLOR="Blue"][SIZE="3"][SIZE="4"]This is a tutorial on how to make your desktop look clean and slick....
[/SIZE][/SIZE][/COLOR]

_**[COLOR="blue"]1)First thing....[/COLOR]**_
  [COLOR="SeaGreen"]install a nice background. (there's three in the attachments.)[/COLOR]

_**2)do a quick hack to get rid of the nasty panel when you try to add a background image or make it bigger**_
[IMG]http://cdn.omgubuntu.co.uk/wp-content/uploads/2011/02/Selection_0019.png[/IMG]
  [COLOR="Red"]to do this you need to do a simple hack...

      >gksu gedit /usr/share/themes/Ambiance/gtk-2.0/gtkrc
      >gedit will open
      >hold <Ctrl + F> to open the find bar
      >Enter apps/gnome-panel.rc
      >Enter a hash (#) at the beginning of the line to ‘comment it out’. (it should look like below...)[/COLOR]
[IMG]http://cdn.omgubuntu.co.uk/wp-content/uploads/2011/02/Selection_0032.png[/IMG]


_**[COLOR="Blue"]3)Add a nice panel image background[/COLOR]**_
  (panel background in attachment below its called panel background.[COLOR="Red"]**just extract the file and set as panel background!**[/COLOR])

[COLOR="blue"]_**4) OPTIONAL: install gnomenu and a not to brash theme...**_[/COLOR]
  
   [COLOR="DarkOrange"]to install...
```

sudo add-apt-repository ppa:gnomenu-team/ppa
sudo apt-get update

```

then install some nice themes...
I've added a .tar with a menu theme and a button theme in.
just extract and copy the button theme to /usr/share/gnomenu/Themes/Button
and the other menu theme to
/usr/share/gnomenu/Themes/Menu
[/COLOR]

---

### Post by Bart92 on 2011-08-10
Old inf.

---

### Post by Spyderkid on 2011-08-10
old inf?

what i've posted still works and applies to 11.04

---

### Post by Bucky Ball on 2011-08-10
How do you make your desktop slick and clean? Use Xfce, no icons, and shortcut keys for everything. Choose whatever background you like. ;)

---

