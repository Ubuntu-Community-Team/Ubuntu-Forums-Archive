---
title: "Command to delete non-admin software"
date: 2011-02-18
forum: General Help
---

### Post by Cheetah05 on 2011-02-18
This is a bit of a longshot but I was wondering if anyone has a command to delete all the non-admin software from ubuntu. E.g. Openoffice, firefox, media players, photomanagers...

Reason being is that there is an image of ubuntu which is specially optimized for my hardware but its on a standard ubuntu install, where infact all I want is file and printer sharing, chromium and xbmc (with any dependancies). I want the install to be as small as possible so I was wondering if anyone has done this before and knows a one line command for it?

I would try building my own image from ubuntu sever but I think it would take too long.

Thanks

---

### Post by Cheetah05 on 2011-02-18
Well does anyone know where I can get a list of the package names so I can try figuring out which is which.

Say I do it by this method and there are some packages left that don't depend on anything else and are not needed (were installed to be able to use OpenOffice for instance)....how would I find and delete these?

---

### Post by TeoBigusGeekus on 2011-02-18
```
dpkg -l > ~/Desktop/installed_packages.txt
```
will create a file on your desktop with all your installed packages.

```
sudo apt-get autoremove
```
will remove any unrequired dependancies.

---

