---
title: "Changed user to administrator, but am still unprivileged"
date: 2012-02-05
forum: General Help
---

### Post by Mahkoe on 2012-02-05
A little while ago I discovered that I could make my user an administrator, which means, and this is an exact quote, "Can change anything on the system, including installing and upgrading software". Unless I misunderstood, to me that means I don't need to sudo if I so much as want to fart near my computer. I still do, so I'm wondering whether this is a problem or if this is normal, and how I can modify my system so I don't have to.

Thanks

---

### Post by haqking on 2012-02-05
> **Mahkoe said:**
> A little while ago I discovered that I could make my user an administrator, which means, and this is an exact quote, "Can change anything on the system, including installing and upgrading software". Unless I misunderstood, to me that means I don't need to sudo if I so much as want to fart near my computer. I still do, so I'm wondering whether this is a problem or if this is normal, and how I can modify my system so I don't have to.

Thanks

no you misunderstood

An administrator has the right to administer the system but you need to provide sudo credentials to authorise it otherwise its the same as logging on as root and anything can run under root privelege.(and root and an administrator/sudo account are not the same thing incase you thought they were)

So everything is normal, modifying things is not the way to do things, if it doesnt request you for authorisation that means anything can happen (browsing the net) scripts can run etc under admin privelege, this is not best practice and may as well just take a hammer to your machine right now ;-)

read here [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

Peace

---

### Post by Mahkoe on 2012-02-05
Okay. Well thanks a lot. Maybe I'll just start an x session as root if I'm in an overlord mood. Cheers

---

### Post by haqking on 2012-02-05
> **Mahkoe said:**
> Okay. Well thanks a lot. Maybe I'll just start an x session as root if I'm in an overlord mood. Cheers

root is locked by default in Ubuntu, there is no need to enable it as everything can be done with sudo.

**If you dont understand that then you should never do anything as root.**

But its your system, good luck.

Cheers

---

