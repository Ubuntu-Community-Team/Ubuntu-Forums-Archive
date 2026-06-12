---
title: "Windows Manager Help..."
date: 2011-05-20
forum: General Help
---

### Post by galacticaboy on 2011-05-20
I tried to install Emerald theme manager on Ubuntu 11.04 and it did not go to well, I was told to do this command in a terminal 'compiz --replace --emerald &' and I got what is in the screenshot below. The bar at the top of my windows is gone, I just want it back, forget about Emerald. Can someone help?

---

### Post by matt_symes on 2011-05-20
Hi

In the terminal type

```
unity --replace &
```

Kind regards

---

### Post by galacticaboy on 2011-05-20
Are you sure it is Unity? Because Xubuntu does not use unity...

---

### Post by linuxinstalledfromhdd on 2011-05-20
If you are in Unity, switch over to classic gnome and see what it looks like from there..

Click on top left corner of Unity. Type in the search box for Login.  Unlock. And select from the dropdown menu Ubuntu Classic. And exit to  save. Reboot to make sure the changes have taken effect.

---

### Post by galacticaboy on 2011-05-20
> **matt_symes said:**
> Hi

In the terminal type

```
unity --replace &
```

Kind regards

I tried that and since Xubuntu uses XFCE and not Unity, it did not work.

---

### Post by matt_symes on 2011-05-20
Hi

I missed the fact you were on xubuntu. I think it must be past my bed time ;)  After all you did say

> I tried to install Emerald theme manager on Ubuntu 11.04 and it did not go to wellAnyways, try

```
compiz --replace &
```Kind regards

---

### Post by galacticaboy on 2011-05-20
> **linuxinstalledfromhdd said:**
> If you are in Unity, switch over to classic gnome and see what it looks like from there..

Click on top left corner of Unity. Type in the search box for Login.  Unlock. And select from the dropdown menu Ubuntu Classic. And exit to  save. Reboot to make sure the changes have taken effect.

I am not in Unity... I have Xubuntu not Ubuntu, Xubuntu uses XFCE not unity...

---

### Post by galacticaboy on 2011-05-20
> **matt_symes said:**
> Hi

I missed the fact you were on xubuntu. I think it must be past my bed time ;)  Try

```
compiz --replace &
```

Kind regards

Haha that is ok, when I tried compiz --replace & it tells me that it could not load the plugin 'ccp'

---

### Post by galacticaboy on 2011-05-20
I got it! After some intense googling I entered into the terminal 'xfwm4 --display=:0.0 --replace' and it brought back the window decoration. Thanks for all of the help though!

---

