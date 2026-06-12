---
title: "Unity and Eclipse"
date: 2011-05-07
forum: General Help
---

### Post by jdunn on 2011-05-07
I'm using the version of Eclipse from the repositories in Ubuntu 11.04 with the Unity shell.  The scrollbars don't work properly.  Does anyone know of a fix for this?

---

### Post by JRV on 2011-05-07
Is it a problem with the new overlay scrollbars in Unity?

To disable the overlay scrollbars:
```
sudo apt-get remove overlay-scrollbar
sudo echo "export LIBOVERLAY_SCROLLBAR=0" > /etc/X11/Xsession.d/80overlayscrollbars
```
   

to re-install the overlay scrollbars:
```
sudo apt-get install overlay-scrollbar
sudo rm /etc/X11/Xsession.d/80overlayscrollbars

```

---

### Post by jdunn on 2011-05-08
> **JRV said:**
> Is it a problem with the new overlay scrollbars in Unity?

To disable the overlay scrollbars:
```
sudo apt-get remove overlay-scrollbar
sudo echo "export LIBOVERLAY_SCROLLBAR=0" > /etc/X11/Xsession.d/80overlayscrollbars
```
   

to re-install the overlay scrollbars:
```
sudo apt-get install overlay-scrollbar
sudo rm /etc/X11/Xsession.d/80overlayscrollbars

```

Thanks.  Your fix appears to have solved the problem.

---

