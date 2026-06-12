---
title: "image format not recognized"
date: 2006-05-24
forum: General Help
---

### Post by shredfitz on 2006-05-24
Could someone please explain why when I go to view a .jpg file that is on my wife's xp machine that is on the same network as my ubuntu machine, I get an error telling me that the image format is not recognized, yet I can copy the image and paste it on my machine and it is still a .jpg file and I can view it perfectly normally ?   

I also try to click on it and choose view in firefox as an option and it tells me that "firefox doesn't know how to open this address because the protocol (smb) isn't associated with any program.

---

### Post by an.echte.trilingue on 2006-05-24
To browse an smb network, you need a browser than can handle that, which firefox is not.  Try to install tksmb (for GNOME) or smb4k (for KDE) and see if that works.  

What have you tried to open the file with?

---

### Post by shredfitz on 2006-05-24
Before I tried to view the file in a browser, I simply tried to view it with the image viewer, either image viewer or gthumb image viewer.

---

### Post by an.echte.trilingue on 2006-05-24
My guess would be that the browser you are using can't handle smb shares 100%;  try to do this with tksmb (that is what I use).

---

