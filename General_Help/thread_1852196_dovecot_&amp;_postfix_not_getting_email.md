---
title: "dovecot &amp; postfix not getting email"
date: 2011-09-29
forum: General Help
---

### Post by ActiveHost on 2011-09-29
here is my hostname activehost.servehttp.com

i can send and receive mail locally ex: [EMAIL="webmaster@activehost.servehttp.com"]webmaster@activehost.servehttp.com[/EMAIL]
i can also send mail outward using smtp relay server to gmail yahoo or hotmail

but i cant receive any emails from gmail or hotmail into my local mail ex: [EMAIL="webmaster@activehost.servehttp.com"]webmaster@activehost.servehttp.com[/EMAIL]

what would be causing this?

im running latest ubuntu server 11
ispconfig 3
webmin
postfix
dovecot
php
mysql
apache2
avamis

---

### Post by ActiveHost on 2011-09-29
i know that my isp blocks in and out port 25
so i uncomment submission in cfg file

---

### Post by ActiveHost on 2011-09-29
are my mx a ptr record ok?

> 
dan@activehost:~$ dig activehost.servehttp.com

; <<>> DiG 9.7.3 <<>> activehost.servehttp.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2361
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;activehost.servehttp.com.      IN      A

;; ANSWER SECTION:
activehost.servehttp.com. 60    IN      A       65.95.45.51

;; Query time: 23 msec
;; SERVER: 207.164.234.129#53(207.164.234.129)
;; WHEN: Thu Sep 29 18:43:48 2011
;; MSG SIZE  rcvd: 58

dan@activehost:~$ dig activehost.servehttp.com mx

; <<>> DiG 9.7.3 <<>> activehost.servehttp.com mx
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64569
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;activehost.servehttp.com.      IN      MX

;; ANSWER SECTION:
activehost.servehttp.com. 60    IN      MX      5 mail.activehost.servehttp.com.

;; Query time: 24 msec
;; SERVER: 207.164.234.129#53(207.164.234.129)
;; WHEN: Thu Sep 29 18:44:14 2011
;; MSG SIZE  rcvd: 63



---

### Post by dcstar on 2011-09-30
> **ActiveHost said:**
> are my mx a ptr record ok?
[LIST=1]
[*]Don't "Quote" Code.
[*]No:
[*]```
Source	TTL	Address Type	Record Type1	Resolution

mail.activehost.servehttp.com.	60	IN	MX	mail.activehost.servehttp.com. (5)

mail.activehost.servehttp.com.  60	IN	A	76.65.186.182
```
[*]This is the SOA:```
Source	TTL	Address Type	Record Type1	Resolution

servehttp.com.	60	IN	SOA	nf1.no-ip.com. hostmaster.no-ip.com. 2009333126 90 120 604800 60
```
[/LIST]

---

