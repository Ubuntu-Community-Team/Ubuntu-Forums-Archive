---
title: "telnet service hw?"
date: 2010-04-30
forum: General Help
---

### Post by ottosykora on 2010-04-30
need to talk to ubuntu 10.04 via normal telnet.
Installed telnet from repository, this allows me now to contact other machines from this ubuntu, but I need also to contact this ubuntu from other machines. 
What do I need to do to enable telnet service reachable via standard p 23?

(pls no lectures abt security of telnet, this is closed network for test and development purposes)

---

### Post by psusi on 2010-04-30
Why don't you just use ssh?

---

### Post by wirelessmonkey on 2010-04-30
You need to install and configure telnetd. Telnet is just the client application.

---

### Post by ottosykora on 2010-05-01
telnetd is installed, but still I can not contact this machine by simple telnet .. command.
How do I set up and start and configure the service?

---

### Post by ottosykora on 2010-05-01
>Why don't you just use ssh?<

simple: all other machines involved do not have it and can not have it and will not have it since those are embeded silid state devices with very limited operating system.

---

