---
title: "Help with compiling specific driver"
date: 2009-08-25
forum: General Help
---

### Post by redscorpion69 on 2009-08-25
After lots of troubleshooting (and a help from another forum), i figured out why i can't run 3 quad port nics at the same time. There is hard-coded limit of 8 instances in via-velocity driver which comes installed with kernel 2.4 and up. 
So i have to recompile it. But i have no idea how.
Do i have to:

a) install kernel source package and compile the whole thing
b) just compile the specific driver (via-velocity.h is the file i need to make changes to)

Can anyone explain what i need to do to make this work because i'm total noob when it comes to this. :redface:

thx

---

### Post by redscorpion69 on 2009-08-26
Bump

---

