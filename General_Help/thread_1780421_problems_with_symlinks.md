---
title: "problems with symlinks"
date: 2011-06-12
forum: General Help
---

### Post by digolax on 2011-06-12
hi there,

i',m on maverick and i've ran into problems while changing my default python version (made some mv and ln -s without knowing what i was actually doing); now i can't run software center or exaile, for instance. is there any way in wich i can restore all this mess i made? what if i upgrade to natty? would really appreciate any help.

---

### Post by WorMzy on 2011-06-12
Without knowing exactly which commands you did, it's difficult to say what you need to do to restore the original set up.

Try reinstalling python first.

```
sudo apt-get install --reinstall python-minimal python2.7-minimal python3-minimal python3.2-minimal
```

Assuming that works, it should restore all the python binary files to their default state.

---

### Post by linuxinstalledfromhdd on 2011-06-12
> **digolax said:**
> hi there,

i',m on maverick and i've ran into problems while changing my default python version (made some mv and ln -s without knowing what i was actually doing); now i can't run software center or exaile, for instance. is there any way in wich i can restore all this mess i made? what if i upgrade to natty? would really appreciate any help.

Did you create a backup of your system to reinstall with like remastersys at this point?

When you start changing things, you need to have backup clone of your system ready to go.

---

### Post by digolax on 2011-06-12
the minimal thing did the job for the most. there are just some applications i cannot run, and i suspect i should be able to. i will reinstall linux over this maverick. i'll try fedora 15 and natty. 
thanks for the help fellas.

---

