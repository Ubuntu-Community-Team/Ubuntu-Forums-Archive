---
title: "Application to convert PDF to Rich Text?"
date: 2006-06-18
forum: General Help
---

### Post by trorion on 2006-06-18
I've seen many applications that convert Text/Rich Text to PDF.  Is there an application that converts PDF to Rich Text?  I can always do it at work but I'd like to solve this problem at my home computer (400-500 page rich text files on email = bad mojo).

Thanks in advance
ps, I tried 
PDF -> HTML -> Text = really fubar
PDF -> Text = fubar

Again, convert FROM PDF TO RICH TEXT

---

### Post by aysiu on 2006-06-18
```
sudo aptitude update
sudo aptitude install kword
kword
``` Import the PDF.

---

### Post by greenstar on 2006-06-18
If you use Kubuntu or KDE the above answer will work.  Just save in the desired format after opening your document.

If you use Ubuntu or Gnome, do:
```
sudo apt-get update
sudo apt-get install abiword
abiword
```

Open the document and save in the desired format.

Also you could use OpenOffice to do the same thing, but it's slower than abiword or kword, and there's no need to access any of OO's advanced functionality for this.


greenstar

---

### Post by aysiu on 2006-06-18
You can use KWord in Gnome, just so you know. It may take a second longer to load, and it'll also install a bunch of KDE libraries with it, but it'll work.

---

