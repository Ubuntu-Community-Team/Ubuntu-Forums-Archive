---
title: "HUP console-kit-daemon"
date: 2011-06-01
forum: General Help
---

### Post by ianmorris1960 on 2011-06-01
HI,

Apologies if this is a dumb question, had a look round and not found the answer in a form I understand!

So my memory is dissapearing on my ubuntu 10.04.1 server, have been restarting the server, I have traced this to console-kit-daemon which seems to be eating lots of memory.

I have manually HUP'd this (via webmin) and this has restored the memory as if I had re-started the server.

Now I want to set up a cron task to HUP it.

From what I have read, I think this means HUP the process id, so the command line would be; kill -HUP 21529

I assume that is the system re-starts for any other reason the PID will change, is there a better way of doing this?

thanks

Ian

---

