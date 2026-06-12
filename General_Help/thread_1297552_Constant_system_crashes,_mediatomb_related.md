---
title: "Constant system crashes, mediatomb related?"
date: 2009-10-21
forum: General Help
---

### Post by Swil on 2009-10-21
I've got a ubuntu 9.04 based server running with mediatomb. The system crashes completely at least once a day, needing a hard reboot.

I've googled around and there seem to be some people saying mediatomb's periodic scan of media folders might be behind it. I have it scanning folders every 30 minutes.

Any ideas on what it might be or how I could track the problem down?

---

### Post by superdav42 on 2009-10-21
Disable mediatomb and see if it stops?

Look at the log files after a reboot. In particular /var/log/messages and /var/log/dmesg and /var/log/dmesg.0

---

### Post by buntunoob on 2009-10-28
Why not just set it to   Inotify---- Enable filesystem event based rescans

---

