---
title: "Accidentaly deleted my usr&gt;share&gt;fonts directory."
date: 2011-11-01
forum: General Help
---

### Post by strawfoot on 2011-11-01
I accidentally deleted my usr>share>fonts directory.  How can I get these files back?  all the text on my compy is showing up as little boxes instead of letters which makes normal operations a bit difficult.  Would be nice if I could find a replacement and just drop it into the file folder.  Running the newest ubuntu release, oneiric.

Thanks!

---

### Post by strawfoot on 2011-11-01
Just a location of where to get the files would be all I need... trying to avoid a reinstall here, any help is appreciated greatly.

---

### Post by thatguruguy on 2011-11-01
Check to see if ubuntu-desktop is installed.

You could also reinstall the ubuntu-font-family in Synaptic or the Ubuntu Software Center, as well as whatever fonts you use.  I think it will set up the folder automatically.

---

### Post by Jaybyrrd on 2011-11-01
Just taking a wild guess, but if this is a fonts issue that involves synaptic then you could probably sudo apt-get update in terminal, and that should fix it. Maybe. I don't know just a guess. Good luck!

---

### Post by crdlb on 2011-11-01
Can you get to a console with ctrl+alt+F1? I don't think the linux console fonts are stored in that directory, so it should still work. From there ```
sudo apt-get install --reinstall ttf-dejavu-core ttf-ubuntu-font-family
``` might be enough to get going again.

The full list of packages owning files in /usr/share/fonts/ on my system is:
> $ dpkg -S /usr/share/fonts/
fonts-arabeyes, xfonts-100dpi, xfonts-75dpi, ttf-sil-andika, ttf-sil-doulos, ttf-dejavu-extra, ttf-ubuntu-font-family, ttf-lyx, ttf-droid, ttf-liberation, ttf-kacst-one, ttf-thai-tlwg, ttf-kannada-fonts, ttf-lao, xfonts-encodings, ttf-wqy-zenhei, ttf-umefont, ttf-vlgothic, ttf-arphic-uming, cmap-adobe-japan1, xfonts-base, ttf-telugu-fonts, ttf-wqy-microhei, xfonts-mathml, ttf-sazanami-mincho, ttf-bengali-fonts, ttf-opensymbol, ttf-devanagari-fonts, ttf-gujarati-fonts, ttf-indic-fonts-core, xfonts-scalable, gs-cjk-resource, ttf-oriya-fonts, ttf-punjabi-fonts, ttf-takao-pgothic, ttf-tamil-fonts, ttf-sazanami-gothic, gsfonts, fonts-cantarell, ttf-khmeros-core, ttf-kacst, ttf-kochi-gothic, ttf-kochi-mincho, ttf-unfonts-core, ttf-sil-gentium-basic, ttf-sil-gentium, gsfonts-x11, ttf-dejavu-core, ttf-freefont, xfonts-utils: /usr/share/fonts

You could run the same command to get a list of packages to reinstall for your system.

---

### Post by strawfoot on 2011-11-01
Thanks so much, that's exactly what I needed.  No more sudo for me... I just get myself in trouble.

Also, thanks to everyone on these Ubuntu forums for making the ubuntu community such an awesome place and allowing me to use the best OS around.:)

---

