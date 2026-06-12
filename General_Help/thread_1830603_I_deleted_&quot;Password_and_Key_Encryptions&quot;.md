---
title: "I deleted &quot;Password and Key Encryptions&quot;  because it's annoying , Is it ok ?"
date: 2011-08-22
forum: General Help
---

### Post by TheLibyanPirate on 2011-08-22
Hi Guys 

I removed "Password and key encryption" from Software Center  because it's annoying , Is it OK ? Even when I tired to remove the passwords from it , remove it from startup , check "All Users" in Wireless connection, keeping the password blank and choosing "Unsafe Storage". It was still annoying and asking for a password over and over again . So I deleted it and I was warned about might not having new updates for Ubuntu desktop . [COLOR=Red]**My question , What does this mean ? Will I have a problem with this ?**[/COLOR]

Thanks in advance
Regards
Muhammad Najem

---

### Post by blazemore on 2011-08-22
It's fine, the back-end Gnome keyring is still there, you just uninstalled the graphic tool for managing it.

---

### Post by TheLibyanPirate on 2011-08-22
> **blazemore said:**
> It's fine, the back-end Gnome keyring is still there, you just uninstalled the graphic tool for managing it.

Thank you very much , but &#1611;what about the warning "you might not get item updates for Ubuntu desktop" ?

---

### Post by mcduck on 2011-08-23
> **TheLibyanPirate said:**
> Thank you very much , but &#1611;what about the warning "you might not get item updates for Ubuntu desktop" ?

Removing a package that belongs to the default install will also result in removing the "ubuntu-desktop"-metapackage. That's not a problem during normal use, you'll still get updates for all your installed packages. However you will definitely want to reinstall that package again before you try to upgrade to new Ubuntu versions.

The "ubuntu-desktop" is an empty package that has all the packages in the default setup marked as it's dependencies. So installing it will install everything that belongs to the default desktop setup. When upgrading to new release this ensures you'll get any new packages that might not exist in the old release, the new stuff would just be added to the metapackage's dependencies and get installed automatically.

(Removing metapackages like this is safe, as package dependencies are one-way mechanic; ubuntu-desktop depends on quite a list of packages, but nothing depends on ubuntu-desktop)

---

### Post by TheLibyanPirate on 2011-08-23
> **mcduck said:**
> Removing a package that belongs to the default install will also result in removing the "ubuntu-desktop"-metapackage. That's not a problem during normal use, you'll still get updates for all your installed packages. However you will definitely want to reinstall that package again before you try to upgrade to new Ubuntu versions.

The "ubuntu-desktop" is an empty package that has all the packages in the default setup marked as it's dependencies. So installing it will install everything that belongs to the default desktop setup. When upgrading to new release this ensures you'll get any new packages that might not exist in the old release, the new stuff would just be added to the metapackage's dependencies and get installed automatically.

(Removing metapackages like this is safe, as package dependencies are one-way mechanic; ubuntu-desktop depends on quite a list of packages, but nothing depends on ubuntu-desktop)

Thank you very much !

---

