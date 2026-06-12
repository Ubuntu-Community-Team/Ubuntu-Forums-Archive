---
title: "Gtk2 MenuItem Underlined Shortcut Letter (=Accel) Please!"
date: 2012-05-24
forum: General Help
---

### Post by ohnonot on 2012-05-24
editing a gtk theme i can set mnemonics, accels and auto-mnemonics (underlined letters and keyboard shortcuts, like _F_ile _E_dit...); no problem there.

however this seems to have an effect only on the menu header (_F_ile _E_dit...)  but when the menu drops down the letters are not underlined - not in  synaptic, transmission, thunar, pcmanfm, gdevilspie, leafpad, lxterminal, xfce4-terminal...
but works in gcalctool, gedit, firefox, ...
(i think this points to gtk2 vs gtk3)

- the shortcuts are there, just invisible! when i press alt-f and then c or q it does close the window. for example.

also see [here]("http://xfce-look.org/content/show.php/creamy+acid?action=content&content=150135") and [here.]("http://ubuntuforums.org/showthread.php?t=762346&highlight=gtk+menu+item+underline")

searching around it seems i'd have to add a few lines to my gtkrc-2.0, or the theme itself. sth like: MenuItem use_underline=true

...can someone point me in the right direction? my search only returns help for writing apps withgtk - not for editing config files.

thanks in advance.

edit: i changed the themes around a bit, using very common ones like clearlooks, but it's always the same in the menus (but not the headers). could this be a problem with gtk2 itself?

PS: this is Xubuntu but it should be the same elsewhere. as i said, i think it applies to gtk2.

---

### Post by ohnonot on 2012-05-27
more searching.
[U]
[this page]("http://developer.gnome.org/gtk/stable/GtkSettings.html")[/U] gives insight, but again i can find only```
gtk-enable-mnemonics = 1
gtk-enable-accels = 1
gtk-auto-mnemonics = 1
```the settings work, but have an effect only on the menu header (which i think, is properly called the menu) - but the submenu that pops up remains unaffected
:-(

[_this page_ ]("http://library.gnome.org/users/user-guide/stable/shortcuts-access.html.en")describes what i want but it's absolute beginner level.
[U]
[Here]("http://developer.gnome.org/gtk/2.24/MenusAndCombos.html") [/U]looks interesting - but i can't translate that into anything i could put into a gtkrc.

---

### Post by ohnonot on 2012-05-30
still no reply?
i heard whitsun was abig holiday in many places so mayb i'd give it just one more bump.

oh and dear admin, is it possible to change the name of the thread from

**Gtk2 MenuItem Underlined Shortcut Letter (=Accel) Please!**

to

**Gtk Underlined Shortcut Letter (Works Only Partly)**

which i think would be more clear. thanks.

---

### Post by ohnonot on 2012-08-06
last try, anybody?

---

### Post by xerostomus on 2012-09-17
This quote is partly wrong:
gtk-enable-mnemonics = 1
gtk-enable-accels = 1
gtk-auto-mnemonics = 1

It should be:
gtk-enable-mnemonics = 1
gtk-enable-accels = 1
gtk-auto-mnemonics = 0

I put it into:
file:///usr/share/themes/Default/gtk-2.0-key/gtkrc
file:///usr/share/themes/Default/gtk-3.0/gtk-keys.css
file:///usr/share/themes/Lubuntu-default/gtk-3.0/settings.ini
file:///usr/share/themes/Lubuntu-default/gtk-2.0/gtkrc

May be it is redundant, but it works now. :-)

---

