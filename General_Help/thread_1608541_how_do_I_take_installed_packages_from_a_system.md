---
title: "how do I take installed packages from a system?"
date: 2010-10-29
forum: General Help
---

### Post by Dobro_player on 2010-10-29
How do I take installed packages from a system? For example, if I install a package on a computer running Ubuntu, is there a way to copy the installed package to another computer running Ubuntu so I don't have to download it again?

---

### Post by plucky on 2010-10-29
> **Dobro_player said:**
> How do I take installed packages from a system? For example, if I install a package on a computer running Ubuntu, is there a way to copy the installed package to another computer running Ubuntu so I don't have to download it again?

[AptonCD](http://aptoncd.sourceforge.net/) is in the repositories.
```
sudo apt-get install aptoncd
```

This will create an .iso file with all the packages that are stored in /var/cache/apt/archives/ on your system and you can either burn to CD or just copy the .iso file onto a pendrive and transfer it that way to another system.

Good Luck

---

### Post by sisco311 on 2010-10-29
Yes, the packages are downloaded to /var/cache/apt/archives/. 

If you need a GUI tool, check out: [APTonCD]("http://aptoncd.sourceforge.net/") and [Keryx]("http://keryxproject.org/").

---

### Post by Dobro_player on 2010-10-29
Thank-you for your help!

---

### Post by gmargo on 2010-10-29
You can use a caching proxy server such as **approx** or **apt-cacher-ng**.

[http://packages.ubuntu.com/maverick/approx](http://packages.ubuntu.com/maverick/approx)
[http://packages.ubuntu.com/maverick/apt-cacher-ng](http://packages.ubuntu.com/maverick/apt-cacher-ng)

---

