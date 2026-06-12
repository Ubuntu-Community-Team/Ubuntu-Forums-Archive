---
title: "Desktop shortcuts invisible"
date: 2009-11-15
forum: General Help
---

### Post by simartem on 2009-11-15
I am using Ubuntu 9.10
When i create a desktop shortcut (for example : shortcut for my documents) The shortcut is not seen on the desktop however when i go to console and look at the content of the desktop directory, i can see the shortcut  (documents.desktop). I have some shortcuts from the past, they are visible but the new ones wont show.

How to solve this ?

---

### Post by arnab_das on 2009-11-16
do this:

press Alt+F2

type "gconf-editor"

go to apps>nautilus>desktop and check the "volumes visible option"

---

### Post by simartem on 2009-11-16
thank you very much, it works.

---

