---
title: "need help with dns"
date: 2009-10-31
forum: General Help
---

### Post by ronyh on 2009-10-31
Hey, I'm kind of new to ubuntu been using it for maybe a week tops on my dedicated server and i decided to buy a domain, now I'm trying to set it all up so that i can type in my domain name and it directs me to my server instead of typing in my ip all the time. I dont really have much experience with ubuntu i installed webmin on the server and followed a guide to link my domain. when i do a dig this is what comes up:

```
; <<>> DiG 9.4.2 <<>> website.info
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50794
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 2

;; QUESTION SECTION:
;website.info.            IN    A

;; ANSWER SECTION:
website.info.        38400    IN    A    123.456.78.90

;; AUTHORITY SECTION:
website.info.        38400    IN    NS    ns1.website.info.
website.info.        38400    IN    NS    ns2.website.info.
website.info.        38400    IN    NS    website.info.

;; ADDITIONAL SECTION:
ns1.website.info.    38400    IN    A    123.456.78.90
ns2.website.info.    38400    IN    A    123.456.78.90

```Assuming 
123.456.78.90 = my server IP which i use to access my server.
website.info = my domain name.

Is everything setup correctly here? sorry once again if this is a simple question im just trying to learn rather then pay for someone to do it for me. Thanks

-Rony

---

