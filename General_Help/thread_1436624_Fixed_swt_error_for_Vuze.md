---
title: "Fixed swt error for Vuze"
date: 2010-03-22
forum: General Help
---

### Post by 98cwitr on 2010-03-22
Been beating my head against a brick wall for the past hour but finally figured it out. Damn 10.04 is killing me...beta FTL.


Short version:
> 
sudo apt-get remove azureus
sudo apt-get remove vuze
sudo apt-get remove libswt-gtk-3.5-java
cd /usr/share/java
**remove anything swt* related**

sudo apt-get install libswt-gtk-3.5-java vuze

in a nutshell this is what I did

---

