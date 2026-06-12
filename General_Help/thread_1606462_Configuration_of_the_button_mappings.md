---
title: "Configuration of the button mappings"
date: 2010-10-26
forum: General Help
---

### Post by Ewgenijkkg on 2010-10-26
Hello! Is it possible to configure button mappings for the mouse in maverick? It was possible in debian. But I tried the option "ButtonMappings" in xorg.conf in Maverick, and it seems to have no influence at all...

BR
Ewgenij

---

### Post by DirtyPC on 2010-10-26
Sorry, could you be more specific? In Button Mappings for Desktop Effects? If so, than yes you can, you press combination and press all the buttons you want in that combination, then press enter.

---

### Post by Ewgenijkkg on 2010-10-26
OK, actually, it is about disabling the middle button of the mouse :) In Debian I just mapped it to the button 9. Since there is no button 9, the button was disabled. But in Ubuntu the option did not work out :((( Or maybe it should be another format?

And what were you talking about? I did not understand :)

---

### Post by Ewgenijkkg on 2010-10-27
Nobody knows? :(

---

### Post by Ewgenijkkg on 2010-10-29
OK, I was told a good solution which worked. Just added the following section to my /etc/X11/xorg.conf

Section "InputClass"
Identifier "DisableWheelButton"
MatchIsPointer "on"
Option "ButtonMapping" "1 9 3 4 5"
EndSection

Here is the link to the thread where my question was answered:

[[COLOR=#444444]http://lists.freedesktop.org/archive...er/051578.html[/COLOR]]("http://lists.freedesktop.org/archives/xorg/2010-October/051578.html")

---

