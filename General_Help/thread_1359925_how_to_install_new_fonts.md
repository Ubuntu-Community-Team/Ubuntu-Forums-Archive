---
title: "how to install new fonts"
date: 2009-12-20
forum: General Help
---

### Post by chitragurung on 2009-12-20
How can I install new fonts which I was using in Windows ?

---

### Post by howefield on 2009-12-20
Open up Synaptic Package Manager and install ttf-mscorefonts-installer (that's for 9.10, this package is called something else for earlier versions) This will install some of the most common ones, Andale Mono,   Arial Black,   Arial (Bold, Italic, Bold Italic)   Comic Sans MS (Bold)   Courier New (Bold, Italic, Bold Italic) Georgia (Bold, Italic, Bold Italic)   Impact,   Times New Roman (Bold, Italic, Bold Italic)   Trebuchet (Bold, Italic, Bold Italic)   Verdana (Bold, Italic, Bold Italic)  Webdings

Also, you can have a read at this

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by nubalci on 2009-12-20
Just copy your fonts from windows partition to ~/.fonts folder (if it is not present, create the folder: note that the name is .fonts). Then, open a terminal and type

sudo fc-cache -fv

(sudo is not necessary actually)

---

