---
title: "Can't RDP into virtualbox after upgrade"
date: 2011-10-30
forum: General Help
---

### Post by mbeltoft on 2011-10-30
After I upgraded my ubuntu server a few days ago I haven't been able to RDP into virtualbox. I just get a connection refused error.
It worked before the upgrade.

I have checked that the guest OS (win XP) is running and that remote display is enabled.

I also did a sudo ufw allow all to disable any firewall block but still no go.

---

### Post by dcstar on 2011-10-31
> **mbeltoft said:**
> After I upgraded my ubuntu server a few days ago I haven't been able to RDP into virtualbox. I just get a connection refused error.
It worked before the upgrade.

I have checked that the guest OS (win XP) is running and that remote display is enabled.

I also did a sudo ufw allow all to disable any firewall block but still no go.

```
telnet *ip-address-of-host* 3389
```
If you get some sort of response then there is a connection path, if it times out then something is blocking it.

---

### Post by mbeltoft on 2011-10-31
Tried to telnet to it via Putty.
it says:
Connection closed by remote host
Network error: Connection Refused

I'm guessing that something is actively blocking it but what??

I have no problem connecting via ssh or to the webserver running on it

---

### Post by keithy on 2011-10-31
Check to see that the virtual network adapter is running in bridged mode.

---

### Post by mbeltoft on 2011-11-01
it is.

and I can see the VM on the network and connect to it shares without problems

---

### Post by jacobrussell on 2012-01-20
i having the same issue have you figured this out yet ?

---

### Post by CharlesA on 2012-01-20
You'd need to install the extension pack if you want to use RDP to connect to a VM. That only works with the version from virtualbox.org, if I recall correctly.

---

### Post by jacobrussell on 2012-01-20
/facepalm 

My issue is now resolved. Thank you so much

---

