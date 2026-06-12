---
title: "How to unban with fail2ban"
date: 2011-05-25
forum: General Help
---

### Post by dsjstc on 2011-05-25
Unbanning an IP with fail2ban appears to require several steps and manual counting of IPs.  Is there a better way?

---

### Post by dsjstc on 2011-05-25
Found it:

fail2ban-client set ssh delignoreip xx.xx.xx.xx

---

