---
title: "Security check on my smb.conf for Samba-daemon"
date: 2012-07-03
forum: General Help
---

### Post by mogie on 2012-07-03
Hello forum!

There are so many options to how I can configure my shares in Samba with user validation and security around each solution. I then ask what would be the simplest and most secure solution to my need here:

1. Everyone on the local network is allowed access. I use this on each local share:
```
hosts allow = 192.168.0.0/255.255.255.0
```

2. At the same time I'd like one internet-shared folder too, preferably with one username and one password (most secure of course, but simplified)

I'm sorry I dont exacly know what I'm talking about, but here's a sample of my smb.conf until now. Please let me know what I should do different, it's not yet completed:

```

[global]
        workgroup = ARBEIDSGRUPPE
        netbios name = lnx
        security = share
        server string = lnx
        directory mode = 755
        create mode = 744

socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=131072 SO_SNDBUF=131072


        debug level = 0
[www]
        force user = www-data
        comment = www
        path = /var/www
        browseable = no
        guest ok = Yes
        read only = No
        hosts allow = 192.168.0.0/255.255.255.0

[share]
        comment = raid0
        path = /mnt/tera
        guest ok = Yes
        read only = No
        browseable = Yes
        hosts allow = 192.168.0.0/255.255.255.0

[outside]
        comment = external
        path = /mnt/tera
        browseable = No
        username = ????



```

---

### Post by mogie on 2012-07-05
Anybody knows about any other very related config-file I could look upon?

---

