---
title: "installed ttf-mscorefonts-installer and still no microsoft fonts?"
date: 2012-07-18
forum: General Help
---

### Post by fishball on 2012-07-18
I ran > sudo apt-get install ttf-mscorefonts-installer and it said I already had the most up to date version, yet I don't see Times New roman or arial under libreoffice.  Suggestions?

---

### Post by mike555 on 2012-07-18
You could go to;  [http://flippingtypical.com/](http://flippingtypical.com/)   ... to see if you have them installed.

---

### Post by princeofnam on 2012-07-18
Hmm.  Looks like I do.  Not sure why the fonts aren't chooseable in LibreOffice strangely.

---

### Post by drmrgd on 2012-07-18
Not sure this will fix it, but you could try updating the font cache:

```
sudo fc-cache
```

Looks like the stock MS fonts are showing up in Libre Office for me.

---

### Post by princeofnam on 2012-07-18
woo

---

### Post by fishball on 2012-07-18
woo

---

### Post by drmrgd on 2012-07-18
Heh!  I take it that worked :)

---

