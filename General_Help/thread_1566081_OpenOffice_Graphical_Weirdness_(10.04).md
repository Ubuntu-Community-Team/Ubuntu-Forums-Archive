---
title: "OpenOffice Graphical Weirdness (10.04)"
date: 2010-09-01
forum: General Help
---

### Post by VanCardboardbox on 2010-09-01
I've been searching around but can find no reference to this anywhere. 

The instance of OpenOffice 3.2 in my installation of Lucid shows graphical weirdness in menus, labels, etc.. Patches of colour come and go - sometimes black, totally obscuring text. Text becomes struckthrough, letter and number characters become distorted. Sometimes it appears that multiple characters are stacked in the same spot. 

All components of the suite are affected. No other installed software on the system shows this problem. 

This is the version of OOo from the Ubuntu repositories. I uninstalled it ("Complete Removal") and reinstalled with no change.

Has anyone else seen this?

---

### Post by AlphaLexman on 2010-09-01
Are you using a 'dark' theme in ubuntu? 
OOo has a lot of difficulties with dark themes.

---

### Post by rollin on 2010-09-01
> **AlphaLexman said:**
> Are you using a 'dark' theme in ubuntu? 
OOo has a lot of difficulties with dark themes.

+1
Have you tried installing openoffice.org-gtk? Open Office tends to play nicer with your gtk theme afterwards. Copy and paste this into your terminal:

```
sudo apt-get install openoffice.org-gtk
```

---

