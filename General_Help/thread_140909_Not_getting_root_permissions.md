---
title: "Not getting root permissions"
date: 2006-03-07
forum: General Help
---

### Post by Poeta on 2006-03-07
Well, my problem is, that if I try running apt-get it says I don't have the permission to do so, but if I try and change the GDM, which needs root permission, I'm allowed to change it, does anyone knoe what I need to do? :-|

---

### Post by codejunkie on 2006-03-07
[QUOTE=Poeta]Well, my problem is, that if I try running apt-get it says I don't have the permission to do so, but if I try and change the GDM, which needs root permission, I'm allowed to change it, does anyone knoe what I need to do? :-|[/QUOTE]
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
this might help a little.

---

### Post by Poeta on 2006-03-07
I'd already seen that link but I still don't know what to do.

The error I get is that the permission to open [COLOR="Red"]apt-get update[/COLOR] is denied, like this, only in English :rolleyes: 

```
E: Abrindo /etc/apt/sources.list - ifstream::ifstream (13 Permissão negada)
```

[SIZE="2"]* Abrindo - Opening
* Permissão negada - Permission denied[/SIZE]

---

### Post by Mustard on 2006-03-07
[QUOTE=Poeta]I'd already seen that link but I still don't know what to do.

The error I get is that the permission to open [COLOR="Red"]apt-get update[/COLOR] is denied, like this, only in English :rolleyes: 

```
E: Abrindo /etc/apt/sources.list - ifstream::ifstream (13 Permissão negada)
```

[SIZE="2"]* Abrindo - Opening
* Permissão negada - Permission denied[/SIZE][/QUOTE]

What is the exact command you are typing in?

---

### Post by Poeta on 2006-03-07
[QUOTE=Mustard]What is the exact command you are typing in?[/QUOTE]

apt-get update

---

### Post by justleen on 2006-03-07
you should run it with sudo
```

$ sudo apt-get update
password:

```
the passwd being your userpasswd (that you use to logon..)

---

### Post by Poeta on 2006-03-07
It worked, thank you ;)

---

