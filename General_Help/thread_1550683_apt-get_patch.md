---
title: "apt-get patch"
date: 2010-08-11
forum: General Help
---

### Post by cmstackar on 2010-08-11
Searched all over for this, but couldn't find it. I'm trying to patch a kernel on an embedded machine running 10.04, and the patch is required to get touch, wifi, bluetooth, etc. working. However, I can't install the patch because the packages required to do so aren't isntalled, so it tells me to do apt-get install patch. Anyway to get it installed via another computer?

---

### Post by Earl_Maroon on 2010-08-11
You can download packages straight from the internet - packages.ubuntu.com - and install them with the command

```
sudo dpkg -i path/to/packages/*.deb 
```

That's providing you can get the files onto your laptop.

You need to manually make sure that you have all of the dependencies sorted though. Using the asterisk wildcard you should be able to easily install them all with one command provided they are all in the same folder.

---

