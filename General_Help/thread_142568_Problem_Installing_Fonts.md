---
title: "Problem Installing Fonts"
date: 2006-03-10
forum: General Help
---

### Post by ForeverUnknown on 2006-03-10
I followed the directions here [http://fluxbox-wiki.org/index.php/Howto_install_fonts](http://fluxbox-wiki.org/index.php/Howto_install_fonts) to install Artwiz fonts but I'm unable to use them.  I tried xlsfonts and artwiz isn't listed.  Ideas?

---

### Post by stuporglue on 2006-03-10
```
stuporglue@ubuntoo:~$ apt-cache search artwiz
artwiz-cursor - artwiz futuristic mouse cursor for x11
xfonts-artwiz - x11 fonts created by Artwiz, TigerT, and Daniel Erat

```

Try just doing "sudo apt-get install xfonts-artwiz". It should install them correctly.

---

### Post by ForeverUnknown on 2006-03-10
Well I tried using apt-get and the fonts still don't show up anywhere.

---

### Post by youbaji on 2006-03-10
you may need to restart your X
or you can do this without restart X:
xset +fp "your_fonts_directory"

---

### Post by ForeverUnknown on 2006-03-10
Ok I can no find the installed files but I am still unable to use the fonts...

---

