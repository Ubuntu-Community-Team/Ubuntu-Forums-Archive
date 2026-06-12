---
title: "Update manager won't update???"
date: 2010-01-15
forum: General Help
---

### Post by demonic_crow on 2010-01-15
I get this message:   E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by MelDJ on 2010-01-15
in terminal type sudo dpkg --configure -a
then try updating

---

### Post by demonic_crow on 2010-01-15
thanks got it working now, the update manager had --a when it should of been -a so thats why I wasn't getting it done until I manually did it through terminal and it gave me that message and thought it was the same.

---

### Post by clmoorehead on 2010-01-15
I tried this, but am a total newb.  Can someone explain this to me a little further?

---

### Post by clmoorehead on 2010-01-15
I tried this, but am a total newb.  Can someone explain this to me a little further?

---

### Post by john newbuntu on 2010-01-15
Open a terminal by going to Applications->Accessories->Terminal.

In there, type the following:
```
sudo dpkg --configure -a
```Then open system->administration->update manager

---

### Post by clmoorehead on 2010-01-15
Ok, now it works.  I am not sure why it did not the first time.  I must not have had the spaces and dashes right.  Thanks for your help.  I am trying ubuntu, but know nothing about linux.

---

### Post by clmoorehead on 2010-01-16
What exactly did that do?

---

### Post by john newbuntu on 2010-01-16
In the Unix/LInux world, the word "man" is your friend.  If you open up a terminal and type
```
man dpkg
```
you can get your answer.  It  basically reconfigured the unpacked packages.

---

### Post by clmoorehead on 2010-01-16
Thanks!

---

