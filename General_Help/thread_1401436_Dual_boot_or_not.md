---
title: "Dual boot or not?"
date: 2010-02-08
forum: General Help
---

### Post by altjx on 2010-02-08
I'm dual booting BT4 and Ubuntu 9.10. My question is, rather than me having two separate partitions for this, could I just put BT4 in VMware and still be able to detect wireless networks from it? Just out of curiosity, does VMware machines have the capability of detecting wireless networks just like the host OS?

---

### Post by altjx on 2010-02-08
If I'm connected via ethernet, can VMware PC be connected to another wireless network using my wireless network adapter?

---

### Post by howefield on 2010-02-08
As long as your wireless is working in the host, the guest operating system will be able to use it.

---

### Post by 3rdalbum on 2010-02-08
> **howefield said:**
> As long as your wireless is working in the host, the guest operating system will be able to use it.

Kind of the opposite.

If the host has network access (wifi, 3G, ethernet, dialup etc), it will be presented to the guest as being an Ethernet connection.

The guest can use certain USB devices that have been "passed through" to the guest, as long as the host is not using them.

So, basically, you can't connect to a wireless network on the host and then use the guest to scan for wireless networks using the same adapter.

---

### Post by altjx on 2010-02-08
> **3rdalbum said:**
> Kind of the opposite.

If the host has network access (wifi, 3G, ethernet, dialup etc), it will be presented to the guest as being an Ethernet connection.

The guest can use certain USB devices that have been "passed through" to the guest, as long as the host is not using them.

So, basically, you can't connect to a wireless network on the host and then use the guest to scan for wireless networks using the same adapter.

Ah, what about connect to ethernet on the host and wireless on the guest?

---

