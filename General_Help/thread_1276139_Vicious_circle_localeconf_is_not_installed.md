---
title: "Vicious circle: localeconf is not installed"
date: 2009-09-26
forum: General Help
---

### Post by Lockheed on 2009-09-26
I run out of ideas here. I am trying to reconfigure my locales with
```
dpkg-reconfigure locales
```
but what I get is
```
~$ sudo dpkg-reconfigure localeconf
Package `localeconf' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: localeconf is not installed.

```

And this is what happens when I try to install it:
```
~$ sudo apt-get install localeconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package localeconf

```

Can anyone help me break this vicious circle?

---

### Post by wojox on 2009-09-26
Here: [https://help.ubuntu.com/community/LocaleConf](https://help.ubuntu.com/community/LocaleConf)

---

### Post by Lockheed on 2009-09-27
Yes, I know this page but there is nothing helpful.

---

