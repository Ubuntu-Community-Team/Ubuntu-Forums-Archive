---
title: "installed fonts don't show up in aps"
date: 2006-06-21
forum: General Help
---

### Post by dr.drake on 2006-06-21
I'm using Kubuntu.
usually I install about 1000 fonts from my windows OS onto my Ubuntu OS usinh the font installer and all works fine.

after I installed Dapper again this week, suddenly the fonts I installed don't show up anywhere.
they don't show up in open office or the gimp, but also not in the fonts list when I want to change the apearance.
the installed msttcorefonts DO show up, but not my installed fonts.

when I run the font installer again, it tells me all the fonts are already installed...
(but they don't show).

anybody any suggestions on how to get fonts working again?
I kinda need them for some design stuff.

thanks

---

### Post by soze on 2006-06-21
Have you tried:
```
sudo fc-cache
```

---

### Post by dr.drake on 2006-06-24
I just did, no change.
what did this command do?

---

### Post by drtvasudevan on 2006-06-25
[QUOTE=dr.drake]I just did, no change.
what did this command do?[/QUOTE]
did a man fc-cache
fc-cache scans the font directories  on  the  system  and  builds  font
       information  cache  files  for  applications using fontconfig for their
       font handling.

       If directory arguments are not given, fc-cache uses each  directory  in
       the  current  font  configuration.  Each  directory is scanned for font
       files readable by FreeType.  A cache is created which contains  proper&#8208;
       ties  of  each font and the associated filename.  This cache is used to
       speed up application startup when using the fontconfig library.

---

