---
title: "Problems with Nautilus"
date: 2010-10-21
forum: General Help
---

### Post by jeddycakes on 2010-10-21
Hi all,

Recently I stated to use Maverick and as part of my usual routine (I always do fresh installs rather than upgrades; bit of a clearout) I created a launcher that enables me to access root, entering 

```
gksudo-nautilus
```

In the command box. Normally, after enabling the launcher then clicking on it, it will then pop up with a prompt to enter root password which then allows access to root.

However, this time it flags up the error message

> failed to execute child process "gksudo-nautilus" (no such file or directory exists)

I'm feeling pretty n00bish and a bit thick. I don't understand why this is coming up.....I haven't done anything any different.

any help would be appreciated :)

---

### Post by wolfgangmcq on 2010-10-21
I think that the command you're looking for is ```
gksudo nautilus
```
Your command tries to run a program called *gksudo-nautilus* instead of running *nautilus* as root.

---

### Post by jeddycakes on 2010-10-22
Thanks mate, tiny but glaring error.

Who knew a little hyphen could cause me such a headache? lol

:guitar:

---

