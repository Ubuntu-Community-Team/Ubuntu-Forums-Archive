---
title: "Installing things is a real problem for me."
date: 2011-08-17
forum: General Help
---

### Post by LDel001 on 2011-08-17
I am sorry, I know this is probably a very buck basic question and I will be hated for asking on a forum. However, I have googled this, and I have even followed tutorials.

In particular I am trying to install GTK+ 3.0 on ubuntu 11.04, as I have recently made the switch from windows to linux, and I am a very experienced C++ developer. In my job, we have people who are responsible for machine setups, so anytime I have needed linux, all my dev libraries have been on the machine when I got them.

I need to do this work from home, and installing GTK 3.0 is a real headache... I have tried following the tutorial on their site but it simply doesn't work, the make, and make install parts just have errors, even when I have root access. which is frustrating me to no end.

Thanks in advance if anyone can help me.

---

### Post by SavageWolf on 2011-08-17
Uh, you can just run ```
sudo apt-get install libgtk-3-0
``` from a terminal.

---

### Post by LDel001 on 2011-08-17
Thanks savagewolf, I tried that, and I trust it has installed somewhere, but when I try to #include <gtk/gtk.h> i get an error saying that the file doesn't exist...

---

### Post by CatKiller on 2011-08-17
You'll probably want the -dev package as well.

---

### Post by LDel001 on 2011-08-17
Apparently I am already running the latest version of the dev pack too... thanks for the suggestion though.

---

