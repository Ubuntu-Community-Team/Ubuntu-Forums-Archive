---
title: "NO unity install after upgrade to 12.04"
date: 2012-05-20
forum: General Help
---

### Post by Chacho on 2012-05-20
I upgrade to ubuntu 12.04, i have an laptop acer travelmate 8200.
The problem is that I have no unity, and I do not know how to intall gnome, I tried 
sudo apt-get install gnome , and download it but it is not working.

Any help is welcome !

I am a user for a year...but I am new to almost every thing..

---

### Post by wilee-nilee on 2012-05-20
> **Chacho said:**
> I upgrade to ubuntu 12.04, i have an laptop acer travelmate 8200.
The problem is that I have no unity, and I do not know how to intall gnome, I tried 
sudo apt-get install gnome , and download it but it is not working.

Any help is welcome !

I am a user for a year...but I am new to almost every thing..

For the gnome-shell
```
sudo apt-get install gnome-shell
```Did you have unity before the upgrade?

What was the desktop you had if not, and did you tweak whatever the install was.

Did you upgrade from a broken set-up trying to fix it?

---

### Post by loklaan on 2012-05-20
Try to reinstall unity:
```
sudo apt-get install --reinstall unity
```

You can select installed desktop environments for use at the login screen. :)

---

### Post by wilee-nilee on 2012-05-20
> **loklaan said:**
> Try to reinstall unity:
```
sudo apt-get install --reinstall unity
```You can select installed desktop environments for use at the login screen. :)

Unity is the ubuntu-desktop basically

```
sudo apt-get install ubuntu-desktop
```

---

### Post by loklaan on 2012-05-20
> **wilee-nilee said:**
> Unity is the ubuntu-desktop basically

The [ubuntu-desktop]("http://packages.ubuntu.com/precise/ubuntu-desktop") is a metapackage, and it includes alot more then Unity.

Is it safer to install then the single unity package?

---

### Post by wilee-nilee on 2012-05-20
> **loklaan said:**
> The [ubuntu-desktop]("http://packages.ubuntu.com/precise/ubuntu-desktop") is a metapackage, and it includes alot more then Unity.

Is it safer to install then the single unity package?

To be honest advising to install anything is not really a good idea, finding out what has happened is better approach first. Unity runs in gnome 3 in compiz, we don't know what was there to begin with.

---

