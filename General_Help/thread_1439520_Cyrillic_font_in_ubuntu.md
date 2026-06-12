---
title: "Cyrillic font in ubuntu"
date: 2010-03-26
forum: General Help
---

### Post by ljupcho on 2010-03-26
Hi,
I have one txt file on Windows with Cyrillic font in it and I transfer it to Ubuntu and the font is messed up. Why?
and i am using Ubuntu as virtual machine.

---

### Post by Nicolas_VP on 2010-03-26
It's a because of the encoding. The way I prefer is just to install wine (from repository) and use notepad (which comes with wine) to open such files.

---

### Post by ljupcho on 2010-03-26
well i actually want to do something to that file under ubuntu, like sorting, don't want just to view it.

---

### Post by ljupcho on 2010-03-26
i found out that i need this:
sudo dpkg-reconfigure locales
and someone post this question that is my problem as well, unfortunately nobody answered :S:

How am I supposed to change locales? I need to change the UTF-8 (curtrent locale) to ISO 8859-1 in gnome-terminal, but everytime I run the terminal I get UTF-8 (and need to change the locale manually).

any of you guys know this?

---

