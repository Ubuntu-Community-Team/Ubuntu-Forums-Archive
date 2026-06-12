---
title: "Aplications-&gt;Add Aplications"
date: 2006-05-05
forum: General Help
---

### Post by ampop on 2006-05-05
When I go to the bar: Aplications->Add Aplications (I directly translate from my Portuguese Ubuntu, not sure if in the English version it's like this ).
I put the password and nothing happens. What should be the problem?
Thank you.

---

### Post by aysiu on 2006-05-06
I don't know, but someone else may be able to help you if you go to Applications > Accessories > Terminal, type ```
gksudo gnome-app-install
``` and then post the output here.

---

### Post by ampop on 2006-05-06
[QUOTE=aysiu]I don't know, but someone else may be able to help you if you go to Applications > Accessories > Terminal, type ```
gksudo gnome-app-install
``` and then post the output here.[/QUOTE]

I had this mesage:
"  File "/usr/bin/gnome-app-install", line 41, in ?
    from AppInstall import AppInstall
  File "/usr/lib/gnome-app-install/AppInstall.py", line 30, in ?
    import gtkmozembed
ImportError: libgtkembedmoz.so: cannot open shared object file: Arquivo ou diretório não encontrado"

Arquivo ou diretório não encontrado=file or directory not found

Thanks.

---

### Post by ampop on 2006-05-06
Any idea? Please.

---

### Post by aysiu on 2006-05-06
[QUOTE=ampop]Any idea? Please.[/QUOTE] Maybe [this](http://www.ubuntuforums.org/showthread.php?t=134046) might help?

---

### Post by ampop on 2006-05-06
[QUOTE=aysiu]Maybe [this](http://www.ubuntuforums.org/showthread.php?t=134046) might help?[/QUOTE]

Ok, it's explained. It was the firefox1.5 installation.
Thanks for the help.

---

### Post by ampop on 2006-05-07
It's done. 	=D>
I removed Firefox 1.5, installed Firefox 1.0.8 and gnome-app-install. Eureka it works. A problem like this on a Windows system, and I should format the disk and reinstall all the system.
:D :D :D

---

