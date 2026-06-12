---
title: "ldap and TLS/SSL"
date: 2011-11-12
forum: General Help
---

### Post by crakeador on 2011-11-12
hi guys,i am installed ldap service. I want connect as secure mode with TLS/SSL mode.
 
I made certificates with **openssl req -newkey rsa:1024 -x509 -nodes -out server-01.pem -keyout server-01.pem -days 365**. I configured archivos /etc/ldap/sldap.conf , /etc/ldap/ldap.conf y /etc/default/sldap as a lot of webs told.
 
 I made this proofs:
- **ps -A | grep slapd **: process enable
- **netstat -putan**: ports listened
- **nmap server-01**: ports open
- **ldapsearch -x**: i see database
 
but executing  **openssl s_client -connect server-01:636 -showcerts -debug**  this error is returned [b]read from 0x80c91c0 [0x80cede8] (7 bytes => 0 (0x0))
1874:error:140790E5:SSL routines:SSL23_WRITE:ssl handshake failure:s23_lib.c:188:[/b]
 
I need help, tahnks very much

---

