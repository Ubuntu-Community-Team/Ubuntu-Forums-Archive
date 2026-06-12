---
title: "x2go &quot;failed password&quot; on Ubuntu 11.10"
date: 2011-10-28
forum: General Help
---

### Post by poguemahone on 2011-10-28
I'm trying to use x2go to connect from a windows client (x2go Client 3.01-4) to x2goserver on Ubuntu 11.10.  Unfortunately, I have been unable to get it to work.  Here are the results from /var/log/auth.log

```
Oct 28 16:31:50 inspiron sshd[22450]: Failed password for justin from 173.8.XXX.YYY port 50240 ssh2
```

I am able to use ssh to login via Putty.

Additionally, here is the log from the x2go client:

```
Loop: PANIC! The remote NX proxy closed the connection.
Loop: PANIC! Failure negotiating the session in stage '7'.
Loop: PANIC! Wrong version or invalid session authentication cookie.

```
Any ideas?

---

