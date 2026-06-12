---
title: "Stop tomcat from starting at boot time"
date: 2009-09-16
forum: General Help
---

### Post by Ang89 on 2009-09-16
Hi all, I've installed tomcat using synaptic, and now it's automatically started at boot time. The question is, can I stop this from starting at boot time? This tomcat service is not listed in System->Administration->Services. I know I can just delete the appropriate entry in /etc/rc?.d folder, but is there any cleaner way to do this?

---

### Post by Ang89 on 2009-09-20
Never mind. I just found the command *sudo update-rc.d -f tomcat5.5 remove*

---

