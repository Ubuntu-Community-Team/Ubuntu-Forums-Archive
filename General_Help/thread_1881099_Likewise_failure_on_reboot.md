---
title: "Likewise failure on reboot"
date: 2011-11-14
forum: General Help
---

### Post by Alizhdheg on 2011-11-14
I'm relatively new to Ubuntu and have installed 11.10 clean on my netbook.  I installed Likewise to join to my AD domain and all was well until I installed all updates on the system.  Now whenever I reboot I cannot login using my domain credentials.  When I log in using the local username and pull up Likewise, I find that it is in an error state: ERROR_FILE_NOT_FOUND.

The easiest way to fix it is to use Synaptic to reinstall Likewise, but after a reboot it will fail again.  I've completely removed Likewise (clean) and reinstalled with the same issue.  This is very frustrating for me.

Does anybody know what I can do to fix it?  I've searched Google, but all I see are others with the same issue and no resolution.

---

### Post by clubbing80s on 2011-11-14
Do you have a valid network connection after rebooting ?

Try setting apparmor to complain. I have noted that after installing Likewise Apparmor is broken and dhcp networking breaks. 


G

---

### Post by Alizhdheg on 2011-11-15
Networking seems to be fine.  Everything works, with the exception of Likewise.  What's interesting is doing a repair on Likewise reconnects me to the domain.  I don't have to rejoin the domain or configure it at all.

---

