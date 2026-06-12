---
title: "VNC to desktop when not on the same network"
date: 2010-01-04
forum: General Help
---

### Post by bigggnick on 2010-01-04
Hello everyone,

I set up a remote desktop connection on my desktop and can connect to it from my laptop while on my home network (with a Linksys router). I'd like to connect to my desktop while on the go-from other networks (school, etc).  What IP address do I use to connect/how is this done?

Thanks for any help,

Nick

---

### Post by prem1er on 2010-01-04
You need to connect to your outside IP address, aka the address your ISP gives you. On your router you also need to forward the correct ports to the machine you are trying to connect. If you set up a free domain with your IP address you can access your computer that way instead of memorizing your IP each time.

---

### Post by doas777 on 2010-01-04
I seriously recommend that you avoid using VNC over the Internet. there are safer ways to get what you want. Saw a guy here a few weeks ago, who had exposed his VNC to the web, and was wondering why his mouse was moving when he wasn't using it.

FreeNX is probably the best bet. it runs over SSH, so instead of forwarding VNC, forward your ssh port. then install the server, and a client on your other PC. 

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by prem1er on 2010-01-04
> **doas777 said:**
> I seriously recommend that you avoid using VNC over the Internet. there are safer ways to get what you want. Saw a guy here a few weeks ago, who had exposed his VNC to the web, and was wondering why his mouse was moving when he wasn't using it.

FreeNX is probably the best bet. it runs over SSH, so instead of forwarding VNC, forward your ssh port. then install the server, and a client on your other PC. 

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

+1. Just outlining the method for the connection. Thanks.

---

### Post by bigggnick on 2010-01-04
thanks for the help, everyone! ill give that a shot.

---

