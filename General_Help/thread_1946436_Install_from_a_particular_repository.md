---
title: "Install from a particular repository"
date: 2012-03-24
forum: General Help
---

### Post by 7o7YlUcb on 2012-03-24
Hi, I need a particular version of an app. The app appears to be included in one of the standard repositories but it is an old version. I have added the repository that includes the bleeding edge version and I want to install the app from this repository. Is there a way to select which repository will be used?

This is what I do:

sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
sudo apt-get update
sudo apt-get install grass

To force it to use this repository, I tried temporarily unchecking the other software sources in the Ubunto software center but then the app failed to install as it seemed to need some dependencies or something from one of these sources.

---

### Post by wildmanne39 on 2012-03-24
Hi, if you ran those three commands one at a time it should be that simple but you will need to have your software sources checked.
Thanks

---

### Post by Rodney9 on 2012-03-24
You have to have it checked in 'Software Sources' otherwise you can't use it.

Rodney

---

