---
title: "chown, CAP_CHOWN, and my miseries."
date: 2006-06-20
forum: General Help
---

### Post by Mamour on 2006-06-20
Hi all,

I've been quite puzzled for a great while concerning the fact that chown would never work if I didn't run it as superuser. I've now discovered that this is a new security feature in Linux 2.6.14 and up. Is there any way to configure my system so that unprivileged users can chown their files? I can't give out the administrator password to everyone, it rather kills its purpose...

Thanks in advance.

---

### Post by ifokkema on 2006-06-20
[QUOTE=Mamour]Hi all,

I've been quite puzzled for a great while concerning the fact that chown would never work if I didn't run it as superuser. I've now discovered that this is a new security feature in Linux 2.6.14 and up. Is there any way to configure my system so that unprivileged users can chown their files? I can't give out the administrator password to everyone, it rather kills its purpose...

Thanks in advance.[/QUOTE]

Erm... 'chown their files' -> like transfering their files to the ownership of a different user, you mean? I guess you can set the suid bitset on chown, but that will allow any user to transfer other people's files in their ownership...

---

### Post by Mamour on 2006-06-20
[QUOTE=ifokkema]Erm... 'chown their files' -> like transfering their files to the ownership of a different user, you mean? I guess you can set the suid bitset on chown, but that will allow any user to transfer other people's files in their ownership...[/QUOTE]
Yes, that is what I mean. Well, it's the expected use of chown anyway... I wonder why this change was made, doesn't this break the POSIX specification for chown? :confused:

---

