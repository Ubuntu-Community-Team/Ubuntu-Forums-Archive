---
title: "The Joys of DNS Records"
date: 2011-05-03
forum: General Help
---

### Post by Trunkles on 2011-05-03
Joys of? Yeh, right!

DNS is making me go bald! Not grey though, I went grey years ago! :)

To business. I have a domain name and two sub-domains off it. Each has a web site and mail. All three sets of mail addresses are handled by the same server software. (Oh yes, I'm running natty server.) Getting mail in and out has gone pear shaped and, frankly, the whole things seems a mess.

Here is the current record set

```

$TTL        14400
@       IN      SOA     ns1.drsimon.co.nz. webmaster.drsimon.co.nz. (
                        2011050405         ; serial, todays date + todays serial #
                        28800              ; refresh, seconds
                        7200               ; retry, seconds
                        604800             ; expire, seconds
                        14400 )            ; minimum, seconds
;

; A records for the main domain and the two sub-domains
drsimon.co.nz.                  A               222.154.250.78
silverport.drsimon.co.nz.       A               222.154.250.78
aotearoawaka.drsimon.co.nz.     A               222.154.250.78

; Reverse lookup
78.250.154.222.in-addr.arpa.    PTR             drsimon.co.nz.

; The three sets of mail addresses are all handled by the one server
aotearoawaka.drsimon.co.nz      MX      10      mail.drsimon.co.nz
drsimon.co.nz.                  MX      10      mail.drsimon.co.nz
silverport.drsimon.co.nz.       MX      10      mail.drsimon.co.nz

; The web,chat and FTP servers and the chat server
www.drsimon.co.nz.              CNAME           drsimon.co.nz.
www.aotearoawaka.drsimon.co.nz. CNAME           aotearoawaka.drsimon.co.nz.
www.silverport.drsimon.co.nz.   CNAME           silverport.drsimon.co.nz.
ftp.drsimon.co.nz.              CNAME           drsimon.co.nz.
ftp.aotearoawaka.drsimon.co.nz. CNAME           aotearoawaka.drsimon.co.nz.
ftp.silverport.drsimon.co.nz.   CNAME           silverport.drsimon.co.nz.
rabbit.drsimon.co.nz.           CNAME           drsimon.co.nz.

; Do the name servers need A records
; ns1.drsimon.co.nz.            A               222.154.250.78 <--- Not needed?
; ns1.inter.net.nz.             A               121.73.240.178 <--- Not needed?

; The name servers
drsimon.co.nz.                  NS              ns1.drsimon.co.nz.
drsimon.co.nz.                  NS              ns1.inter.net.nz.


```

So, please, can a DNS guru please tell me what the f-f-f-flaming heck I've got wrong?

On hands and knees here say thank you!

Simon.

---

### Post by dcstar on 2011-05-04
> **Trunkles said:**
> Joys of? Yeh, right!

DNS is making me go bald! Not grey though, I went grey years ago! :)

To business. I have a domain name and two sub-domains off it. Each has a web site and mail. All three sets of mail addresses are handled by the same server software. (Oh yes, I'm running natty server.) Getting mail in and out has gone pear shaped and, frankly, the whole things seems a mess.

Here is the current record set

```

$TTL        14400
@       IN      SOA     ns1.drsimon.co.nz. webmaster.drsimon.co.nz. (
                        2011050405         ; serial, todays date + todays serial #
                        28800              ; refresh, seconds
                        7200               ; retry, seconds
                        604800             ; expire, seconds
                        14400 )            ; minimum, seconds
;

; A records for the main domain and the two sub-domains
drsimon.co.nz.                  A               222.154.250.78
silverport.drsimon.co.nz.       A               222.154.250.78
aotearoawaka.drsimon.co.nz.     A               222.154.250.78

; Reverse lookup
78.250.154.222.in-addr.arpa.    PTR             drsimon.co.nz.

; The three sets of mail addresses are all handled by the one server
aotearoawaka.drsimon.co.nz      MX      10      mail.drsimon.co.nz
drsimon.co.nz.                  MX      10      mail.drsimon.co.nz
silverport.drsimon.co.nz.       MX      10      mail.drsimon.co.nz

; The web,chat and FTP servers and the chat server
www.drsimon.co.nz.              CNAME           drsimon.co.nz.
www.aotearoawaka.drsimon.co.nz. CNAME           aotearoawaka.drsimon.co.nz.
www.silverport.drsimon.co.nz.   CNAME           silverport.drsimon.co.nz.
ftp.drsimon.co.nz.              CNAME           drsimon.co.nz.
ftp.aotearoawaka.drsimon.co.nz. CNAME           aotearoawaka.drsimon.co.nz.
ftp.silverport.drsimon.co.nz.   CNAME           silverport.drsimon.co.nz.
rabbit.drsimon.co.nz.           CNAME           drsimon.co.nz.

; Do the name servers need A records
; ns1.drsimon.co.nz.            A               222.154.250.78 <--- Not needed?
; ns1.inter.net.nz.             A               121.73.240.178 <--- Not needed?

; The name servers
drsimon.co.nz.                  NS              ns1.drsimon.co.nz.
drsimon.co.nz.                  NS              ns1.inter.net.nz.


```

So, please, can a DNS guru please tell me what the f-f-f-flaming heck I've got wrong?

On hands and knees here say thank you!

Simon.

And where is the A record for mail.drsimon.co.nz?

---

### Post by Trunkles on 2011-05-04
Ah. You mean the hidden A record in tiny text that isn't really there? The sort of theoretical A record that only a complete dunce like me would leave out?

Is that the record you mean?

You're a star David.

Thank you!

And yes, it is there now. :)

---

### Post by dcstar on 2011-05-04
> **Trunkles said:**
> Ah. You mean the hidden A record in tiny text that isn't really there? The sort of theoretical A record that only a complete dunce like me would leave out?

Is that the record you mean?

You're a star David.

Thank you!

And yes, it is there now. :)

If you ever have future DNS issues use the Ubuntu Network Tools to compare the problem site with a working one, any issues usually become apparent.

---

