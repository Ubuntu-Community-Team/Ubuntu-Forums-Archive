---
title: "XDMCP login between linked computers doesn't work"
date: 2009-09-22
forum: General Help
---

### Post by t0p on 2009-09-22
I've got a desktop computer running Xubuntu Hardy and a netbook running Eeebuntu Jaunty.  They're connected by crossover cable, and I give them ip addresses (desktop = 192.168.0.1, netbook = 192.168.0.2) so I can ssh between them.

I want to be able to log into the dektop from the netbook.  So I went to Login Window settings on the desktop and enabled XDMCP remote logins.

But when I logged out of the netbook, then tried to log into remote XDMCP server, it says it can't detect any XMCP servers on the network.  I tried to add the desktop to the network by using the Add button in the XDMCP Login window - using its ip address 192.168.0.1, then its hostname, ubunty.local - but it comes back saying the desktop computer did not respond and it's probably not accepting XDMCP logins.  Which is nonsense, I just enabled remote XDMCP logins on the damn machine - I can go look at Login Window settings on the desktop computer and it says it's accepting remote XDMCP logins... 

So why can't I do the remote login?  What can I do to figure out why the desktop machine won't let me log in?  Is there some kind of problem with XDMCP over crossover cable?  What can I do to enable remote login over crossover cable?

---

### Post by t0p on 2009-09-23
*bump*

---

