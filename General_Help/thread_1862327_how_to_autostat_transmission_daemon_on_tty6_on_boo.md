---
title: "how to autostat transmission daemon on tty6 on boot ?"
date: 2011-10-16
forum: General Help
---

### Post by obarthelemy on 2011-10-16
Hi.

I'm running a bare cli, ubuntu 10.4 arm server.

I'm trying to get transmission-daemon -f to execute at boot, on tty6, with owner olivier.

right now, I'm getting 3 instances of it, and a locked-up tty6 (ctrl-c doesn't work), with:

expect fork
expect daemon
console owner

start on started tty6

exec transmission-daemon-f

What am I doing wrong ?

Thanks for any help, Olivier

---

