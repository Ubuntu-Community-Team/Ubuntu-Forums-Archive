---
title: "root of a problem"
date: 2009-08-13
forum: General Help
---

### Post by Rita G. on 2009-08-13
9.04

mouse & keyboard do not function after logging in as root.

pointer appears, but will not move.

(they function as user)

advice?

---

### Post by michy99 on 2009-08-13
> **Rita G. said:**
> 9.04

mouse & keyboard do not function after logging in as root.

pointer appears, but will not move.

(they function as user)

advice?

Advice: Don't log in as root.

No, I'm not trying to be funny, but what do you need to do as root that you can't do with sudo and gksudo?

---

### Post by Rita G. on 2009-08-13
thank you michy,

you're right.

gksudo was all i needed to edit my grub menu.

---

### Post by pizza-is-good on 2009-08-13
I've never tried to log in as root, and I don't think that I will ever want to.
It is sacry, like being afraid of too much power.

---

### Post by bodhi.zazen on 2009-08-13
> **Rita G. said:**
> 9.04

mouse & keyboard do not function after logging in as root.

pointer appears, but will not move.

(they function as user)

advice?

Thread closed as your question has been asked and answered.

FYI setting a root password and logging in as root are potentially detrimental.

To reset your root password use :

```
sudo usermod -p ! root
```

> **michy99 said:**
> Advice: Don't log in as root.

No, I'm not trying to be funny, but what do you need to do as root that you can't do with sudo and gksudo?

Thank you [michy99]("http://ubuntuforums.org/member.php?u=811368") .

---

