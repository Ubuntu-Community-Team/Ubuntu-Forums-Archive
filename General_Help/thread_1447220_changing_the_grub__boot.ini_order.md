---
title: "changing the grub / boot.ini order"
date: 2010-04-05
forum: General Help
---

### Post by apollocreed on 2010-04-05
hi guys 

is there any way to change the boot order in Ubuntu for the grub loader? thanks :guitar:cdefa448621161481ae7f8a1bc3b1d0372111432

---

### Post by apollocreed on 2010-04-05
or is there any pre-existing thread on this

I want to get version 15 going as a default

---

### Post by drs305 on 2010-04-05
apollocreed,

Welcome to Ubuntu and the Ubuntu forums.

Which version of Grub are you using? The version is shown on the initial Grub boot screen (Grub 0.97 is Grub legacy, 1.96 or later is Grub 2) or by running the following command:
```
grub-install -v
```

From your question, I believe you want to change the OS booted by default and not order the items appear in the menu.

 If you are using Grub 2, here is the link to a guide on making the basic changes to the default settings. Section 2 covers the default OS selected by Grub 2.[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

If you aren't comfortable with using the terminal and the command line, I would recommend using the GUI app StartUp-Manager. It can set the default OS in either Grub legacy or Grub 2. There is a link on how to install and use it in my signature line (the "SUM" link).

If you have questions, just ask.

---

