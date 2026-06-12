---
title: "Server 9.04 hangs indefinitely 'starting crond'"
date: 2009-07-28
forum: General Help
---

### Post by DigitalMocking on 2009-07-28
Morning everyone.  

I've got a weird issue with a 9.04 server build that's been running fine.  I haven't installed anything recently other than updates, after a reboot this morning (server room power shutoff) the system hangs indefinitely at 'starting crond' in normal mode.  I can boot recovery and start/stop crond without a problem, and I've got nothing in messages or dmesg.  Any ideas?

---

### Post by DigitalMocking on 2009-07-28
I'm really not sure what's going on with this server now.  I don't think the problem is with crond.  I removed crond from the startup and the system gives a login prompt, but just hangs when you give it a username/password.

There's nothing out of the ordinary in dmesg or messages when you boot in recovery mode.

---

### Post by dlmarti on 2009-07-28
First thing I would do is grab your install CD.

1. Run the memory checker ( for a while ).
2. Boot off of the CD and check the logs on the HD.

---

