---
title: "Can't connect to citrix"
date: 2009-08-07
forum: General Help
---

### Post by jan0ng on 2009-08-07
Good day,

Kindly help me to fix it.  I have already installed properly the application from citrix but when I tried to connect, there is a client error message saying that: You have not chosen to trust "/C=US/ST=/L=/0=Equifax/OU=Equifax Secure Certificate Authority/CN=", the issuer of the server's security certificate (ssl error 61).

Thanks for you help...

---

### Post by jan0ng on 2009-08-07
I have already fix it.  Thanks

---

### Post by fhlh on 2009-08-10
what's the fix?:popcorn:

---

### Post by jan0ng on 2009-08-14
I'll inform you I forgot the website

---

### Post by Lahntaler on 2009-08-20
Check this URL:
[http://blog.torh.net/2008/02/29/problems-with-citrix-client-on-linux/]("http://blog.torh.net/2008/02/29/problems-with-citrix-client-on-linux/")

But on my Ubuntu 8.04 sits the missing Equifax certificate in /etc/ssl/certs

My RHEL5 system at work has libpurple installed. There I did:
```
cp -ip /usr/share/purple/ca-certs/Equifax_Secure_CA.pem /usr/lib/ICAClient/keystore/cacerts
chgrp sys /usr/lib/ICAClient/keystore/cacerts/Equifax_Secure_CA.pem
```

---

