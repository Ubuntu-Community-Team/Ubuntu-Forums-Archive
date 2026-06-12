---
title: "Ubuntu 10.10 login problem"
date: 2010-10-19
forum: General Help
---

### Post by sam45 on 2010-10-19
Hi, I installed Ubuntu 10.10 a few days ago, everything worked fine, did some tweaking and somehow I can't login anymore..

so, I can boot ubuntu, get on my desktop, and I can also go into the terminal (alt+F*)

This picture will explain my problem better:
[IMG]http://img822.imageshack.us/f/s0098.jpg/[/IMG]
(if you can't see the picture, try this [http://img822.imageshack.us/f/s0098.jpg/]("http://img822.imageshack.us/f/s0098.jpg/")
(the second screen behind the login keyring is a screenlet manager window I think..

I can't use my keyboard to write the login keyring, I also can't do anything else (only the terminal)

I really hope someone can help me with this issue, Finally got ubuntu working after weeks being stuck with windows because of graphic card support..

---

### Post by fragos on 2010-10-19
occasionally the keyring won't accept my password when the window first pops up. It almost always works when I try the second time.

---

### Post by sam45 on 2010-10-20
It's not that the keyring doesn't accept my password, but I can't even type the password in the keyring..
can't click anything else on my desktop also

---

### Post by fragos on 2010-10-20
So your machine is frozen but the cursor moves. Try <Alt>F4 to close the keyring window.

---

### Post by sam45 on 2010-10-20
Tried alt+F4, doesn't work..

update: when I can log back in ubuntu after 2-4 tries..
all the other times I get a frozen desktop

---

### Post by fragos on 2010-10-20
Exactly what is your hardware. Some early hardware had compatibility problems with ACPI, Advanced Configuration and Power Interface. In that case the problem was solved by disabling ACPI during the boot process. I don't recall how to do that but searching this forum for ACPI might give you some insight. I'm in pure guess where to look mode on this issue.

---

### Post by swidmer on 2010-10-21
The solution is here:
[http://ubuntuforums.org/showthread.php?p=9938975](http://ubuntuforums.org/showthread.php?p=9938975)

---

### Post by sam45 on 2010-10-21
> **swidmer said:**
> The solution is here:
[http://ubuntuforums.org/showthread.php?p=9938975](http://ubuntuforums.org/showthread.php?p=9938975)

thank you swidmer ! (and everyone else)
fixed the problem like that ^^

---

