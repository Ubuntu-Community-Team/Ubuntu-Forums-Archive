---
title: "Noob,please help"
date: 2010-08-10
forum: General Help
---

### Post by bender1 on 2010-08-10
hi ,i installed Vmare on XP and i installed ubuntu on it ,and i amde a private server of a MMO,what can i do so that my friends can connect to the server?cuz XP has other Ip then ubuntu .(ps.game uses a .bat file to connect to server)can u help me with instructions?please ,ty.nca't i do a port forwording from XP to ubuntu ,if i can ,intructions please?

---

### Post by bender1 on 2010-08-10
can someone tell me?

---

### Post by alex88 on 2010-08-10
maybe if you write better you will be helped...

---

### Post by bender1 on 2010-08-10
this is my first post,how can i write ,what do i need to write?

---

### Post by b0z0n3 on 2010-08-10
It seems like your problem isn't with ubuntu, but more in the way VMware gives your Virtual Machin an IP adress.

Is yourNetwork set as Bridged, NAT or Host-only in VMware?

---

### Post by bender1 on 2010-08-10
this are my settings [http://www.imageno.com/cruro0h8fwlgpic.html]("http://www.imageno.com/cruro0h8fwlgpic.html")  and it's NAT in vmare:D

---

### Post by bender1 on 2010-08-10
what should i do?

---

### Post by bender1 on 2010-08-10
anyone?

---

### Post by Vaphell on 2010-08-10
check if you can ping the IP address assigned to the VM from outside (from host or from other machine on your local network).

---

### Post by bender1 on 2010-08-10
i can ping it.i mean from my XP(host)but i ask a friend to ping it from him but couldnt.
what do i do?

---

### Post by bender1 on 2010-08-11
can i install hamachi so i avoid all this problems?

---

### Post by elricscripts on 2010-08-12
The settings you linked to, those are your local area network IP addresses.  Is your friend trying to connect from your local area network (e.g. the Ubuntu system to the XP system), or are they connecting from the Internet?

I'm getting very hypothetical because i don't know the setup... but if you are trying to get someone to connect from the Internet to your XP/Ubuntu system, it depends on several factors.  For example how many Internet connections do you have, and how is VM Ware routing the WAN to the LAN?

---

### Post by b0z0n3 on 2010-08-27
> **bender1 said:**
> this are my settings [http://www.imageno.com/cruro0h8fwlgpic.html]("http://www.imageno.com/cruro0h8fwlgpic.html")  and it's NAT in vmare:D
If it is NAT, the you can't ping it from the outside  - you should bridge it so the VM gets an IP address from the 'real' network.

---

