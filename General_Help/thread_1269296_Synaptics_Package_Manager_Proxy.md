---
title: "Synaptics Package Manager Proxy"
date: 2009-09-18
forum: General Help
---

### Post by markvdm on 2009-09-18
Hi Guys

I'm a bit confused at the moment. I'm trying to download a few packages using Synaptics, but it keeps trying to use a proxy server. Now when I am at work I do connect to a proxy, so I usually change it under Synaptics and Network Proxy settings, then when connecting from home I change it back to Direct Connection.

However, today, when changing both back to Direct Connection Firefox works fine, but Synaptics is still trying to use the proxy. I even tried deleting the apt.conf file completely, but still it tries the proxy.

Any ideas? I'm not that savvy with Linux, but I usually find my way around.

---

### Post by dcstar on 2009-09-18
> **markvdm said:**
> Hi Guys

I'm a bit confused at the moment. I'm trying to download a few packages using Synaptics, but it keeps trying to use a proxy server. Now when I am at work I do connect to a proxy, so I usually change it under Synaptics and Network Proxy settings, then when connecting from home I change it back to Direct Connection.

However, today, when changing both back to Direct Connection Firefox works fine, but Synaptics is still trying to use the proxy. I even tried deleting the apt.conf file completely, but still it tries the proxy.

Any ideas? I'm not that savvy with Linux, but I usually find my way around.

Sometimes the Update Manager is running in background so your changes may not apply immediately. Wait 30 or so minutes or reboot and the proxy changes whould work.

---

