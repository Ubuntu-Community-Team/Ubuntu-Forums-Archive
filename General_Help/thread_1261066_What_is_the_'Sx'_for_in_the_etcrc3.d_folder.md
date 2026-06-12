---
title: "What is the 'Sx' for in the /etc/rc3.d folder ?"
date: 2009-09-08
forum: General Help
---

### Post by Dawson Lewis on 2009-09-08
Hi everyone ,

I am using ubuntu 8.10 I was reading about how to make scripts run at boot time and I found that the  /etc/rc3.d folder contains links for scripts in the /etc/init.d/ folder. After I run the *ls* command in the rc3.d folder I got the following output

[I]S18mysql-ndb                 S25bluetooth       S99rmnologin
S19mysql                     S25pulseaudio      S99stop-readahead
[/I]
What is the meaning of the 'Sx' (where x is a number)?  

Regards,

Dawson Lewis

---

### Post by sprilutsky on 2009-09-08
Hi there,

S - means start. Also, it has to be capital "S", not small "s"
K - means kill. Also, it has to be capital "K", not small "k"

Hope it helps

---

### Post by Dawson Lewis on 2009-09-08
> **sprilutsky said:**
> Hi there,

S - means start. Also, it has to be capital "S", not small "s"
K - means kill. Also, it has to be capital "K", not small "k"

Hope it helps

Understood.
Thanks for the quick reply 

Dawson

---

