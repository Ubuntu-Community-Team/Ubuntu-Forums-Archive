---
title: "Broken logs"
date: 2012-10-06
forum: General Help
---

### Post by henrythemouse on 2012-10-06
I'm having a hard time believing that my logging issues are ubuntu issues. I'm posting this hoping that other ubuntu users will take a look at their logs and confirm that they either have a problem or don't.

On Sept 23, 2012 certain system logs stopped logging on my ubuntu laptop. These logs were working fine up until that time. Some were rotated, creating a new log file, which thereafter remained empty. Some just have no entries after the 23rd, but would normally have daily entries.

I run ubuntu 12.04 on two other computers in my household and neither are having this issue, but both are running stock ubuntu installs.

Some of the files affected are:

kern.log
syslog
dmesg
boot.log
samba/log.winbindd

I'm at a total loss, needless to say. On that day I did do an upgrade. Synaptic tells me it did this:

Commit Log for Sun Sep 23 14:32:57 2012


Upgraded the following packages:
ghostscript (9.05~dfsg-0ubuntu4.1) to 9.05~dfsg-0ubuntu4.2
ghostscript-cups (9.05~dfsg-0ubuntu4.1) to 9.05~dfsg-0ubuntu4.2
libgs9 (9.05~dfsg-0ubuntu4.1) to 9.05~dfsg-0ubuntu4.2
libgs9-common (9.05~dfsg-0ubuntu4.1) to 9.05~dfsg-0ubuntu4.2

Anyway, anyone else having this problem?

TIA

---

### Post by Bashing-om on 2012-10-06
nope, my 12.04.1 logging is up to date, see no opens.

hope you find what has disabled logging !

---

### Post by henrythemouse on 2012-10-09
> **Bashing-om said:**
> nope, my 12.04.1 logging is up to date, see no opens.

hope you find what has disabled logging !

Thanks for the reply.

---

