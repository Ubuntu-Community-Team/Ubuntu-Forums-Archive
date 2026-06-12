---
title: "kubuntu-desktop"
date: 2006-02-06
forum: General Help
---

### Post by Zaventh on 2006-02-06
Hi,

I am planning on installing kubuntu on my new laptop shortly. I use kubuntu on other machines and I am wondering if there is any possible way to get around installing kubuntu without using the kubuntu-desktop meta-package since I would rather exclude certain packages such as openoffice, XMMS, and others. Thanks.

---

### Post by newuser111 on 2006-02-06
you can uncheck all the stuff you dont want after selecting kubuntu-desktop

for example you can even uncheck kdm if you want to use gdm instead

you could install meta package "kde" but i think its broken

---

### Post by raublekick on 2006-02-06
Before I knew of the kubuntu-desktop package I installed KDE via the kde package, and it worked. It just doesn't have all of the Kubuntu touches. I would imagine that it doesn't include OpenOffice or anything like that, but I already had them installed when I installed KDE.

So basically, if you don't want the extra stuff from the initial install, just do a server install and then do ```
sudo apt-get install kde
```

---

### Post by newuser111 on 2006-02-06
but keep in mind 'kde' package installs about a dozen different media players and pretty much every extra kde app

---

### Post by Adrian on 2006-02-06
I think the **kde** meta-package contains all official KDE packages, so you don't want to install it if you think **kubuntu-desktop** installs too much stuff.

[http://packages.ubuntu.com/breezy/kde/kde](http://packages.ubuntu.com/breezy/kde/kde)

I think you're more interested in the **kde-core** meta-package. It installs just the necessary programs and libraries (+ aRts sound server).

[http://packages.ubuntu.com/breezy/kde/kde-core](http://packages.ubuntu.com/breezy/kde/kde-core)

If you want to compare the different alternatives, you can search for each meta-package here and see what is included:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

