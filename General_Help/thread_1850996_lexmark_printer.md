---
title: "lexmark printer"
date: 2011-09-27
forum: General Help
---

### Post by cragtom on 2011-09-27
can you get linux driver for the lexmark x74/75 printer scanner ?

---

### Post by wolfen69 on 2011-09-27
Go to the Lexmark website and see if there is one available for download.

---

### Post by wolfen69 on 2011-09-27
There is no driver available at lexmark.com unfortunately. But, I did find a linux driver for it [here]("ftp://ftp.pbone.net/mirror/carroll.cac.psu.edu/pub/linux/distributions/mandrakelinux/official/2009.0/SRPMS/main/release/cups-drivers-lxx74-0.8.4.2-5mdv2009.0.src.rpm"). You will need to convert the .rpm file to a .deb file using alien. Then *hope* it works. You may be out of luck if that doesn't work.

On a side note, all new(ish) Lexmark printers now come with linux drivers. But I always buy HP because 99% of the time they are plug and play.

---

### Post by wolfen69 on 2011-09-27
Just in case you are not familiar with alien, just do:
```
sudo apt-get install alien
```
then put the rpm file you downloaded into your home folder. Then
```
sudo alien cups-drivers-lxx74-0.8.4.2-5mdv2009.0.src.rpm
```
you should now see another file with a .deb extension. Click to install.

---

