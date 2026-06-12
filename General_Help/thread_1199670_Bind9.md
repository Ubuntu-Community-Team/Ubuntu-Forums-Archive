---
title: "Bind9"
date: 2009-06-29
forum: General Help
---

### Post by xiaomahe on 2009-06-29
hai i am still rather new to ubuntu, and i am currently using 8.10

I had 1 question, what is actually bind9? can someone explain in a simple word for me?

according to what i had understand, i can create a virtual web domain using bind9 (so, it is not really a legal domain). Hence, i can name the domain according to my wish rite?

So, for my example, i built a php website, and i am using lampserver to do it. So, instead of typing localhost/filename.php  i can just type the domain name (for example: CoolWeb.com), am i right?

---

### Post by alphacrucis2 on 2009-06-29
> **xiaomahe said:**
> hai i am still rather new to ubuntu, and i am currently using 8.10

I had 1 question, what is actually bind9? can someone explain in a simple word for me?

according to what i had understand, i can create a virtual web domain using bind9 (so, it is not really a legal domain). Hence, i can name the domain according to my wish rite?

So, for my example, i built a php website, and i am using lampserver to do it. So, instead of typing localhost/filename.php  i can just type the domain name (for example: CoolWeb.com), am i right?

Sure you can do that but any local device using your copy bind9 as its' resolver will find the fake coolweb.com rather an a real authoritative one from the net, which may be what you want of course. Another approach is to use a reserved tld such as .test, or .example. So you would have for your domain: coolweb.test which won't conflict with anything on the public internet. I have come across the .local tld being used for this purpose but .local isn't actually reserved, so in the future it could in theory end up as a valid public tld.


Whoops. Forgot to answer your first question about what is bind9. It is DNS server software. Berkeley Internet Name Daemon. One of the more common ones used in the Internet DNS. Some reading for you"

[http://en.wikipedia.org/wiki/BIND]("http://en.wikipedia.org/wiki/BIND")

and 

[http://www.bind9.net/]("http://www.bind9.net/")

---

### Post by xiaomahe on 2009-06-29
hi, so i can really actually set up a fake domain name right?

i had tried setting up the DNS using BIND9 just now.. and it seems that i could not set my IP to the domain name that i have just created.. what's wrong with it?


my ip is 10.0.0.2 and i set the name into mysecure.com

but when i reload the bind9, and i do dig, mysecure.com did not show my ip address, but it showed other ip address.

---

### Post by alphacrucis2 on 2009-06-29
> **xiaomahe said:**
> hi, so i can really actually set up a fake domain name right?

i had tried setting up the DNS using BIND9 just now.. and it seems that i could not set my IP to the domain name that i have just created.. what's wrong with it?


my ip is 10.0.0.2 and i set the name into mysecure.com

but when i reload the bind9, and i do dig, mysecure.com did not show my ip address, but it showed other ip address.

Just starting bind9 won't do anything. You have to also tell your system to use it as the DNS resolver.

---

### Post by xiaomahe on 2009-06-30
hai, i have solved my problem by reconfiguring for almost like 10 times.. 

after i dig secure.sec , server shown as localhost, not 10.0.0.2

; <<>> DiG 9.5.0-P2 <<>> secure.sec
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 15846
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;secure.sec.			IN	A

;; ANSWER SECTION:
secure.sec.		86400	IN	A	10.0.0.2

;; AUTHORITY SECTION:
secure.sec.		86400	IN	NS	secure.sec.

;; Query time: 7 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Jul  1 05:52:37 2009
;; MSG SIZE  rcvd: 58


is that ok?

---

