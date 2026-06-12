---
title: "Need to ssh by name not IP"
date: 2009-11-19
forum: General Help
---

### Post by tarekeldeeb on 2009-11-19
Hello, 

I have set a 10 PC network .. all having karmic. I also installed openssh-server to all for easier administration.

The problem I face is I always forget which PC has which IP. They have host names PC1, PC2 ..

I always make: ssh [email]mylogin@192.168.0.bla[/email]
then I get it to the terminal displaying:
mylogin@pc7:~$


how can I possibly make: ssh mylogin@pc7 directly?

Thanks in advance,

Tarek

---

### Post by dcstar on 2009-11-19
> **tarekeldeeb said:**
> Hello, 

I have set a 10 PC network .. all having karmic. I also installed openssh-server to all for easier administration.

The problem I face is I always forget which PC has which IP. They have host names PC1, PC2 ..

I always make: ssh [email]mylogin@192.168.0.bla[/email]
then I get it to the terminal displaying:
mylogin@pc7:~$


how can I possibly make: ssh mylogin@pc7 directly?

Thanks in advance,

Tarek

Put the entries in your /etc/hosts file.

---

### Post by tarekeldeeb on 2009-11-19
> **dcstar said:**
> Put the entries in your /etc/hosts file.

thanks for the quick reply ..
but this task will be a headache to do for each PC.
Moreover, if the DHCP server (for any reason) assigned different IPs, then I will have to re-do it.

Is there a dynamic way ?

Like when you go to Places -> Network, PCs with windows share appear with their correct names.

---

