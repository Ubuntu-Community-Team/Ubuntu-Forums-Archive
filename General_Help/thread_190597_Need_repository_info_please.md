---
title: "Need repository info please"
date: 2006-06-06
forum: General Help
---

### Post by jmpmjmpm on 2006-06-06
Hi all,

I need to know what to do to add the latest cvs of alsa to the package manager, enabling backports don't do it

thanks

---

### Post by cmarker on 2006-06-06
There are a couple of options:

first make sure you have the universe and multiverse repositories added:

```


## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse


```

Or you can install Automatix - this will allow you to get lots of common programs easily

---

### Post by cdude on 2006-06-06
[QUOTE=jmpmjmpm]Hi all,

I need to know what to do to add the latest cvs of alsa to the package manager, enabling backports don't do it

thanks[/QUOTE]
The best place to go for generating Ubuntu (Dapper) repositories list is [Ubuntu - Sources.list generator]("http://www.ubuntulinux.nl/source-o-matic")

---

