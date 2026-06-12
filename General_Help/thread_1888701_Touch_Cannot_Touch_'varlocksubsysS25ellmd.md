---
title: "Touch: Cannot Touch '\var\lock\subsys\S25ellmd"
date: 2011-11-29
forum: General Help
---

### Post by Anton Wan on 2011-11-29
My Ubuntu server (8.04.4 hardy) was restarted running a service that I need.  Error message I get is:

Starting S25ellmd:
touch: cannot touch '/var/lock/subsys/S25ellmd' : No such file or directory
Starting S26elmd.../sbin/start-stop-daemon: --start needs  --exec or --startas

Starting S27elived: /sbin/start-stop-daemon:  --start needs  --exec or --startas

When I try to start the services manually, it tells me that the files don't exist, but they do!  ???

Thanks in Advance,

Anton

---

### Post by galvatron408 on 2011-11-30
Starting S25ellmd:
touch: cannot touch '/var/lock/subsys/S25ellmd' : No such file or directory
Starting S26elmd.../sbin/start-stop-daemon: --start needs  --exec or --startas

type....

sudo touch /var/lock/subsys/S25ellmd

see what happens...

---

