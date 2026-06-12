---
title: "ettercap"
date: 2009-07-23
forum: General Help
---

### Post by davewickett on 2009-07-23
ettercap

when i scan for hosts i get this message 


"SSL dissection needs a valid 'redir_command_on' script in the etter.conf file
Privileges dropped to UID 65534 GID 65534..."

need help to configure the file i think

---

### Post by DLGandalf on 2009-10-14
the ubuntu forum hates people who use ettercap it seems, I'm being ignored all the time too, 

but in this case the solution to your problem is VERY easy, the solution is the same as the hint given in your topic-start.

remove the '#' in the /etc/etter.conf file before the 2 lines which start with something like: 

# iptables {........}

/edit
topic is pretty old :S

---

