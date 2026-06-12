---
title: "Auto Restart Ubuntu Desktop"
date: 2011-05-01
forum: General Help
---

### Post by person287 on 2011-05-01
How can I get Ubuntu 10.10 Desktop to Automatically Restart at say 3am? It's pretty much a default installation at the moment.

Thanks

---

### Post by Joe of loath on 2011-05-01
Firstly, why?

Secondly, run 'man crontab', work out what you need to write down in crontab, then 'sudo crontab -e' and write it in, with the command as reboot.

---

