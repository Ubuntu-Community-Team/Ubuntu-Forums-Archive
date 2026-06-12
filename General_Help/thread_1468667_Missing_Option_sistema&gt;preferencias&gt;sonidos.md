---
title: "Missing Option sistema&gt;preferencias&gt;sonidos"
date: 2010-05-01
forum: General Help
---

### Post by bdvd on 2010-05-01
Hi,i just install the new ubuntu 10.04, everything works fine, but a few minuts ago  i realize that the option "sistema>preferencias>sonidos" is missing, and i can't find it anywhere, maybe some package is lost or broken but i can't find it :(...

i search google, but i did not find anything, maybe is a new problem or is just my pc.

---

### Post by alfplayer on 2010-05-01
It should be there. The same application can be accessed clicking "Sound Preferences..." (or the spanish language equivalent) after clicking the sound icon on Ubuntu's top panel. You can try that. Also, you may need to enable the menu item (in case it was somehow disabled).

---

### Post by bdvd on 2010-05-01
i already try that, the problem is that clicking the volume button next to the clock appears the volume bar and the preferences button, but when i click it nothing happens :(...

---

### Post by bdvd on 2010-05-01
recien me doy cuenta que sos de buenos aires, en español puedo detallar mas---

el problema es que cuando apreto el boton del volumen al lado del reloj me aparece para bajar y subir el volumen y un boton que dice preferencias, cuando lo aprieto no pasa nada, y cuando vi que no pasaba nada me fui a sistema > preferencias > y busque sonido para ver que pasaba y me di cuenta de que no estaba el boton "sounds o sonido"... busque en varios lugares de la web y no encontre nada, no se que sera, y necesito entrar a esas opciones para seleccionar bien unas opciones de sonido.

---

### Post by alfplayer on 2010-05-01
Se recomienda postear en idioma inglés en este subforo. Te recomiendo que sigas usando inglés para que puedan ayudar todos.

-- 

Posting in English language is recommended on this forum. I suggest you continue to post in English so that everyone can help.

That application is "gnome-volume-control" and is part of "gnome-media" package. It should be installed on every new and unmodified 10.04 installation.

---

### Post by bdvd on 2010-05-02
oh! ok thanks :)!...


i fix the problem, the "sound" option was missed because i remove the package "ubuntu-desktop"... fix it now!

---

### Post by alfplayer on 2010-05-02
You're welcome.

From [http://packages.ubuntu.com/lucid/ubuntu-desktop](http://packages.ubuntu.com/lucid/ubuntu-desktop):

This package depends on all of the packages in the Ubuntu desktop system 
 It is also used to help ensure proper upgrades, so it is recommended  that it not be removed.

---

