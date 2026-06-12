---
title: "Way to install Kubuntu Desktop Environment to Ubuntu from Kubuntu CD?"
date: 2009-07-13
forum: General Help
---

### Post by rocket16 on 2009-07-13
Hello all. I've just downloaded Kubuntu .iso and added it to a cd. Now, I already have Ubuntu 9.04, and in addtion, I want to try Kubuntu 9.04. But instead of adding them as individual Ones, I want to add Kubuntu environment to Ubuntu, such that I can enjoy the flexibility of Ubuntu and the beauty of KDE. Is there a way to do it, or should I have to download the KDE package from Internet seperately?

---

### Post by Celauran on 2009-07-13
You'll need to grab the packages separately. The liveCDs contain an install image, no actual packages.

---

### Post by aysiu on 2009-07-13
You can add it through the CD only if you got the Kubuntu **Alternate** CD.

The Kubuntu **Desktop** CD cannot be used to add Kubuntu to Ubuntu.

With the Desktop CD, you can install Kubuntu over Ubuntu (erasing Ubuntu completely), you can run Kubuntu as a live session (in RAM, no installation), you can install Kubuntu as a dual-boot with (next to) Ubuntu. But you cannot just add it to Ubuntu.

Alternate CD or broadband internet connection.

---

### Post by ajgreeny on 2009-07-13
Just use ```
sudo apt-get install kubuntu-desktop
```, then choose from the **Options > Change session** menu in GDM.

Just a warning.  It makes your menus rather untidy, but you can deal with that, and often the kubuntu usplash takes over from ubuntu's version, which is no disaster, but annoys some people, who prefer to keep the ubuntu's.  Again it can be changed back quite easily, but don't be surprised if some things you didn't expect change their looks.

---

### Post by aysiu on 2009-07-13
> **ajgreeny said:**
> Just use ```
sudo apt-get install kubuntu-desktop
```, then choose from the **Options > Change session** menu in GDM.

Just a warning.  It makes your menus rather untidy, but you can deal with that, and often the kubuntu usplash takes over from ubuntu's version, which is no disaster, but annoys some people, who prefer to keep the ubuntu's.  Again it can be changed back quite easily, but don't be surprised if some things you didn't expect change their looks.
Yes, that works, but it doesn't use the Kubuntu Desktop CD. It uses your internet connection.

As I said before, if you want to add Kubuntu to Ubuntu, you need either the Kubuntu Alternate CD or a broadband internet connection.

---

