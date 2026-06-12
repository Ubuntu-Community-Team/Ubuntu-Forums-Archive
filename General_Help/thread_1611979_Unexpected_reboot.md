---
title: "Unexpected reboot"
date: 2010-11-02
forum: General Help
---

### Post by jkounis on 2010-11-02
When I came in this morning, I found out that my Ubuntu machine had unexpectedly rebooted at around 3:15 am. I looked at both /var/log/syslog and /var/log/kern.log, and nothing unexpected is there. Here's the relevant portion of the kern.log.

The big gap between 03:15 and 11:33 is because the machine rebooted into the default operating system--windows--at 3:15. I found my machine in Windows, and then I rebooted to Linux at 11:33.

```
Nov  2 02:32:42 pgfs kernel: [29230.093927] usb 1-1: reset high speed USB device using ehci_hcd and address 2
Nov  2 02:37:00 pgfs kernel: [29487.672219] usb 1-1: reset high speed USB device using ehci_hcd and address 2
Nov  2 03:14:09 pgfs kernel: [31712.949694] usb 1-1: reset high speed USB device using ehci_hcd and address 2
Nov  2 03:15:54 pgfs kernel: [31817.794481] usb 1-1: reset high speed USB device using ehci_hcd and address 2
Nov  2 11:33:11 pgfs kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov  2 11:33:11 pgfs kernel: [    0.000000] Initializing cgroup subsys cpuset

```

Is there anyplace else I can look for hints as to why my machine suddenly rebooted?

I'm running Ubuntu 10.10 x86_64.

---

### Post by HermanAB on 2010-11-02
Buy a UPS.

---

### Post by fast_ian on 2010-11-02
> **HermanAB said:**
> Buy a UPS.

:D 

[Probably true though. ;)]

---

### Post by jkounis on 2010-11-02
Sorry, I should have mentioned that two machines are connected to the same power strip. The other one is still running.

Here's the uptime on the other machine on the same 
```
 12:05:46 up 19 days, 10:13,  5 users,  load average: 0.21, 0.24, 0.10

```

---

