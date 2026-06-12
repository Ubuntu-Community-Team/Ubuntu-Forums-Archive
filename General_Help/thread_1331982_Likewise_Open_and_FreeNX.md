---
title: "Likewise Open and FreeNX"
date: 2009-11-19
forum: General Help
---

### Post by ghendoaus on 2009-11-19
Hi all can I use Likewise Open to authenticate FreeNX users if so how? 
Thanks in advance for any help

---

### Post by gabrielebellini on 2009-12-01
Yes, it's possible and you can do it by default. Once Likewise and FreeNX are both installed (linux box joined to AD domain, obviously) you can connect to the linux NX server from a NX client machine using any Active Directory user. Very important: username on the NX client session must be of the form: domain\\user (MUST use double backslashes instead of one).

Gabriele

---

### Post by ghendoaus on 2009-12-03
> **gabrielebellini said:**
> Yes, it's possible and you can do it by default. Once Likewise and FreeNX are both installed (linux box joined to AD domain, obviously) you can connect to the linux NX server from a NX client machine using any Active Directory user. Very important: username on the NX client session must be of the form: domain\\user (MUST use double backslashes instead of one).

Gabriele
Hi Gabriele. Thanks for getting back to me this works great! The double backslash was the killer \\ is there any way to be able to avoid using this? It would make user training and support so much easier.

Edit PS. Sorry for not following up sooner it's been a busy time!!

---

