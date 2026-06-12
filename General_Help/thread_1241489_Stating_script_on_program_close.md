---
title: "Stating script on program close"
date: 2009-08-16
forum: General Help
---

### Post by nitromanrc on 2009-08-16
I have recently been getting into typesetting with LaTeX and kile, but I hated the way the keyboard was laid out, it seemed inneficient to me, because of the number keys/symbols at the top, I almost always wanted the symbols while using LaTeX, so why should I have to press "Shift" for them?

Anyways, I like the normal keymap for normal things, so i wanted to make a script that will auto-change the keymap when kile starts, and change it back when kile closes. the startup I can do fine, I can just make a startup script for kile itself, but the closing I'm not so sure about.

 Is there a way that I can have a script execute automatically when kile closes?

---

### Post by mrbiggbrain on 2009-08-16
why not make a shell script

#change keymap
.....
#run program
.....
#change keymap back

---

### Post by nitromanrc on 2009-08-16
I was planning on making a shell script but can I have one automatically init when it sees the program close?

---

### Post by Johnny B on 2009-08-16
> **mrbiggbrain said:**
> why not make a shell script

#change keymap
.....
#run program
.....
#change keymap back

script commands will be executed sequentially, so it will automaticly change keymap back when the program closes

---

