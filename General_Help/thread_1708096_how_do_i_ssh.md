---
title: "how do i ssh?"
date: 2011-03-16
forum: General Help
---

### Post by xoron on 2011-03-16
hi 

i want to set up my ubuntu box so that i can access it through ssh but it doesnt seem to be working :s

im have installed ssh and openssh-server through repos but its still not working :S

can someone help me please?

thanks in advanced! :)

---

### Post by matt_symes on 2011-03-16
Hi

Open a terminal and type

```
ssh <your_user_name>@<the_ip_address_of_server>
```

ie. 

```
ssh matthew@192.168.1.99
```

then enter your password.

Kind regards

---

### Post by slackthumbz on 2011-03-16
```
ssh username@host
```

Does the machine you're connecting to have a static IP? Also, if it's behind a router then you'll need to configure NAT forwarding as the only IP you'll get from outside the home network is that of the router itself.

---

