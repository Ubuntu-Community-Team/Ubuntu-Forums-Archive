---
title: "Can't install evolution 2.30 (after removing evolution 2.32.2)"
date: 2011-04-01
forum: General Help
---

### Post by Krondaj on 2011-04-01
Hi,

i tried to update my evolution from 2.30.? to 2.32.1 usning 

ppa

ppa:julenlanda/evolution 

Because the exchange plugin didn't work i uninstalled evolution and removed the ppa.

Now when i try to install evolution from the software centre i get this:

[CENTER]Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.[/CENTER]

it asks me if I want to repair the catalog, i say yes.  then it keeps on asking me...

Now I can't install anything!

Can some body please help me!!!!!!!!

---

### Post by gradysghost on 2011-04-01
Hello.  Maybe I can help.  I haven't run into this problem myself, but I'll do what I can with your assistance.

Can you please post the full output of the following:

```
ls /etc/apt/sources.list.d
```
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```
```
sudo apt-get install evolution
```

---

### Post by Krondaj on 2011-04-01
Hi,

In the end I ran into other problems so i backed up my files and have reinstalled ubuntu 10.10 onto the laptop.

Do you know how i can get the latest stable release of evolution??

---

