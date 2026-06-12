---
title: "Samba Problems"
date: 2009-08-11
forum: General Help
---

### Post by ctimko on 2009-08-11
I am having some difficulties with my samba setup. It was originally working (runs on a server in Chicago) and I had it mapped in my laptop. I was able to use it without a problem. I got back to school, where I can't connect at all. So I decided to re-install everything thinking that I screwed up badly, but still I haven't gotten anywhere on this. So that said, I would really appreciate some assistance.  

```
[global]
        workgroup = WORKGROUP
        server string = Samba PDC running %v
        interfaces = eth0
        bind interfaces only = Yes
        log level = 2
        log file = /var/log/samba/log.%m
        max log size = 1000
        read raw = No
        disable netbios = Yes
        name resolve order = lmhosts host bcast
        socket options =
        hostname lookups = Yes
        load printers = No
        show add printer wizard = No
        os level = 65
        preferred master = Yes
        domain master = Yes
        dns proxy = No
        invalid users = nobody
        hosts allow = ALL
  domain logons = Yes
  wins support = Yes

[homes]
        comment = Samba Homes
        read only = No
        case sensitive = No
        browseable = No
  create mask = 0644
  directory mask = 0775

```

This is my first time configuring a Samba drive, so if I did something I wasn't supposed to do, let me know.

Ok, so the issue is this, when I do the "nmblookup -L <MYIP>" I get a "name_query failed to find name <MYIP>"

If you need anything else from me in order to figure this out, let me know, thanks.

Charles

---

### Post by ctimko on 2009-08-12
Anyone have any advice?

*BUMP*

---

