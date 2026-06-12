---
title: "How to disable some standard users"
date: 2009-07-24
forum: General Help
---

### Post by alpha_lt on 2009-07-24
Hello all,
 
I have read lots about root account and why it is safe to turn it off. Its ok, but what should I do with bunch of users in /etc/passwd file ? They come preinstalled and I think their usernames are pretty standard and known to every hacker. So can I disable all users except my own ? I mean not disable, but delete or at least give them fake shell ? Maybe its enought to block them in sshd_config file for disabling ability to log these users onto machine from ssh ?
 
Regards,
alpha

---

### Post by ibutho on 2009-07-24
I would leave /etc/passwd as it is. If you remove the default system users, you can end up with a broken system because some processes expect those users to be there. Most system users cannot login directly via ssh (or any other means) and have their shell already set to something like /bin/false.

---

### Post by alpha_lt on 2009-07-24
Thank you for fast reply.
Ok, I will leave them, but what about giving them fake shell ? Is it safe for normal system work ?

---

### Post by Iowan on 2009-07-24
> **alpha_lt said:**
> Ok, I will leave them, but what about giving them fake shell ? Is it safe for normal system work ?/bin/false should be adequate.> **ibutho said:**
> Most system users cannot login directly via ssh (or any other means) and have their shell already set to something like /bin/false.

---

