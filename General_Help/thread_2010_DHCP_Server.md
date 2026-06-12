---
title: "DHCP Server"
date: 2004-10-25
forum: General Help
---

### Post by Rule on 2004-10-25
Hi, I was wondering if I can set up ubuntu to be a dhcp server. And if so how can I do it? is it also possible to set it up to scan files for viruses as they pass through the computer?

TIA
Rule

---

### Post by shufla on 2004-10-25
Hello,

[QUOTE=Rule]Hi, I was wondering if I can set up ubuntu to be a dhcp server. And if so how can I do it?[/QUOTE]

Yes. Just install package `dhcp3-server' and configure it properly. Remeber that in Ubuntu packages are listening on non-local network interfaces.

[QUOTE=Rule]
 is it also possible to set it up to scan files for viruses as they pass through the computer?
[/QUOTE]

Huh, that's little complicated task. For emails, if your ubuntu system is acting as email server, you shuld install amavisd-new and clamav (synaptic will suggest you that). Then you have to configure postfix + amavis + clamav. But if you do want to scan http/ftp traffic for viruses, there is even more complicated - squid (web/ftp proxy server) isn't able to scan traffic for viruses in "easy" way... Google for solutions.

Best regards,
Lukasz Nowak

---

