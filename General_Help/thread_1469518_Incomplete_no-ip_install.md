---
title: "Incomplete no-ip install?"
date: 2010-05-02
forum: General Help
---

### Post by draxfelton on 2010-05-02
I'm trying to install No-IP, but I can't get it to complete.  The Software Center is giving me this message: "Previous installation hasn't been completed" when I try to remove it.  

The command "sudo apt-get -f install" causes the install to pick up again, but the installer freezes after I answer yes or no to this question: "2 hosts are registered to this account.  Do you wish to have them all updated?[N] (y/N)"

How do I untangle this?

I'm using 10.04 LTS.

---

### Post by dino99 on 2010-05-02
why do you need such package ?

install locate then into console: locate noip2 (i guess its that package)

then sudo rm -f /the different path given by locate

then sudo apt-get install -f

sudo dpkg --configure -a

---

