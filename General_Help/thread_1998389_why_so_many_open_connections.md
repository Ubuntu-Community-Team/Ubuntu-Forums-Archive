---
title: "why so many open connections?"
date: 2012-06-06
forum: General Help
---

### Post by Mia_tech on 2012-06-06
guys, I just did a fresh install of xubuntu, and I have so many open connections to 91.189.88.33 that is not even funny. Is this new in the new release of ubuntu/xubuntu. The process is "gvfsd-htt" and here's the info for the remote address

```
IP Information - 91.189.88.33

IP address:                     91.189.88.33
Reverse DNS:                    scandium.canonical.com.
Reverse DNS authenticity:       [Verified]
ASN:                            41231
ASN Name:                       CANONICAL-AS (Canonical Ltd AS Number)
IP range connectivity:          0
Registrar (per ASN):            RIPE
Country (per IP registrar):     IM []
Country Currency:               Unknown 
Country IP Range:               91.189.88.0 to 91.189.95.255
Country fraud profile:          Normal
City (per outside source):      Unknown
Country (per outside source):   UK [United Kingdom]
Private (internal) IP?          No
IP address registrar:           whois.ripe.net
Known Proxy?                    No
Link for WHOIS:                 91.189.88.33
```

obviously this is an ubuntu/canonical server, I wonder was is the function of this process, and why is it always spawning open connections?

take a look at the snapshot...
[IMG]http://pctechtips.org/apps/ubuntu_connections.jpg[/IMG]

---

### Post by Toz on 2012-06-06
Looks like a bug. Have a look here: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/760344]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/760344"). Post #8 doesn't bode well.

Interesting that I'm not seeing this though. Are you using rhythmbox?

---

