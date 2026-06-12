---
title: "Remote Desktop Viewer problems"
date: 2010-05-19
forum: General Help
---

### Post by ozguitarplayer on 2010-05-19
Hi,
I have four home computers (linux) that I can easily access using Remote Desktop Viewer. Two of the computers have Windows partitions with UltraVNC installed and I can access them without a problem. 

However when I try to access a friends Windows computer in another part of the state I fail.
I have researched the issue at length and it appears to be as simple as it is in my home situation the exception being I need to use the external IP address of the other computer but when I try I get a message saying the computer I am trying to access is closed, (the other computer is turned on)
UltraVNC is used on the other computer and it has a dynamic IP address which I am updated with.
I have checked the Windows firewall and it will allow VNC and we have tried it with the anti-virus disabled just in case that firewall was causing an issue.
Lastly, remote access has been activated on the Windows computer.

Can't think of anything else to mention, anyone got any ideas to help fix the issue?

---

### Post by 2hot6ft2 on 2010-05-19
Port forwarding on your friends router and the firewall on their machine, also along with forwarding the port in the router they should set it to assign a static IP Address for the machine you're trying to connect with.
:popcorn:

---

### Post by ozguitarplayer on 2010-05-19
thanks 2hot6ft2 I'll try that out

---

