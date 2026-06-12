---
title: "fetchmail problem"
date: 2010-05-21
forum: General Help
---

### Post by evaristegalois on 2010-05-21
I've used fetchmail for quite a while now and never had a problem, until (without having changed anything) today it suddenly quit working, giving me the error message:

> fetchmail: connection to localhost:smtp [127.0.0.1/25] failed: Connection refused.
fetchmail: SMTP connect to localhost failed
fetchmail: SMTP transaction error while fetching from stefan%mydomain.com@mail.mydomain.com and delivering to SMTP host localhost
fetchmail: Query status=10 (SMTP)

I googled the error message, but didn't find anything that look promising.

---

### Post by dcstar on 2010-05-21
> **evaristegalois said:**
> I've used fetchmail for quite a while now and never had a problem, until (without having changed anything) today it suddenly quit working, giving me the error message:



I googled the error message, but didn't find anything that look promising.

```
telnet localhost 25
```

If it connects then your system still works, if it doesn't then some process has stopped working or there is something blocking the port.

And do not "quote" data, use the Code function.

---

