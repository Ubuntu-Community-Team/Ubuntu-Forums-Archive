---
title: "Restart after changed logrotate apache2 configuration"
date: 2010-09-06
forum: General Help
---

### Post by bfrederi on 2010-09-06
When I change the configuration of the logrotate apache2 configuration file, do I need to restart the logrotate or apache2 service? If so, how do you typically restart the logrotate service?

---

### Post by bfrederi on 2010-09-06
Nevermind, I just read that logrotate is not a daemon. It's run by cron, so it doesn't need to be restarted.

---

