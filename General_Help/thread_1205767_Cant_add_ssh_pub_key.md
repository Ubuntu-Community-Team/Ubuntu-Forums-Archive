---
title: "Cant add ssh pub key"
date: 2009-07-06
forum: General Help
---

### Post by triangleSLO on 2009-07-06
I know i am asking alot of questions lately but i a starting to explore ubuntu under the hood so please bare with me :)

Everything worked fine (i guess) but then i had one of those moments. I created new pair of keys and ofcourse now i can connect from computer A to cumputer B but cant connect from computer B to computer A. I suspect its because i created new pair of keys :KS

I tried to delete keys(known host) on computer A with $ ssh-add -D but this doesnt help. When i try to copy key from computer B i get Access denied public key error.

I need a way do delete old key and copy new key without errro, or so i think.

---

### Post by elitenoobboy on 2009-07-06
Well, to delete the old keys, you can try deleting the .ssh folder in your home directory instead of ssh-add -D, and that should restore ssh to default.

---

