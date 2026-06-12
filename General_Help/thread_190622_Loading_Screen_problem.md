---
title: "Loading Screen problem"
date: 2006-06-06
forum: General Help
---

### Post by KevRus on 2006-06-06
I recently upgraded to Dapper and everything is running fine for the most part.

This problem didn't just start with the upgrade, it was also occurring with Breezy.

The screen where Ubuntu is booting up shows Kubuntu instead of Ubuntu, but once it's finished, everything is Gnome.  This is why it isn't so much a problem as it is an annoyance.  Why does my boot screen show Kubuntu and how can I change it back to Ubuntu?  Thanks!:wink:

---

### Post by Ramses de Norre on 2006-06-06
```
sudo update-alternatives --config usplash-artwork.so
```
and pick the right option.

---

### Post by KevRus on 2006-06-06
Thank you! :D

---

### Post by cleentrax on 2006-06-06
I had the same problem with Xubuntu.

The above suggestion will work for the initial splash, and there is a gui tool in gnome to change the login screen. But I still can't figure out how to get rid of the  Xubuntu blue in between the splash and login, and  after the login.

---

### Post by Ramses de Norre on 2006-06-06
I have that blue too without ever having xubuntu installed.. I've been wondering were it comes from..

---

