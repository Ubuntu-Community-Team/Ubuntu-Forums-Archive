---
title: "not able to use win key on laptop"
date: 2010-05-19
forum: General Help
---

### Post by jaunty.jacklope on 2010-05-19
Hi
i am not able to use win key on my ibm t60 laptop with ubuntu 10.04. i have a file in my home directoy called .xstartup and has the following lines in it

# Make the Windows key a useable mod key:
xmodmap -e "remove mod4 = F13"
xmodmap -e "keycode 115 = Super_L"
xmodmap -e "add mod4 = Super_L"

when i get into system > preferences > keyboard shortcuts i am not able to assign the the win/super key to launch the main menu.

Please help

Many thanks

---

### Post by meijer.o on 2010-05-19
Dear linux user,

run gconf-editor

add Super_L to apps > metacity > global_keybindings, see screenschot,

Kind regards,

Otto

---

### Post by jaunty.jacklope on 2010-05-19
that solved my problem

Many thanks for your help

---

### Post by user1001 on 2010-05-19
Can you use the thread tools to mark your thread as solved please, Thanks.

---

