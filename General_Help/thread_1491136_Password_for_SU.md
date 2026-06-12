---
title: "Password for SU"
date: 2010-05-23
forum: General Help
---

### Post by theKuch on 2010-05-23
Thanks to all those who posted on my previous link re SU.

How do I find my password for SU? I was not given the opportunity, at least that I noticed, to set this up at installation. And it is not my "regular" user password either.

Thanks

---

### Post by theKuch on 2010-05-23
OK -- just saw it -- root, thus SU, is locked.

I thought one of the essences of Linux that it gave you enough rope to hang yourself if you insisted.

---

### Post by sisco311 on 2010-05-23
su prompts for the target user's password. Since the root account password is locked by default you can not su to root.

Instead of su use sudo to run commands as root or another user: [uhelp]community/RootSudo[/uhelp].

---

### Post by Elfy on 2010-05-23
> **theKuch said:**
> OK -- just saw it -- root, thus SU, is locked.

I thought one of the essences of Linux that it gave you enough rope to hang yourself if you insisted.

It does - however as was already pointed out in your other thread we do not allow root login tutorials. 

The assumption is that if you really need to unlock the root account you will have enough knowledge to find the rope you need.

---

