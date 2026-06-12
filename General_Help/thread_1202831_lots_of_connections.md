---
title: "lots of connections"
date: 2009-07-02
forum: General Help
---

### Post by philcamlin on 2009-07-02
ok i have foirestarter but it seems people are trying to connect on port 5900 and 80

if i open them will they be able to hack my apache or remte desktop ??

thats why im scared to use it because ive seen people get hacked 

is it safe to use remote desktop and i dont know about apache

but those ip's are foreign :(

if i open them up can i get hacked?

---

### Post by wojox on 2009-07-02
The port 80 is a google.bot

---

### Post by philcamlin on 2009-07-02
80 is apache isnt it :popcorn:  and can i gethacked through it ? 

and can i get hacked if i open 5900because its vnc and i want to use it when i go on trips but wil i get hacked?

---

### Post by credobyte on 2009-07-02
80 port can't be *hacked*, so .. yeah, you can open it ( if you have a web server ).

---

### Post by philcamlin on 2009-07-02
how about 5900 ? vnc ??

thats what scres me :(

---

### Post by philcamlin on 2009-07-02
bump

---

### Post by akakingess on 2009-07-02
I am by no means an expert, but anytime you remote in there is the chance of being hacked, obviously a firewall would help and I also choose to use odd ports to open up (in other words, ones that hackers wouldn't normally look for) like port 51385 or any random port like that, but it depends on whether your software will work with a different port and if you can configure as you wish.  Again, keep in mind I am not an expert on the subject, but this may be a direction worth looking into.

akakingess

---

### Post by philcamlin on 2009-07-02
> **akakingess said:**
> I am by no means an expert, but anytime you remote in there is the chance of being hacked, obviously a firewall would help and I also choose to use odd ports to open up (in other words, ones that hackers wouldn't normally look for) like port 51385 or any random port like that, but it depends on whether your software will work with a different port and if you can configure as you wish.  Again, keep in mind I am not an expert on the subject, but this may be a direction worth looking into.

akakingess

thanks :)

---

### Post by Brandon Williams on 2009-07-02
Any time you open a port for public access, yes, it's possible for someone to hack into your computer using that port. It's important for you to ensure that the server listening on that port is fully up to date with all security patches.

You can limit risk by limiting public access. For example, if all valid HTTP connections will come only from a small set of client IP addresses, then you can use iptables rules to drop incoming connections from unauthorized clients. For VNC, it's common to configure VNC so that it only listens on localhost, and then to connect to VNC through an SSH tunnel.

---

### Post by t4thfavor on 2009-07-02
I usually only open up one port to my ssh interface on the router, and when I need remote I login, and enable it. This way there is less chance of port scanners getting wind of my services. I also have my ports on non-standard numbers such as ssh on 2245 or 22222 its pretty easy to avoid bots, if you know what they are looking for.

leave 80 closed unless you actually use apache, if not theres no reason to open it.

---

### Post by akakingess on 2009-07-03
> **Brandon Williams said:**
> You can limit risk by limiting public access. For example, if all valid HTTP connections will come only from a small set of client IP addresses, then you can use iptables rules to drop incoming connections from unauthorized clients. For VNC, it's common to configure VNC so that it only listens on localhost, and then to connect to VNC through an SSH tunnel.

Thanks Brandon Williams, I had forgotten about the use of iptables, that is an excellent point and great advice.

akakingess

---

