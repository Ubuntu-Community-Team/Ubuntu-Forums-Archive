---
title: "Ubuntu Firefox cannot open website"
date: 2010-10-24
forum: General Help
---

### Post by ghatzige on 2010-10-24
Firefox in Ubuntu does not allow me to open a website. The name is

[http://_.722253.n3.nabble.com/](http://_.722253.n3.nabble.com/)

On the contrary, Firefox in Windows opens the website.

Do you have any suggestions? Is it because of the _. in the beginning?

---

### Post by knutschr on 2010-10-25
I tried with Google Chrome.
It did not open here either.

---

### Post by WorMzy on 2010-10-25
[http://downforeveryoneorjustme.com/http://_.722253.n3.nabble.com/](http://downforeveryoneorjustme.com/http://_.722253.n3.nabble.com/)

```
wormzy@sakura[pts/10]:~$ ping _.722253.n3.nabble.com
ping: unknown host _.722253.n3.nabble.com

---

wormzy@sakura[pts/12]:~$ ping www.google.com        
PING www.l.google.com (173.194.37.104) 56(84) bytes of data.
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=1 ttl=54 time=42.6 ms
```

It's not just firefox. That address is just not valid. I'm surprised if it works on Windows.

---

### Post by SeijiSensei on 2010-10-25
> **WorMzy said:**
> ping: unknown host _.722253.n3.nabble.com

That address is just not valid. I'm surprised if it works on Windows.

Me, too. Underscores are not valid in hostnames, only hyphens.  From [RFC 952]("http://tools.ietf.org/html/rfc952"), "A 'name' (Net, Host, Gateway, or Domain name) is a text string up to 24 characters drawn from the alphabet (A-Z), digits (0-9), minus sign (-), and period (.)."

Windows seems less picky about hostnames, in part because hostnames in LAN Manager supported some special characters like the underscore.  We had a NT server in one client's office with an underscore in its name.  Windows had no problem with it, but Linux would object to its illegal name.

---

### Post by efflandt on 2010-10-25
The name resolves:

```
efflandt@efflandt-desktop:~$ host _.722253.n3.nabble.com
_.722253.n3.nabble.com has address 216.139.250.152

efflandt@efflandt-desktop:~$ dig _.722253.n3.nabble.com ns

; <<>> DiG 9.7.1-P2 <<>> _.722253.n3.nabble.com ns
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 65444
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;_.722253.n3.nabble.com.        IN    NS

;; AUTHORITY SECTION:
nabble.com.        3600    IN    SOA    dns3.nabble.com. root.nabble.com. 2010053101 7200 3600 604800 3600

;; Query time: 77 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Mon Oct 25 12:50:44 2010
;; MSG SIZE  rcvd: 86
```But Firefox says: **Firefox can't find the server at _.722253.n3.nabble.com.** so it is not responding and/or not configured properly for that name.  [www.nabble.com]("http://www.nabble.com") is one IP higher, but in same netblock (NET-216-130-240-0-1) 216.130.240.0 - 216.130.255.255

---

### Post by ghatzige on 2010-11-05
Thank you very much for all your answers. It seems that the website has wrong name. Windows are just lucky.

---

