---
title: "How can I Turn on a remote computer"
date: 2010-01-25
forum: General Help
---

### Post by ibrahim.k on 2010-01-25
Hi,
I am using ubuntu 9.10 and I want to know if I can power on a remote computer working on windows server 2003 

Can you please offer me help regarding this issue since it's important.

---

### Post by Grenage on 2010-01-25
You'll want to use WoL (wake on LAN), it enables a 'magic packet' to turn on the machine.

---

### Post by ibrahim.k on 2010-01-25
After enabling this feature what should I do ?
thnx



> **Grenage said:**
> You'll want to use WoL (wake on LAN), it enables a 'magic packet' to turn on the machine.

---

### Post by Grenage on 2010-01-25
Are you waking up the Windows machine from Ubuntu, or Ubuntu from the Windows machine?

---

### Post by ibrahim.k on 2010-01-25
I am waking up the windows machine from ubuntu 

thnx again

Also i have tried to wake up ubuntu from ubuntu using wakeonlan but it didn't work


> **Grenage said:**
> Are you waking up the Windows machine from Ubuntu, or Ubuntu from the Windows machine?

---

### Post by Grenage on 2010-01-25
Ensure WoL is enabled in the BIOS on the Windows server, then use *wakeonlan* to wake the windows server:

```
wol -i IP MAC
```

The IP of the server is optional, but recommended.

As for the Ubuntu machine, check that your adapter supports WoL:

```
sudo apt-get install ethtool
ethtool eth0
```

You'll see something like:

```
Auto-negotiation: on
Supports Wake-on: pumbg
```

To enable it:

```
ethtool -s eth0 wol g
```

---

