---
title: "Host and dig in terminal"
date: 2010-08-21
forum: General Help
---

### Post by cetoka on 2010-08-21
I have been trying ''host'' and ''dig'' commands in the terminal but when I try ''dig'' I get an answer like this:
; <<>> DiG 9.7.0-P1 <<>> bw-in-f103.1e100.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45678
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;bw-in-f103.1e100.net.      IN   A

;; ANSWER SECTION:
bw-in-f103.1e100.net.   85230   IN   A   74.125.43.103

;; Query time: 68 msec
;; SERVER: 208.67.220.220#53(208.67.220.220)
;; WHEN: Fri Aug 20 09:51:24 2010
;; MSG SIZE  rcvd: 54
----------------desktop:~$ 
The Authority and the Additional parts are missing.What do I have to do  in order to see those sections.I tried with OpenDNS and GoogleDNS and  also with different IP numbers but everytime the answer was the  same,those two parts missing.
                                                    The version of the dnsutils is:
-------an-desktop:~$ dpkg -l | grep dnsutils
ii  dnsutils                             1:9.7.0.dfsg.P1-1                               Clients provided with BIND

And Ubuntu is 10.04 LTS with all the updates is now 10.04.1

---

