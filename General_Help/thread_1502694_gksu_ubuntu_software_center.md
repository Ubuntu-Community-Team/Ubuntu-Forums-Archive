---
title: "gksu ubuntu software center"
date: 2010-06-05
forum: General Help
---

### Post by spezticle on 2010-06-05
instead of starting the Ubuntu software center, finding applications, clicking install and then entering in the password, i thought i would change the command to start it with gksu having me enter in the password before hand and not needing to type the pw when i'm ready to click install or remove.

will this work fine, or will it cause issues with how applications get installed, seeing as root installs them?

---

### Post by kerry_s on 2010-06-05
any which way your entering a password so why bother messing with the way it is?

---

### Post by spezticle on 2010-06-06
> **kerry_s said:**
> any which way your entering a password so why bother messing with the way it is?

good question indeed. I was just wondering if the timing of password entry is really the only difference

---

### Post by new_tolinux on 2010-06-15
> **spezticle said:**
> good question indeed. I was just wondering if the timing of password entry is really the only difference
In my opinion the password should be asked for as soon as system changes are requested. Selecting packages can be time consuming and therefore is a task which sometimes is done in parts. That means it would be insecure if the password has to be entered before selecting any package, because that would leave a program running with elevated permissions if you decide to have a break while selecting those packages.

---

### Post by anantshri on 2010-06-15
> **new_tolinux said:**
> In my opinion the password should be asked for as soon as system changes are requested. Selecting packages can be time consuming and therefore is a task which sometimes is done in parts. That means it would be insecure if the password has to be entered before selecting any package, because that would leave a program running with elevated permissions if you decide to have a break while selecting those packages.


the only problem here is that software center runs apt in daemon mode i.e. as soon as you select first package its starts processing it. and all packages are processed as seperate object in FIFO queue. the problem is password is asked first time when first package is selected and then password is only asked if the queue is already cleared and new software is requested.


not sure about the op's point but i would also prefer giving password before hand.

---

