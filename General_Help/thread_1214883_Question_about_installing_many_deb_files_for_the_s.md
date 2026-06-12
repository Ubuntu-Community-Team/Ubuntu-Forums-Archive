---
title: "Question about installing many deb files for the same program!"
date: 2009-07-16
forum: General Help
---

### Post by Rytron on 2009-07-16
Hi.
I just downloaded Audacious 2.1 from [getdeb]("http://www.getdeb.net/"). As you can see in the picture [attached] there are five items to install. This can be quite awkward as I have to input my password five times for each file install. Is there a way I can select all deb files at once and install them by just inputting my password once?
Thanks.

---

### Post by ibutho on 2009-07-16
You can do something like
```
sudo dpkg -i *.deb
```
or
```
sudo dpkg -i deb1.deb deb2.deb deb3.deb
```

---

### Post by Rytron on 2009-07-16
> **ibutho said:**
> You can do something like
```
sudo dpkg -i *.deb
```
or
```
sudo dpkg -i deb1.deb deb2.deb deb3.deb
```

Thank you ibutho.

---

