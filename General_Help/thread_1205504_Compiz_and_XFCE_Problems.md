---
title: "Compiz and XFCE Problems"
date: 2009-07-06
forum: General Help
---

### Post by jman6495 on 2009-07-06
hi
so,
i installed xfce on ubuntu 9.10 and somehow i enabled compiz,
then, because gnome-panel and my nautilus kept running when i launched xfce,
i ran ```
jordan@laptop > sudo apt-get remove gnome-panel nautilus
```
or something like that, but the gnome panel and nautilus got removed.
now , because xfce takes aaagggeeesss.. to load with compiz , i want to disable it ,xfce's session and startup doesn't work and it wont stop!!!
i have tried changing back to xfwm4 using fusion-icon but nothing works!

any ideas?

jman6495

---

### Post by Bigtime_Scrub on 2009-07-06
To install xfce on ubuntu you run the code

```
sudo apt-get xubuntu-desktop
```

Then you log out and under sessions you choose XFCE.

The code you ran I think, deleted Gnome-panels and Nautilus.

I would try to reinstall it 

```
sudo apt-get install gnome-panel nautilus
```

If you cant open a terminal try to get into a terminal with alt-ctrl+f1

---

### Post by jman6495 on 2009-08-05
> **Bigtime_Scrub said:**
> To install xfce on ubuntu you run the code

```
sudo apt-get xubuntu-desktop
```

Then you log out and under sessions you choose XFCE.

The code you ran I think, deleted Gnome-panels and Nautilus.

I would try to reinstall it 

```
sudo apt-get install gnome-panel nautilus
```

If you cant open a terminal try to get into a terminal with alt-ctrl+f1

thanks

---

