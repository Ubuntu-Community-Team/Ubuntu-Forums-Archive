---
title: "ubuntu doesnt reboot after security update"
date: 2010-02-12
forum: General Help
---

### Post by orcurrentresident on 2010-02-12
I'm currently running Ubuntu 9.10 x64.  After a recent security update my ubuntu refuses to reboot from the system menu.  If I click System --> Shutdown and choose Restart, Ubuntu logs me out and immediately presents me with a Log-in Screen.

I can force a reboot by going to a terminal and doing a "sudo init 6" command

At the same time, my internet started behaving strangely.  immediately after starting up, i can access the internet perfectly fine.  Within 30 minutes of being rebooted, I am unable to access google.com or gmail.  (i'm still able to access most other sites.)  I've tried restarting my cable modem & router but the only thing that seems to fix it is doing a reboot via "init 6".

The two problems may be unrelated, but since they started at the same time I thought I'd mention it.

Any thoughts, comments, suggestions, or icecream will be greatly appreciated.  (especially the icecream)

Thanks in advance!

---

### Post by ironclaw on 2010-02-12
Check syslog and messages in /var/log/ when the problems occur (or just use the Log File Viewer utility 'gnome-system-log'). There may be useful information there.

---

