---
title: "ati x1200 driver"
date: 2011-07-10
forum: General Help
---

### Post by smile-its-smiley on 2011-07-10
Does any one know of an driver for the ATI x1200 graphics card? I believe this is stopping me from logging in.

---

### Post by mali2297 on 2011-07-10
The card should work with either the [open-source driver](https://help.ubuntu.com/community/RadeonDriver) or the [proprietary driver](https://help.ubuntu.com/community/BinaryDriverHowto/ATI). Both are available in the repositories.

What do you mean when you say that you cannot log in? Have you tried to start a fail-safe session? (I think there is an option like that if you look through the menus on the login screen.)

---

### Post by Mark Phelps on 2011-07-10
If you're running an Ubuntu version newer than 8.10, there is NO proprietary driver available -- from ANYWHERE!

AMD/ATI dropped proprietary support for your card YEARS ago.

The only driver available now is the open-source -- and it is installed by default with Ubuntu.

---

### Post by smile-its-smiley on 2011-07-12
Basicly when i log in in anything other than Ubuntu safe mode and classic (no effect) mode. I cant log in. The screen just jams on the desktop background and plays the login sound. I'm using 11.04.

I believe it may be caused by my graphics card, allthough im not 100% certain.

---

### Post by mali2297 on 2011-07-12
> **smile-its-smiley said:**
> Basicly when i log in in anything other than Ubuntu safe mode and classic (no effect) mode. I cant log in. The screen just jams on the desktop background and plays the login sound. I'm using 11.04.

I believe it may be caused by my graphics card, allthough im not 100% certain.

I agree with your analysis. 

According to Mark, your only option is the open-source driver. Make sure that it is installed and that any proprietary driver is uninstalled so that there will not be a conflict. Perhaps the link I gave you in the earlier post can give you some guidance.

---

### Post by Mark Phelps on 2011-07-13
> **smile-its-smiley said:**
> Basicly when i log in in anything other than Ubuntu safe mode and classic (no effect) mode. I cant log in. The screen just jams on the desktop background and plays the login sound. I'm using 11.04.

I believe it may be caused by my graphics card, allthough im not 100% certain.

By default, 11.04 will only run the Unity UI if it determines that the needed graphics support is present. If Ubuntu Classic works (you say that it does), it's most likely that's the best you're going to get using that card.  And, since there are no newer drivers (and won't be any), you're pretty much stuck with what you have now.

---

