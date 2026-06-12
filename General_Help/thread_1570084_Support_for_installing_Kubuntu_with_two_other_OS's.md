---
title: "Support for installing Kubuntu with two other OS's Please!"
date: 2010-09-07
forum: General Help
---

### Post by silkworm2.5 on 2010-09-07
Hey there. ):P
I am currently using a CompaQ Altec Lansing laptop, which came with Windows 7 Pre-installed. It is the 64 bit version. The same day I got it I got Ubuntu on it as well, also in 64 bit.
I have had no problems with either of them.

What I would like to do, is install Kubuntu 10.04 64 bit along side Windows 7 and Ubuntu. Is it possible? Or would i be stuck having to make a Wubi?

---

### Post by zvacet on 2010-09-07
Yes,you can do that,but you can also just install kubuntu-desktop package in your ubuntu and change desktops as you like.So if you decide to install kubuntu desktop in your ubuntu 

```
sudo apt-get install kubuntu-desktop
```

---

### Post by silkworm2.5 on 2010-09-10
Thanks for that. is there any way I can get it without all the KDE applications? And can i get the netbook remix of Gnome with this same method?

---

### Post by zvacet on 2010-09-12
I don´t know about avoid to install all apps,because kubuntu-desktop is metapackage.If you use some other desktop on your netbook I don´t see reason why not install Gnome with same method.In that case 

```
sudo apt-get install ubuntu-desktop
```

---

