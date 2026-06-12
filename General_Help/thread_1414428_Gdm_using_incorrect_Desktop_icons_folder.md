---
title: "Gdm using incorrect Desktop icons folder"
date: 2010-02-23
forum: General Help
---

### Post by jimbob on 2010-02-23
I mistakenly moved the /home/user/Desktop file to another location so now when my desktop starts it used the entire contents of my /home/user/ directory (except for the hidden contents) to create icons all over my desktop.
 I have restored the Desktop folder to the correct location but it ignores it now and continues to show every file under /home/user as an icon.

How do I reset it to point to the original Desktop folder?
(Using 64-bit Ubuntu)

---

### Post by RedRat on 2010-02-23
Have you tried re-booting the computer?

---

### Post by raktarok on 2010-02-23
You may use ubuntu-tweak to change the desktop folder to the default one. The program has the option..
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by ajgreeny on 2010-02-23
Have a look in **gconf-editor ->apps ->nautilus ->preferences**, and if there is a check mark in **desktop_is_home_directory** remove it.

I don't know if it will help, but I recall seeing a similar problem in the past solved that way.

---

### Post by jimbob on 2010-02-24
Many thanks to those who replied.  I still could not get the problem to resolve using any of the solutions.  I even tried ticking the boxes to force the condition, rebooting, then un-ticking them and rebooting again.
Something must have gotten clobbered in gdm but I'll be darned if I could find it.
  I ended up saving my stuff, creating another user and replacing it under the new account.

---

