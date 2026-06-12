---
title: "*having server problems, behind rotuer*"
date: 2006-02-11
forum: General Help
---

### Post by kruz on 2006-02-11
hey, say in theory
i have 30 pc's behind a router, so they all essentially have 1 computer

if i setup a bind dns server on one of the computers that had a certain port forward to them
could i make it so that when u connect to that main server, u can acess other servers?

okay
say pc 1 is the server, that is the DMZ host, and its ip is 192.168.1.100

and i have other computers, that are essentially ghost to the outside world
192.168.1.101-200
and they all have vnc servers running on them
could i setup a dmz server to where if i connect to

username.pc1'sexternalwebsite.com then it would go to that computer inside the network??

any other suggestions

thanx

---

### Post by dcstar on 2006-02-11
[QUOTE=kruz]hey, say in theory
i have 30 pc's behind a router, so they all essentially have 1 computer

if i setup a bind dns server on one of the computers that had a certain port forward to them
could i make it so that when u connect to that main server, u can acess other servers?

okay
say pc 1 is the server, that is the DMZ host, and its ip is 192.168.1.100

and i have other computers, that are essentially ghost to the outside world
192.168.1.101-200
and they all have vnc servers running on them
could i setup a dmz server to where if i connect to

username.pc1'sexternalwebsite.com then it would go to that computer inside the network??

any other suggestions

thanx[/QUOTE]

Do a forum search for "Connection Sharing".

---

### Post by ttallos on 2006-02-12
You can do this by changing port ## with vnc on each machine I am not exactly sure how I have done it in windows. The router has to have the ports forward to each different internal IP. You will probubly have to tweak some settings to get it to work.

---

