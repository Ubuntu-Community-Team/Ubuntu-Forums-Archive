---
title: "how do i share files in 9.10 Server with GUI ?"
date: 2010-03-03
forum: General Help
---

### Post by danushk on 2010-03-03
Guys ,

I have two PCs , once runs 9.10 Ubuntu Desktop named "desktop" and another runs 9.10 Ubuntu Server named "server".

as you know that "desktop" PC has a GUI installed , and i write this from there now, but "server" PC does not have anything like that so i use SSH to connect and administrate it.

Here is what i need,

I want a graphical way to share the files in "server" PC so i can edit files in that (such as css , php and html files ) on the fly and i don't need to ftp them back in to "server" from "desktop" after editing.

How do i get that done ?

---

### Post by pholden on 2010-03-03
Have you tried accessing the server using SFTP through Nautilus?

i.e. entering the following path in the address bar: "sftp://[[ip|fqdn]]/"

---

### Post by danushk on 2010-03-03
> **pholden said:**
> Have you tried accessing the server using SFTP through Nautilus?

i.e. entering the following path in the address bar: "sftp://[[ip|fqdn]]/"

:KS THANKS !!!   ya it works !!!! ,  simply and effective. :KS

Thanks a million again.

---

