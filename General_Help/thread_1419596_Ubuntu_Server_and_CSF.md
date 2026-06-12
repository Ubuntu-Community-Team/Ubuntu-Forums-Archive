---
title: "Ubuntu Server and CSF"
date: 2010-03-02
forum: General Help
---

### Post by snake_eyes on 2010-03-02
Hello,

I have 7 servers Ubuntu 8.4 server and the CSF installed on 5 of them, one of the CSF installed which is the mail server blocking automatically some IPS, below is an example:

```

	IP address	Port	Dir	TTL (secs)	Comment
 Unblock 192.168.118.72? 	192.168.118.72	*	in	276	lfd - *Port Scan* detected from 192.168.118.72 (**/-/alloushi-pc.domain.com). 11 hits in the last 221 seconds
 Unblock 192.168.118.83? 	192.168.118.83	*	in	281	lfd - *Port Scan* detected from 192.168.118.83 (**/-/b-b2-eng4.domain.com). 11 hits in the last 226 seconds
 Unblock 10.10.10.25? 	10.10.10.25	*	in	644	lfd - *Port Scan* detected from 10.10.10.25 (**/-/mail2.domain.com). 11 hits in the last 297 seconds
 Unblock 192.168.118.30? 	192.168.118.30	*	in	679	lfd - *Port Scan* detected from 192.168.118.30 (**/-/b-b3-303.domain.com). 11 hits in the last 30 seconds
 Unblock 192.168.118.194? 	192.168.118.194	*	in	1211	lfd - *Port Scan* detected from 192.168.118.194 (**/-/b-b1-303.domain.com). 11 hits in the last 261 seconds

```

So how I can solve this matter? plz note that one of the mentioned ip's is mine, Although I'm working on Ubuntu 9.10 desktop and the rest are windows

Cheers,

---

