---
title: "Adding New Fonts?"
date: 2010-01-31
forum: General Help
---

### Post by savaan on 2010-01-31
I'm not trying to change fonts on my desktop, I'm wanting to add new fonts that I find online for use in GIMP, Office and other programs. Is there a way to do this? I keep finding threads on how to change fonts for the desktop but none on how to add new ones :(

---

### Post by BUSHYBOB on 2010-01-31
Create a .fonts folder in your home directory and bung them in there.

---

### Post by m_duck on 2010-01-31
You will also want to run the following after putting the fonts in that folder.```
fc-cache -vf
```This refreshes the font cache so the computer can find the new fonts.

---

### Post by SuperSonic4 on 2010-01-31
> **m_duck said:**
> you will also want to run the following after putting the fonts in that folder.```
fc-cache -vf
```this refreshes the font cache so the computer can find the new fonts.

+1

---

### Post by savaan on 2010-01-31
Great :) It's easier than I thought it would be. Thanks!

---

