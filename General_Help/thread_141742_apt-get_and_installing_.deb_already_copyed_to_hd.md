---
title: "apt-get and installing .deb already copyed to hd?"
date: 2006-03-08
forum: General Help
---

### Post by aosmith on 2006-03-08
is it possible to use aptget to install a .deb file i have saved on my hard drive?

---

### Post by aysiu on 2006-03-08
If it's on your desktop, go to Applications > Accessories > Terminal and type ```
cd Desktop
sudo dpkg -i *.deb
```

---

### Post by byen on 2006-03-08
and if you get any dependency errors while installing a deb using
sudo dpkg -i packagename.deb

You can type 
sudo apt-get -f install
to install all the missing dependencies! Goodluck!

---

