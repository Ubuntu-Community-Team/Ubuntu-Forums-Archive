---
title: "mrtg"
date: 2010-10-16
forum: General Help
---

### Post by g.badawi on 2010-10-16
i need to run it each time from terminal to make mrtg grow
env LANG=C /usr/bin/mrtg /etc/mrtg/mrtg.cfg
that what is in my 
/etc/cron.d/mrtg
*/5 *l * * * root if [ ! -d /var/lock/mrtg ]; then mkdir /var/lock/mrtg; fi; if [ -x /usr/bin/mrtg ] && [ -r /etc/mrtg.cfg ]; then env LANG=C /usr/bin/mrtg /etc/mrtg.cfg 2>&1 | tee -a /var/log/mrtg/mrtg.log ; fi

---

