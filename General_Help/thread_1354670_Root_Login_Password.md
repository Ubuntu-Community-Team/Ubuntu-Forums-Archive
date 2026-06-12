---
title: "Root Login Password"
date: 2009-12-14
forum: General Help
---

### Post by samyserse on 2009-12-14
Hi All,

   How are you Guys, Iam installing unbuntu server latest edition iam not able to give the password for the root so iam not able to login has a root and i want to go in GIU mode can you please give some tips regarding my question.

Regards
Samy

---

### Post by kellemes on 2009-12-14
> **samyserse said:**
> Hi All,

   How are you Guys, Iam installing unbuntu server latest edition iam not able to give the password for the root so iam not able to login has a root and i want to go in GIU mode can you please give some tips regarding my question.

Regards
Samy

You're asked for a 'root'-password at startup?
By the way, the server edition of Ubuntu has no GUI by default.
If you want to go GUI you probably have to install the hole thing first..
```
sudo apt-get install ubuntu-desktop
```
If you need GUI on a server you better install a GUI-based distribution to begin with..
Tip: [CentOS]("http://www.centos.org/")

---

### Post by Sin@Sin-Sacrifice on 2009-12-14
If you want to use root you can use sudo and your password. If you really need a root terminal you can sudo -i and your password. If you want a GUI installed on your server then you just need to sudo apt-get install ubuntu-desktop, kubuntu-desktop, xubuntu, lxde, or whichever you want. Don't need to use the root terminal for this... that's why the sudo command. Not real safe to use a root log in. If not one of those you can Google the package name for yours. After it's installed just type startx as a normal user and there you have it.

---

### Post by coffeecat on 2009-12-14
Why are you wanting to log in as root in a GUI? :-s

Have a read of the forum policy on logins as root:

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

And this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

