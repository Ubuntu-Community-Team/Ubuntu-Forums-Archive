---
title: "Problem with Synaptic Package Manager on search"
date: 2010-05-20
forum: General Help
---

### Post by NeverHide on 2010-05-20
I open the Synaptic Package Manager and everything works gr8,i can install or uninstall packages and so on...
** BUT **
when i try to write something in the "search" field it will just close,no errors pop up or anything like that...

any ideas???

thnx in advance :D

---

### Post by SlidingHorn on 2010-05-20
Try running Synaptic from your terminal and recreating the error.  When it crashes, the terminal will tell you what the error is.  Please post it here when you're done.

---

### Post by dino99 on 2010-05-20
into a console:

sudo apt-get update
sudo apt-get install --reinstall synaptic
sudo apt-get install -f

---

### Post by NeverHide on 2010-05-20
When i run it from the terminal it runs fine.
But i noticed something now,every time i run synaptic from the System>Administration>Synaptic Package Manager menu i was always prompted to enter my password and then i'd run it as administrator.Now that i have this problem i'm not asked to enter my password...
Don't know if it's relevant in any way but just noticed that...

P.S. when running it in terminal with 'sudo synaptic',it runs fine aswell

---

### Post by NeverHide on 2010-05-20
> **dino99 said:**
> into a console:

sudo apt-get update
sudo apt-get install --reinstall synaptic
sudo apt-get install -f


dino,i've also tried what u suggested but the problem remains
thnx for the effort though :P

---

