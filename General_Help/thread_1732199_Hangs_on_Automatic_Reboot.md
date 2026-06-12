---
title: "Hangs on Automatic Reboot"
date: 2011-04-17
forum: General Help
---

### Post by gfunkdave on 2011-04-17
I'm perplexed and hoping someone has some ideas.

I've got a server running Lucid that hangs sometimes (not every time!) when it tries to reboot automatically. I used to have it reboot weekly via root's crontab and first noticed the problem then. Now, I have it reboot when it needs to after an automatic update by running a script daily that checks for the existence of /var/run/reboot-required.

Initially, I had the crontab, and currently the script, call /sbin/reboot when required. I thought that might be the problem, so I changed it to "/sbin/shutdown -r now". But it still hangs. The only thing I can do to fix it is wait until people get back into the office and hold the power button until the machine turns off, then turn it back on.

Does anyone know what's going on here, or how I might go about diagnosing?

Thanks!

---

