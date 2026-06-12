---
title: "Massive Problems with Postfix and email"
date: 2009-07-13
forum: General Help
---

### Post by doomsayer on 2009-07-13
Hey there,

Does anyone know the simplest way to get postfix to allow a server to handle email correctly? I've just put myself through the ringer all morning trying to find a way to get my new server's email working, and specifically just forward anything that would go to my name (ray@mxdwn) to forward to my gmail email.

I have this in main.cf


myhostname = mail.mxdwn.com

myorigin = mail.mxdwn.com
local_transport = error:local delivery is disabled

mydestination = mail.mxdwn.com, mxdwn.com, localhost.mxdwn.com localhost
inet_interfaces = 127.0.0.1

And I made sure to set up my mx record for email.

I also placed a .forward file in the home url for my user with my gmail email as the text.

For the life of me I can't figure out what I'm doing wrong here. Does anyone know what I might be doing incorrectly? I'm not even really looking to run a full mail server on my new server, I just need to be able to define that a certain email (somebody@mxdw) can be forwarded over to a different email, as most of my employees use gmail to handle their email.

Ack!

---

### Post by doomsayer on 2009-07-13
help!? anyone?

---

