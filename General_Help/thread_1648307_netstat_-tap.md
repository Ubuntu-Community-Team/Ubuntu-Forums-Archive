---
title: "netstat -tap"
date: 2010-12-18
forum: General Help
---

### Post by lex1 on 2010-12-18
Could someone please explain this line:



tcp        0      0 localhost.:kerberos-adm *:*                     LISTEN      4389/famd   

what is kerberos and famd?

thanks

lex1

;)

---

### Post by efflandt on 2010-12-19
/etc/services file tells what ports are ***monly used for what purpose.  Or netstat -tapn would list numerical ports and IP's instead of names

```
**cat /etc/services | grep kerberos**

kerberos            88/tcp        kerberos5 krb5 kerberos-sec    # Kerberos v5
kerberos            88/udp        kerberos5 krb5 kerberos-sec    # Kerberos v5
kerberos-adm       749/tcp                # Kerberos `kadmin' (v5)
kerberos4          750/udp        kerberos-iv kdc    # Kerberos (server)
kerberos4          750/tcp        kerberos-iv kdc
kerberos_master    751/udp                # Kerberos authentication
kerberos_master    751/tcp
```For      4389/famd 4389 is the PID and famd is the name of the program.  [http://en.wikipedia.org/wiki/File_alteration_monitor](http://en.wikipedia.org/wiki/File_alteration_monitor)

Why are the censor police blocking  c o m  when part of regular dictionary words?

---

### Post by lex1 on 2010-12-19
thanks for your post

"Why are the censor police blocking c o m when part of regular dictionary words?"

no idea

lex1;)

---

