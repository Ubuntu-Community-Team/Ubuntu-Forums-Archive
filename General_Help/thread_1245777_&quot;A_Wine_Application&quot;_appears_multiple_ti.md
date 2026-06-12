---
title: "&quot;A Wine Application&quot; appears multiple times under &quot;Open With&quot;"
date: 2009-08-20
forum: General Help
---

### Post by picpak on 2009-08-20
Hello everyone, today I have an unusual problem. Whenever I right-click a file and go to Open With > Open With Other Application, "A Wine Application" appears as an option about 40 times. I've attached a screenshot of it to show you what I mean.

Does anyone know what's happening? Maybe my Wine install is corrupt? If so, can anyone help me?

---

### Post by picpak on 2009-08-23
bump

---

### Post by khelben1979 on 2009-08-23
Maybe you should reinstall the wine application? Do Wine work over there?

---

### Post by picpak on 2009-08-25
Well, I found the culprit: under ~/.local/share/applications, there are dozens of wines with the names wine-extension-*.desktop. With those removed, "Open With" works as it should.

Thanks for your help!

---

### Post by pazuzuthewise on 2010-07-31
> Well, I found the culprit: under ~/.local/share/applications, there are dozens of wines with the names wine-extension-*.desktop. With those removed, "Open With" works as it should.
------------------------------------------------------------------
   I've got the same strange behavior after installing "Windows Media Player" with the winetricks script (under playonlinux), possibly because the damned thing tried to register itself as the default application for lots of multimedia file types (I quickly deleted it). 
   Deleting these "wine-extension-*.desktop" files fixed the "Open with other application" menu. 
   Take care that not all *.desktop files from that directory have to be deleted (there are also useful ones), only those with the above-mentioned naming pattern.

---

### Post by kelvin.illa on 2010-08-14
> **picpak said:**
> Well, I found the culprit: under ~/.local/share/applications, there are dozens of wines with the names wine-extension-*.desktop. With those removed, "Open With" works as it should.

Thanks for your help!

Just "thanks."

---

### Post by yugo4k on 2010-08-25
Yeah, thank you. :)

---

### Post by lunatico on 2010-09-21
> **picpak said:**
> under ~/.local/share/applications, there are dozens of wines with the names wine-extension-*.desktop. With those removed, "Open With" works as it should.


:guitar: you rock.

---

