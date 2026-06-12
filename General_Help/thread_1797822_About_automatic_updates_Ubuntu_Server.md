---
title: "About automatic updates Ubuntu Server"
date: 2011-07-05
forum: General Help
---

### Post by Jeinhor on 2011-07-05
Hi,

I'm running Ubuntu Server 10.10 on a SVN/Git server I'm hosting. On this server, I've configured cron to check status of the server, and send me an email when something fails. It also sends a heartbeat mail twice a month.

This has been working fine, but after the 15th of May this year I suddenly stopped receiving the heartbeats. Turned out I had an error in the syslog about cron, saying "Module is unknown". Apparently, some security update was installed automatically, which made the cron daemon fail. I restarted the daemon and it's now working again.

So, my question is: do ubuntu server automatically download and install security updates? And if so, how do I disable it using the command line (this server have no GUI).

Thanks in advance!

---

### Post by seawolf167 on 2011-07-05
Take a look at [this page ]("https://help.ubuntu.com/10.10/serverguide/C/automatic-updates.html")and see if it answers your question.

---

### Post by Jeinhor on 2011-07-18
Yep, that did it. However, no file named 10periodic existed, but I found another one named 20auto-upgrades where I could disable unattended upgrades.

Thanks :)

---

### Post by seawolf167 on 2011-07-19
Awesome, glad it worked!

---

