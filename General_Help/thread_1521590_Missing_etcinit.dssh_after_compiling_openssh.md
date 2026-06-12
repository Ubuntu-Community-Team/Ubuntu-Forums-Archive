---
title: "Missing /etc/init.d/ssh after compiling openssh"
date: 2010-07-01
forum: General Help
---

### Post by jeeves on 2010-07-01
I had to compile **openssh** so I could have a version with the [HPN-SSH patch]("http://www.psc.edu/networking/projects/hpn-ssh/faq.php") applied. The compile seems to have gone fine, but oddly enough **I have now have no ssh script in my /etc/init.d directory.** So I have no easy way of automatically starting openssh-server.

Any idea how to fix this. Here are the configure options I used when compiling openssh:

```
./configure --prefix=/usr --sysconfdir=/etc/ssh --with-pam
```

---

### Post by diesch on 2010-07-01
Quite often source packages don't include init scripts. To make your own you can use  */etc/init.d/skeleton *as a base. Or use the one from the Ubuntu openssh package.

---

