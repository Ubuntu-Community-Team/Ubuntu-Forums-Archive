---
title: "Open VMware tools aren't detected by VMware Workstation"
date: 2011-07-17
forum: General Help
---

### Post by wiseguy12851 on 2011-07-17
I have installed the latest version of Ubuntu Linux (11.04) into latest VMware workstation (7.1.4 build-385536). I have tried to install the VMware tools ISO that came with VMware workstation but It didn't work and the installation seemed real sloppy anyways. 

I installed the open VMware tools from synaptic within the guest linux and restarted, everything seemed to have been installed just fine but VMware Workstation doesn't detect it. I'm not sure if the tools are outdated, silent errors happened, or if any manual post installation steps need to be taken.

I need help getting any form of VMware tools to run in Linux and detected by VMware Workstation.

---

### Post by HermanAB on 2011-07-17
VMware Tools must be installed on the client, not the host.  Assuming that you are talking about the client, ensure that the VMware Tools service is actually started.

---

### Post by wiseguy12851 on 2011-07-17
How do you determine if it's started and if not how would you start it and add it to be started automatically?

---

### Post by wiseguy12851 on 2011-07-17
I temporarily moved it to another computer and it the new computer's VMware detected the installed VMware tools so obviously the problem lies within the other VMware and not Ubuntu even though their both fresh installations running the exact same host system.

---

