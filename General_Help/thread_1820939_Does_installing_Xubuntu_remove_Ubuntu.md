---
title: "Does installing Xubuntu remove Ubuntu?"
date: 2011-08-08
forum: General Help
---

### Post by knutschr on 2011-08-08
I have Ubuntu and Kubuntu installed.
I can choose which I want to use during login.
I thought I would give Xubuntu a try the same way, but when I in Synaptic mark xubuntu-desktop for installing I get
```
Will be removed:
ubuntu-desktop
```
Does that mean my choices afterwards will be Xubuntu and KDE?

One more question:
If so and I do this, and later remove xubuntu-desktop and reinstalls ubuntu-desktop, will my configuration of Ubuntu still be there?

---

### Post by SalHelder on 2011-08-08
I don't think so, if it will only remove that package alone "ubuntu-desktop" you'll still be able to use Gnome/Unity, KDE and XFCE. What I think will happen is that your loading screen will change to Xubuntu's but you can change that later with Plymouth Manager:

sudo apt-add-repository ppa:mefrio-g/plymouthmanager
sudo apt-get update
sudo apt-get install plymouth-manager

---

### Post by knutschr on 2011-08-08
Thank you!
Now I can choose either Ubuntu, Kubuntu or Xubuntu by login!

---

