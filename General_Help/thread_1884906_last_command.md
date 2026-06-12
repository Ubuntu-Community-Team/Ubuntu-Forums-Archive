---
title: "last command"
date: 2011-11-22
forum: General Help
---

### Post by techbrainless on 2011-11-22
Hi All,
I have checked  "last" and it contains only the current month  logs , it seems that it gets rotating monthly  , my questions are :
1. Is it possible to get the logs of the previous month using last command.
2. How to configure last to be rotated in a user defined period (something like 2 months , 6 months or 1 year)

---

### Post by gmargo on 2011-11-22
> **techbrainless said:**
> Hi All,
I have checked  "last" and it contains only the current month  logs , it seems that it gets rotating monthly  , my questions are :
1. Is it possible to get the logs of the previous month using last command.
2. How to configure last to be rotated in a user defined period (something like 2 months , 6 months or 1 year)

1. Previous month's log is **/var/log/wtmp.1**, so use "last -f /var/log/wtmp.1".

2. The log rotation parameters for /var/log/wtmp and /var/log/btmp are contained in **/etc/logrotate.conf**.

The log rotation entry contains the key "monthly" (which corresponds to the rotation period), and the key "rotate 1" (which corresponds to keeping 1 backup.)

You can choose "daily", "weekly", "monthly", or "yearly" for the rotation period.  And you can increase the 'rotate' value to keep more backups.

The **last** and **logrotate** man pages contain all the additional details.

---

