---
title: "clean ubuntu install failure"
date: 2011-11-20
forum: General Help
---

### Post by Macbologos on 2011-11-20
NewBee clean install from cd won't work boot mgr missing pls hlp

---

### Post by fantab on 2011-11-20
> **Macbologos said:**
> NewBee clean install from cd won't work boot mgr missing pls hlp

You must tell us more to get help.


[LIST]
[*]What kind of computer is it, Laptop/desktop?
[*]What version of Ubuntu? What flavor? what architecture?
[*]Are you trying to Dual Boot?
[*]How did you choose to install Ubuntu?
[/LIST]

Providing all the information will help us help You, otherwise we will have to guess everything, just as I would do now.

Read this [**Installation info**]("https://help.ubuntu.com/community/GraphicalInstall")
Read this for [**Dual-Boot**]("https://help.ubuntu.com/community/WindowsDualBoot").

In your case I GUESS you have not installed GRUB correctly. You must** install GRUB on** the Hard Drive you are booting from, for instance,** /dev/sda** and NOT /dev/sda1 or /dev/sda3, etc.

---

