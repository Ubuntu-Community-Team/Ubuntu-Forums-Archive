---
title: "CUPS problem after wake-up"
date: 2006-02-23
forum: General Help
---

### Post by anandrd on 2006-02-23
CUPS works perfectly well when I start the computer but when it sleeps and wakes up, somehow CUPS stops functioning. When I try to start cupsd as a regular user, I get "Child exited with status 13". When I try to start it as root, I get "Child exited with status 99."

The error log shows this error

E [23/Feb/2006:17:46:34 -0500] StartListening: Unable to bind socket for address 7f000001:631 - Cannot assign requested address.

---

### Post by anandrd on 2006-02-23
I think the problem is not with wake-up but with dhclient. I recently started using dhclient to configure my DHCP IPs instead of dhcpcd and that's when the trouble started. I will use dhcpcd and report back if the problem persists.

---

