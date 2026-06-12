---
title: "Log into one IM account on multiple computers(Preferably with pidgin)?"
date: 2010-04-13
forum: General Help
---

### Post by lildigiman on 2010-04-13
I've got multiple PCs (Running Ubuntu) lying around my house and I'd like to make it easier to go between computers and not have to log in and out of each computer. Ideally, I'd like one computer to be a host running pidgin. The host would then allow the other PCs to read/write to the pidgin account logged in on the host. This would most definitely involve some coding. Unfortunately I'm mostly Java Trained, but I have some C++ under my belt as well.

Any Suggestions? Think out of the box too, what I said above is only what I think will work, but maybe you guys have better ideas.

Thanks!

---

### Post by falconindy on 2010-04-13
- use bitlbee to connect to your IM services on the server
- run an IRC client like irssi or weechat in a named screen session on the server
- connect to the server via ssh and use 'screen -xr <session_name>' to attach to that screen session.
- profit!

---

### Post by partloer on 2010-04-13
Hi lildigiman,

I am not sure what you are trying to accomplish.

> I'd like to make it easier to go between computers and not have to log in and out of each computer.

If you could explain a little more what you are trying to do I might be able to help.

---

### Post by lildigiman on 2010-04-14
> **partloer said:**
> Hi lildigiman,

I am not sure what you are trying to accomplish.



If you could explain a little more what you are trying to do I might be able to help.

Haha - I'd like not to log in and out of my IM account between the computers.

Thanks. Sorry for any misunderstanding.

---

### Post by lildigiman on 2010-04-14
Falconindy I think I just may try that! Let's see how that works out...

---

