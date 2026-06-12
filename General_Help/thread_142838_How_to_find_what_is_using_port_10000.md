---
title: "How to find what is using port 10000?"
date: 2006-03-11
forum: General Help
---

### Post by az_human on 2006-03-11
I recently hosed my Breezy install with an attempt to upgrade to Dapper...

So I'm back to Breezy, and now I am trying to reinstall Zend Studio... but it tells me that port 10000 is in use (Zend uses this port for debugging)... and I have never experienced this particular problem before.

I don't believe I have anything new or different on my system this time.

Anyhow, the question is: How do I find what processes or programs are using what ports?

Thanks a ton!!

---

### Post by varunus on 2006-03-11
Install "firestarter" from synaptic.  Its a graphical frontend to the built-in linux firewall "iptables."  It will show you what programs are using what ports (and don't worry, Ubuntu starts with its firewall always on and blocking all ports; you actually need firestarter to open any).

---

### Post by az_human on 2006-03-11
Ahhh that's right... and it's funny because I was just installing Firestarter right after I posted that (not remembering that it showed me all active connections, though)...

Thanks!  Much appreciated.

However, it is showing that nothing is using port 10000 so I'll hunt around and see what the crap Zend is thinking...

Thanks again!

---

### Post by youbaji on 2006-03-11
netstat -anp|grep 10000
you'll find the pid of the program using port 10000

---

### Post by rkelly on 2006-03-11
Have you installed Webmin?
It´s using port 10000 by default...

---

### Post by az_human on 2006-03-11
[QUOTE=rkelly]Have you installed Webmin?
It´s using port 10000 by default...[/QUOTE]

AAaaarrrrgggghhhh!!!  That was it!  Duh!  Hehehehe... forgot all about that one!

I couldn't figure out how to use it, anyway... granted I didn't spend too much time with it.

Thanks everybody! \\:D/

---

