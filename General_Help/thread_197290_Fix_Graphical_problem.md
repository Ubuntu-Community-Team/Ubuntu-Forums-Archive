---
title: "Fix Graphical problem"
date: 2006-06-15
forum: General Help
---

### Post by playmobiel on 2006-06-15
Look at the screenshot inculed , does anybody know how to fix this?

Thanks

---

### Post by dlpfmVfH on 2006-06-16
did you set a gtk1 theme in System Preferencess themes....
try and set it back to original human theme...

and look in you're home folder for .gtk files...
if there are any...(maybe because you started kde) remove those...
.gtkrc-1.2 or .gtkrc...

---

### Post by playmobiel on 2006-06-16
its a GTK 2.x Theme/Style , i set theme back yo ubuntu , removed .gtkrc-1.2-gnome2 and tried the theme again , same results

---

### Post by dlpfmVfH on 2006-06-16
[QUOTE=playmobiel]its a GTK 2.x Theme/Style , i set theme back yo ubuntu , removed .gtkrc-1.2-gnome2 and tried the theme again , same results[/QUOTE]


strange, I tried setting gnome-panel to a diff color,
make it transparent, adding a image to the back,
and couldn't replicate you're picture...

---

### Post by dlpfmVfH on 2006-06-17
Ok, got something...

I installed the new rezlooks engine, in dapper,
and I got the same look as you...

My solution...very simple but not a definitive fix...

open gnome-panel and set the background color to the same colour as the panel-bar. than adjust the slider for transparancy to no transparancy...

and voila you're menu behaves.

hope this will help.

---

### Post by giuliastro on 2006-06-17
Gnome-panel transparency doesn't work fine, you need to disable it.

---

### Post by playmobiel on 2006-06-22
yes i found it, i replaced it with a menu button , thanks

---

