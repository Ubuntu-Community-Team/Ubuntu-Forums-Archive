---
title: "Login problem"
date: 2010-11-22
forum: General Help
---

### Post by manosone on 2010-11-22
Hi all,

I tried to login to my 10.04 10 minutes ago but when i type the password and press enter it sends me to login again.
In fact it seems that it loges in for 1 second then showing a blank screen and then it goes back to the login screen.
Username/password are the right one.
I do not know if that matters, but yesterday i reinstalled nautilus(and it works fine).



Any ideas?

Thanks in advance.

PS.If at the login screen i press alt-ctrl-f1 i can login from console but when i press alt-ctrl-f7 in order to go back to x, i return back to login screen even if i am loged in.

---

### Post by searchfgold6789 on 2010-11-22
Try reinstalling xorg.

---

### Post by manosone on 2010-11-23
> **searchfgold6789 said:**
> Try reinstalling xorg.

Thanks for the help.I tried to reinstall nautilus via terminal 
```
sudo apt-get install --reinstall nautilus
```
and also xorg 
```
sudo apt-get install --reinstall xorg
```
but nothing changed.
Then i decided to do an update and an upgrade to the latest kernel
That didnt solved the problem either.
Finally i reinstalled ubuntu-desktop
```
sudo apt-get install --reinstall ubuntu-desktop
```
and that worked.
So i guess i was missing a basic package for the gui.

Thanks to all.
See you around.

---

