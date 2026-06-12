---
title: "pages do not load on certain sites"
date: 2010-03-15
forum: General Help
---

### Post by foxy123 on 2010-03-15
I've got a weird problem. Pages do not load on certain sites (such as LinkedIn and Which? for example). The sites themselves load but when I click on links the pages load forever. With Which? I can close FF and open it again and then the link loads but after a few clicks they stop loading. It happens on all browsers (at least I tried FF and Chromium) but OK on Windows. Has anyone ever encountered something like this?

---

### Post by ajgreeny on 2010-03-15
Have you disabled ipv6 in your browser?  I've no idea how you can do it in others than FF, but in that enter **about:config** in the address bar, accept the warning about dragons, then in the filter type ipv6, and double click the line that shows:-

network.dns.disableIPv6;false

to change *false* to *true* at the end.  That may help with your problem.

---

### Post by foxy123 on 2010-03-16
> **ajgreeny said:**
> Have you disabled ipv6 in your browser?  I've no idea how you can do it in others than FF, but in that enter **about:config** in the address bar, accept the warning about dragons, then in the filter type ipv6, and double click the line that shows:-

network.dns.disableIPv6;false

to change *false* to *true* at the end.  That may help with your problem.
I had IPv6 disabled ages ago. Thanks anyway. Any other ideas?

---

### Post by lovinglinux on 2010-03-16
> **foxy123 said:**
> I had IPv6 disabled ages ago. Thanks anyway. Any other ideas?

Have you tried to use another DNS server, like OpenDNS or Google DNS?

Disabling the feature to block attack sites and web forgeries may help too.

---

### Post by dcstar on 2010-03-16
> **foxy123 said:**
> I had IPv6 disabled ages ago. Thanks anyway. Any other ideas?

The default Linux MTU may not be compatible with your router/network.

You may want to experiment with it to see if a reduction changes things.

---

