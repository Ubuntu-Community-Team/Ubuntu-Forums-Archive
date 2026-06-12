---
title: "lock package"
date: 2010-02-28
forum: General Help
---

### Post by pavel989 on 2010-02-28
searched google and searched the forums, found nothing.

im running karmic, how can i lock my xorg version, such that if i upgrade to lucid xorg will stay

---

### Post by Primefalcon on 2010-02-28
> **pavel989 said:**
> searched google and searched the forums, found nothing.

im running karmic, how can i lock my xorg version, such that if i upgrade to lucid xorg will stay
open synaptic, highlight the package, select the package menu and click lock package

---

### Post by pavel989 on 2010-02-28
oh i thought that was in the right click menu, and i didnt see it there. lol.

ty!

---

### Post by Primefalcon on 2010-02-28
> **pavel989 said:**
> oh i thought that was in the right click menu, and i didnt see it there. Lol.

Ty!
yw

---

### Post by dcstar on 2010-03-01
> **Primefalcon said:**
> open synaptic, highlight the package, select the package menu and click lock package

Unfortunately I have found that "Pinning" a package does **not** stop it from being replaced by the ***Upgrade*** process (not the regular Update process, that is ok).

I have reported this as a [bug]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/399538") ages ago, but I still see that locked packages that I want left alone are listed to be replaced by an Upgrade - so beware!

I just tested a 9.04 to 9.10 Upgrade and Pinned packages are still marked for version upgrade!!!  :-(

---

### Post by pavel989 on 2010-03-01
yeah same

---

