---
title: "how to configure dial up on a laptop"
date: 2006-05-31
forum: General Help
---

### Post by tomslopez on 2006-05-31
I have an HP Pavilion ze5270, and I want to connect to internet through dial up, but I don't know how to configure it to make it work, can anyone help me out how to do it?
Thank You.

---

### Post by nemtudod on 2006-05-31
sudo pppconfig

---

### Post by gborzi on 2006-05-31
Is the internal modem of your laptop already working ? If the answer is "yes", then follow the advice of nemtudod. If the answer is "no", then post the model of your internal modem, and I'll try to help. Use lspci to see the model.
Please note that not all internal modem are supported by the Linux kernel.

---

### Post by tomslopez on 2006-06-06
My internal modem model is:
> Modem: ALi Corporation M5457 AC'97 Modem Controller

---

### Post by gborzi on 2006-06-06
Your model is supported, but the ubuntu kernel does not have the module for it. BTW, the kernel in the final stable dapper no longer includes some modules that were included in the beta and the various flight. Among the missing modules, the one for my internal modem ](*,)  .
Using google I have found the following page for your modem
[http://who.is.free.fr/wiki/index.php?M5457](http://who.is.free.fr/wiki/index.php?M5457)
at a first read it doesn't seem an easy task to set up your modem.

---

