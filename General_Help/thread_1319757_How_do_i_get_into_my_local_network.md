---
title: "How do i get into my local network"
date: 2009-11-08
forum: General Help
---

### Post by invitingdopeman on 2009-11-08
[list]
[*]high everybody im trying to figure out how to acess my loacl network any suggs thanks so very much i hope there are some great softwar tools out there
[/list]

---

### Post by billyboy1978 on 2009-11-08
Install openssh:
$ sudo apt-get install ssh

Connect:
$ ssh -X <username>@<local-ip>

TIP: 
$ man ssh

---

