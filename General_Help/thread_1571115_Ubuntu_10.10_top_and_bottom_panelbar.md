---
title: "Ubuntu 10.10 top and bottom panel/bar"
date: 2010-09-09
forum: General Help
---

### Post by rajmahendra on 2010-09-09
Hi 

I am trying with different Docks. Currently i am hiding both top and bottom bar of my Ubuntu. 

I like to remove them completely so my Dock dominate the screen. At the same time i like to bring both the bar later if i need them. 

Any one tell me how to remove the bar and how can i bring the bar again.

---

### Post by nothingspecial on 2010-09-09
```
sudo mv /usr/bin/gnome-panel ~/.panel
```That will move the binary of gnome panel to a hidden file in your home folder

```
sudo mv ~/.panel /usr/bin/gnome-panel
```will put it back

It`s not recommended that you do this but it has worked for me on many different computers and ubuntus

---

### Post by kerry_s on 2010-09-09
gconf-editor-> desktop-> gnome-> session-> required_components
click on panel, double click gnome-panel & make it empty
log out & back in

to put back right click-> unset key

---

