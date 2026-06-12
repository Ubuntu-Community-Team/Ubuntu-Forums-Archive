---
title: "log Interpreting"
date: 2010-06-25
forum: General Help
---

### Post by linux_lrnr on 2010-06-25
hi Guys,
what does the following message mean? I found this message in my SSH log file .
 
Failed password for root from 173.13.101.153 port 49141 ssh2
Failed password for invalid user chris from 173.13.101.153 port 49239 ssh2
Failed password for root from 173.13.101.153 port 49338 ssh2
 
Any help is appreciated.
 
Thanks

---

### Post by supergrav on 2010-06-25
I think that ssh log file stores the attempts made to login to your system from any user such as "root", "chris" etc. Probably as this log informs you somebody was trying to login unsuccessfully from address 173.13.101.153...

---

### Post by Dustin2128 on 2010-06-25
> **supergrav said:**
> I think that ssh log file stores the attempts made to login to your system from any user such as "root", "chris" etc. Probably as this log informs you somebody was trying to login unsuccessfully from address 173.13.101.153...
which is not good assuming that's not your IP. I'd guess that IS your IP, you just typo'd your password a time or two. If its not, either you tried to access it remotely with typo'd password or someone else is trying to access it remotely. Server or desktop?

---

