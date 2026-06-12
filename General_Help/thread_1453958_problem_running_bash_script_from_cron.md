---
title: "problem running bash script from cron"
date: 2010-04-14
forum: General Help
---

### Post by abubin on 2010-04-14
i have a very simple bash script that I schedule to run every hour.

But the problem is, this script does run but the command inside doesn't work.

If I run it manually, it works. I am puzzled!!!

Here is the script:
```

#!/bin/bash
/usr/bin/pon vpn1

```

crontab run under root user.
30 */1 * * * /home/script.sh

Problem is not the cron but the script doesn't work when run under cron.

If I run it manually using ./script.sh, then it will work.

Any ideas?

*the pon command is to connect to a remote vpn server

---

### Post by prodigy_ on 2010-04-14
> **abubin said:**
> 30 */1 * * * /home/script.sh
Are you sure that the path to the script is **/home** and not **/home/<your_user_name>**?

---

### Post by john newbuntu on 2010-04-14
Interesting! Check the script path.  Also check /var/log/syslog to see for any errors.  Just to make sure cron is not able to run this, put a debug statement such as:
echo `date` >> /tmp/jnk
before and after the pon command and debug it.

---

