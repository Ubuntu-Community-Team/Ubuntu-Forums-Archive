---
title: "installing themes"
date: 2010-11-25
forum: General Help
---

### Post by arunthakurmanali on 2010-11-25
hey guys,i just downloaded a theme from gnome-look.org,it was .tar.gz file.iextracted it but couldn't find any config or make file.can anyone help me to install those themes

---

### Post by dino99 on 2010-11-25
here is how to get a "deb" from a "tar.gz"

sudo apt-get install alien

then goto this tar.gz folder and:

sudo alien -k filename.tar.gz

then doubleclick on the new deb file to install it (gdebi need to be installed)

---

### Post by qamelian on 2010-11-25
> **arunthakurmanali said:**
> hey guys,i just downloaded a theme from gnome-look.org,it was .tar.gz file.iextracted it but couldn't find any config or make file.can anyone help me to install those themes
You don't need to extract it. You should be able to just open the Appearance applet from the Preferences menu, then drag and drop the tar.gz archive onto the Appeance box. This should automatically install the theme. Alternately, you can use the install button in the applet.

---

### Post by Frogs Hair on 2010-11-25
If you want use the gui open appearance preferences select install navigate to downloads select and open the package. This will work a tar.gz but a zip file will have to be extracted first.

---

### Post by aeiah on 2010-11-25
i always extract themes to the .themes directory. its an old habit from when most themes would break when you threw them at the theme manager i guess.

if you extract it to .themes, it'll show up in whatever theme manager you use

---

### Post by arunthakurmanali on 2010-11-25
isn't Alien for converting rpm packages to dev

---

