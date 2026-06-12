---
title: "Cant use linuxpartition anymore"
date: 2006-04-11
forum: General Help
---

### Post by Bishop Hill on 2006-04-11
Well, as I stated in another tread, I cant access my linuxpartition. When I boot in recovery mode and type 

```

dpkg --status xserver-common
dpkg --status xserver-base
```

I get the result that xserver-base is not installed. Then, when i try 

```

sudo apt-cache search X| grep server
```

it shows a lot of packages, but nothing that I can use.

Please help me, I want my files and my good OS back:(

---

### Post by incubus on 2006-04-12
Sorry, I don't think I understand. You're saying you can't access the partition, or you can't start the X server? (I don't know what's the other thread)

What about:
$ dpkg -l xserver-xorg

Yeah, it would be better get more details. What's the other thread you mentioned?

incubus

EDIT: Alright, found it:
[http://www.ubuntuforums.org/showthread.php?t=158254](http://www.ubuntuforums.org/showthread.php?t=158254)

---

