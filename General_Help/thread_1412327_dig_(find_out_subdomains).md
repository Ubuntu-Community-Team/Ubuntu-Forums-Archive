---
title: "dig (find out subdomains)"
date: 2010-02-21
forum: General Help
---

### Post by alin19 on 2010-02-21
i was looking for a way to find out all subdomains of a domain and i have found dig. 

But it doesn't seam to work how i sow in those tutorials.

this is what i get:
[PHP]root@alin-laptop:~# dig example.com

; <<>> DiG 9.6.1-P2 <<>> example.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17948
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;example.com.            IN    A

;; ANSWER SECTION:
example.com.        89997    IN    A    192.0.32.10

;; Query time: 46 msec
;; SERVER: *************
;; WHEN: Sun Feb 21 11:02:50 2010
;; MSG SIZE  rcvd: 45

[/PHP]Is there other way that i can find out all subdomains of a domain?

---

### Post by Ryan Dwyer on 2010-02-21
No. DNS does not work that way.

---

