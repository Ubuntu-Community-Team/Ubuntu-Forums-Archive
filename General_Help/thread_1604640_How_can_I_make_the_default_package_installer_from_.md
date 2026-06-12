---
title: "How can I make the default package installer from lucid, be the default in maverick?"
date: 2010-10-24
forum: General Help
---

### Post by Mr_VeRiTy on 2010-10-24
Hi, in maverick the default package installer (when I double click on a .deb) is Ubuntu Software Centre, how can I make the default package installer from lucid (was it called "dpkg"?) the default again? Ubuntu Software Centre is too slow and freezes every time I click on something, can it be replaced?

---

### Post by drs305 on 2010-10-24
You may have used GDebi, a simple .deb installer:
```
sudo apt-get install gdebi
```

Then find a .deb file in your file browser, right click on it, "Open with", and choose "GDebi Package Installer". Tick the bottom right "Remember this application..."

If GDebi isn't listed as an 'Open With' option, click on the "Use a custom command" and type in "gdebi-gtk".

---

### Post by Mr_VeRiTy on 2010-10-24
> **drs305 said:**
> You may have used GDebi, a simple .deb installer:
```
sudo apt-get install gdebi
```

Then find a .deb file in your file browser, right click on it, "Open with", and choose "GDebi Package Installer". Tick the bottom right "Remember this application..."

If GDebi isn't listed as an 'Open With' option, click on the "Use a custom command" and type in "gdebi-gtk".
This works, thanks XD.

---

