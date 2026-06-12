---
title: "All ports closed by default?"
date: 2009-09-04
forum: General Help
---

### Post by TinyKnob on 2009-09-04
I've just started testing Ubuntu Server on an old Dell in preparation for setting up a small file server at home.  From my Windows-machine, I'm using Putty to connect to the Dell via SSH.  This works great.

But from what I've read, all ports on Ubuntu are closed by default (except port 22?).  So why am I still able to connect via SSH after changing the default port in **/etc/ssh/sshd_config**?

Doesn't make sense to me, but I'm new at this so what do I know. :)

---

### Post by i.r.id10t on 2009-09-04
Ports are only blocked IF you enable the firewall (ufw).

You can do something like

ufw allow ssh

or 

ufw allow 2222 (some port)

and then

ufw enable

To actually enable the ufw firewall.

---

### Post by TinyKnob on 2009-09-04
Ahhh, I see.  Thanks! :D

---

### Post by Whiffle on 2009-09-04
By default, there are no services that are running that will answer on external ports, making it act like they're closed.  When you install the ssh server, it responds on port 22.

---

### Post by TinyKnob on 2009-09-04
Appreciate the help, thank you.

---

### Post by The Cog on 2009-09-04
You need to restart sshd after changing the config.
sudo /etc/init.d/ssh restart

You don't need a firewall unless you have a need to be selective about which IP addresses can access a particular service. Just stop the services you don't want people to connect to. **sudo netstat -lntp** will tell you which ports are open and by which programs.

---

