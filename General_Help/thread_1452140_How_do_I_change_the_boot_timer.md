---
title: "How do I change the boot timer?"
date: 2010-04-11
forum: General Help
---

### Post by schwabdale on 2010-04-11
Can someone please tell me step by step how to change the Countdown timer during boot?
I want to change it to 0.

Thanks in advance!

---

### Post by r_s on 2010-04-11
edit /etc/default/grub file to change the timeout and the run sudo update-grub , if you are using grub2
if you are running the older version just change it in menu.lst.

---

### Post by schwabdale on 2010-04-11
It doesn't give me the option to save?

---

### Post by r_s on 2010-04-11
open it using sudo gedit /etc/default/grub

---

### Post by akakingess on 2010-04-11
You have to open/edit with root capabilities, that may be the reason it won't let you save. Use a terminal and do sudo gedit /etc/defualt/grub or /etc/default/grub/menu.lst (whereever they are located) to open with root capabilities.

---

