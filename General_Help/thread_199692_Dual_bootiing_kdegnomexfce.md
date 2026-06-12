---
title: "Dual bootiing kde/gnome/xfce?"
date: 2006-06-19
forum: General Help
---

### Post by ensomniac on 2006-06-19
So, I was trying to install "musix-Gnu+linux" and grub was deleted and replaced.  I couldn't get grub to setup and reinstall on the system, so I installed fedora core, and tried it's grub to work.  So, I give up.  but I would like to try dual booting with kubuntu, ubuntu, and/or xubuntu.  how would I go about this?  this is my third time reinstalling ubuntu ](*,)  ...but I am beginning to be a professional.  :D But I am not complaining...trial and error are the best teachers right?  So, I have downloaded the iso's for both, and now...I would like to install it, so how would I dual boot this?  What settings do I need for grub?  Thanks for your help...and I am sorry for asking all these seeming noob questions.

---

### Post by Ramses de Norre on 2006-06-19
You don't need to dual boot them, just install ubuntu and then do ```
sudo aptitude install kubuntu-desktop xubuntu-desktop
``` you can choose which one to start in the session menu of the login screen.

---

### Post by aysiu on 2006-06-19
Don't forget to do ```
sudo aptitude update
``` first.

---

