---
title: "Installing Fonts for Ubuntu 10.10"
date: 2011-03-12
forum: General Help
---

### Post by kloakenratte on 2011-03-12
Hi!

I copied my old Font folder from my Windows. There are *tff files and also *.fon files in it. Do somebody know if the *.fon files are also Fonts or do I have to delete it? I wanna install my Fonts on my Ubuntu. Is there an easy way to do this? Thank you!

Sandy

---

### Post by turtle153 on 2011-03-12
You can copy fonts to **/usr/share/fonts** and put the truetype fonts in the appropriate folder.

---

### Post by tredegar on 2011-03-12
... and once you have moved to fonts to **/usr/share/fonts/whatever** you should run```
sudo fc-cache -f -v
``` to update the font cache.

---

