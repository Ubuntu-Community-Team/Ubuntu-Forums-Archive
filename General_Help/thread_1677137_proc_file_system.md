---
title: "proc file system"
date: 2011-01-28
forum: General Help
---

### Post by AlanTuring on 2011-01-28
**Is it possible to 'hide' a process from the listing of `ps` on Linux?**

---

### Post by yetiman64 on 2011-01-28
> **AlanTuring said:**
> **Is it possible to 'hide' a process from the listing of `ps` on Linux?**

Looking for hidden processes is one of the tests that can be enabled in rkhunter (it is off by default as it requires the "unhide" package installed and is a slow test to run), so I assume it's safe to say it is possible.

A small excerpt from Rootkit Hunters output on this machine,

```
  Performing **malware** checks
    Checking running processes for suspicious files          [ None found ]
    **Checking for hidden processes                            [ None found ]**
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

```

---

