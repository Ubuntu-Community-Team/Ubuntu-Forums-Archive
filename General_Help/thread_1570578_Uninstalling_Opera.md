---
title: "Uninstalling Opera"
date: 2010-09-08
forum: General Help
---

### Post by TimEnid on 2010-09-08
i am trying to completely remove opera from my pc. I go into synpatic and choose complete removal. but then when i reinstall it, it opens up as if it was never deleted, all my bookmarks, passwords, speed dial info, shows up. how do i get rid of every trace of opera on my pc? thanks.

---

### Post by orianablage on 2010-09-08
Do you have those bookmarks and passwords in another browser too? Then the problem might be on the installation. Opera got the information from the other browser.

---

### Post by TimEnid on 2010-09-08
> **orianablage said:**
> Do you have those bookmarks and passwords in another browser too? Then the problem might be on the installation. Opera got the information from the other browser.

nope, i didnt import my bookmarks into chrome or firefox. both have about 5 booksmarks, while opera has about 40. and then theres the speed dial page, after i remove opera, the same configured speed dial pops up, without me syncing opera.

---

### Post by stee1rat on 2010-09-08
Try to look with **ls -a** in your home directory, i bet there is **.opera** directory with your settings :)

---

### Post by TimEnid on 2010-09-08
> **stee1rat said:**
> Try to look with **ls -a** in your home directory, i bet there is **.opera** directory with your settings :)

yes there is, now how do i get to it? thanks.

---

### Post by gandaran on 2010-09-08
> **TimEnid said:**
> yes there is, now how do i get to it? thanks.
enable view hidden files in nautilus then delete the .opera folder

---

### Post by stee1rat on 2010-09-08
What do you mean? if you want to delete it completely just use **rm -r .opera** in your home directory.

---

### Post by TimEnid on 2010-09-08
> **stee1rat said:**
> What do you mean? if you want to delete it completely just use **rm -r .opera** in your home directory.

thanks, still fairly new to this. that did the trick

---

### Post by AlexandreP on 2010-09-08
A complete removal of software using Synaptic doesn't delete personal data/preferences in users' home folders created by this software. It only removes all files installed during installation.

---

### Post by TimEnid on 2010-09-09
> **AlexandreP said:**
> A complete removal of software using Synaptic doesn't delete personal data/preferences in users' home folders created by this software. It only removes all files installed during installation.
got it. thanks a lot.

---

