---
title: "Ubuntu 8.04 Hardy need curl-config"
date: 2009-11-03
forum: General Help
---

### Post by KayakJim on 2009-11-03
I am attempting to compile an application and during the ./configure stage I am receiving the following message:
```
checking for curl >= 7.18.2... FAILED
configure: error: curl-config was not found
```

I do have CURL installed and receive the following from curl -V:
```
curl 7.18.0 (x86_64-pc-linux-gnu) libcurl/7.18.0 OpenSSL/0.9.8g zlib/1.2.3.3 libidn/1.1
Protocols: tftp ftp telnet dict ldap ldaps http file https ftps
Features: GSS-Negotiate IDN IPv6 Largefile NTLM SSL libz
```

When I do sudo apt-get install curl I am told that it is already at the newest version. How do I upgrade from 7.18.0 to 7.18.2?

Any help would be appreciated in resolving this issue.

---

