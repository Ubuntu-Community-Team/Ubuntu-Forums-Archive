---
title: "Ubuntu wireless DNS/IPV6 issues resolved in 10.04?"
date: 2010-06-06
forum: General Help
---

### Post by cAlpha on 2010-06-06
Can anyone confirm (or deny) that the wireless issues touched on [here]("https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757") have been fixed for Ubuntu 10.04?

I've still yet to find a fix for the very slow wireless speeds across apps (Firefox and Evolution both drag badly) that I'm seeing.

Please let me know if you've seen or heard of other fixes that I could try of if this has been cleared up in 10.04.  Thanks!

---

### Post by fragos on 2010-06-06
The delays you're talking about were caused by trying IPv6 DNS and having to wait for the timeout before using IPv4 for DNS. 10.04 has separate configuration for v4 and v6. V6 defaults to "ignore" which I'd think would solve the problem I described.

---

