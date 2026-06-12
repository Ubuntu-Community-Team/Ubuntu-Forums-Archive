---
title: "How do I share / to 1 user with full control permissions?"
date: 2011-01-04
forum: General Help
---

### Post by SnowPunk98 on 2011-01-04
I have a Ubuntu 10.10 server and I would like to have full access to / from my Windows 7 box so I can modify config files and such.

I have already installed Samba and created a local user on the server for myself.

I am at the point where I need to create the share to / and give my user read/write to it.

Additionally if possible I would like for it to be a hidden share for additional security.

---

### Post by dcstar on 2011-01-05
> **SnowPunk98 said:**
> I have a Ubuntu 10.10 server and I would like to have full access to / from my Windows 7 box so I can modify config files and such.

I have already installed Samba and created a local user on the server for myself.

I am at the point where I need to create the share to / and give my user read/write to it.

Additionally if possible I would like for it to be a hidden share for additional security.

Apart from violating the basic Linux security model - and being an incredibly stupid thing to do - it is probably impossible to do for a normal user account.

---

### Post by Habitual on 2011-01-05
What about ssh or sftp?

---

