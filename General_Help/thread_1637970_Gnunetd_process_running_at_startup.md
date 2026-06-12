---
title: "Gnunetd process running at startup"
date: 2010-12-05
forum: General Help
---

### Post by DanR01 on 2010-12-05
I installed Gnunet (a secure P2P program) on Ubuntu 10.10 using Ubuntu software centre but had difficulties getting it to work so removed it. 

However, the gnunetd process loads at startup. It is only visible when typing 'top' in the console and not in the system monitor list of processes.

*gnunetd --version* tells me that it is 0.8.1b

*sudo apt-get remove gnunetd* tells me 'unable to locate package'

Could anyone tell me why the process loads and how to remove it? I can kill it in the console but would like a way of getting rid of it permamently.

Thank you in advance and apologies if I've missed something obvious!

---

### Post by psihokiller4 on 2010-12-05
try locating package at:

**System --> Administration --> Synaptic Package manager**

try locate it in there

---

### Post by DanR01 on 2010-12-05
Thanks for the quick reply.

I found the problem I think - the process belonged to gnunet-server which I have now removed.

---

