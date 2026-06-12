---
title: "Configure e-mail client to work behind http proxy"
date: 2012-05-05
forum: General Help
---

### Post by jfreak_ on 2012-05-05
I am connecting to the net through a http/https proxy. Problem is, all the e-mail clients that I have used do not seem to realize this fact and try and connect directly. What to do?

PS: I use gmail.

---

### Post by dcstar on 2012-05-05
> **jfreak_ said:**
> I am connecting to the net through a http/https proxy. Problem is, all the e-mail clients that I have used do not seem to realize this fact and try and connect directly. What to do?

PS: I use gmail.

E-mail clients cannot use web proxies, they are **not** web browsers.

---

### Post by jfreak_ on 2012-05-06
I kind of figured that out, but isn't there a solution ? Why isn't any e-mail client able to connect ?

---

### Post by jfreak_ on 2012-05-07
Bumpity bump bump 
:D

---

### Post by smurphy on 2012-05-07
because they are using another protocol and don't talk HTTP.
What you may want to do - is setup an openvpn tunnel tjhrough port 443, and tunnel all your traffic through that tunnel (also know as backhoming). But that is only something for people knowing how to set it up, what security risks it includes, and who really don't have another choice :}

---

