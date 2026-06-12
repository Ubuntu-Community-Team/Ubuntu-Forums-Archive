---
title: "Run program as root at boot time"
date: 2009-07-19
forum: General Help
---

### Post by snorkytheweasel on 2009-07-19
How do I configure ubu to run, as root, a program at boot time?

The program is /usr/local/sbin/dnsmasq.

---

### Post by michy99 on 2009-07-19
System->Preferences->Startup Applications->Add

---

### Post by snorkytheweasel on 2009-07-19
> **michy99 said:**
> System->Preferences->Startup Applications->Add

My 8.10 installation has System->Preferences->Sessions->Startup Programs->Add

Close enough, but will it run as root?

---

### Post by Zorael on 2009-07-19
I'd add it to **/etc/rc.local**, as a new line somewhere before 'exit 0'.

---

