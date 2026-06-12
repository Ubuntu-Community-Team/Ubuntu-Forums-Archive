---
title: "dhcp server"
date: 2005-01-27
forum: General Help
---

### Post by anachron on 2005-01-27
hello. i'm a newbie and i've just installed ubuntu on my server at home. i have a small Local Area Network, with an internet connection that's in my house. I'm trying to use my linux as an server. I couldn't find the package that contains dhcp server. can someone help me? i really wanna make this work...

---

### Post by az on 2005-01-27
dnsmasq

You install it and remove the comment from one line,restart it  and you are good to go.

Take a look at shorewall, too.  It does NAT as well as firewalling.  Also for NAT, there is firestarter in the backports repository.

---

