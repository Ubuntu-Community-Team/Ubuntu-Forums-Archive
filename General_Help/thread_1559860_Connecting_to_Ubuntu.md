---
title: "Connecting to Ubuntu"
date: 2010-08-24
forum: General Help
---

### Post by john.a on 2010-08-24
Hello,

I have installed Ubuntu(latest version) on my laptop (that has vista) using VirtualBox. Now i want to connect **to ubuntu** from windows using ssh, but it's not working.

can somebody please provide a step by step explanation how to configure the VM network adapter, the changes i should make on Ubuntu side and windows side ?

P.S: i've installed ssh on ubuntu (installed on windows too).

thanks in advance

---

### Post by aeiah on 2010-08-24
do you know the ip address you should be using? if not, in ubuntu do ```
ifconfig
``` in a terminal. you should see an entry for 'eth0'. you should be able to ping this ip and ssh into it. if not, where do these instructions stop working?

---

