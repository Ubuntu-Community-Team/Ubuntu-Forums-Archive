---
title: "SSH and direct root access"
date: 2010-03-14
forum: General Help
---

### Post by eNc707 on 2010-03-14
Hi there,

PermitRootLogin is set to "yes" but I cannot login as root. Is there anything else to do? I found nothing via google or in this forum. :(

Thanks,
Frank

---

### Post by alarme on 2010-03-14
Can you log as root on console?
if not, type
sudo passwd root
and enter a valid password for root
but be careful
DON'T log as root if possible.  You can do everything with sudo <command>
this is more safe

---

### Post by eNc707 on 2010-03-15
Yes, on console everything works fine - and that's the problem. :(

> **alarme said:**
> but be careful
DON'T log as root if possible.  You can do everything with sudo <command>
this is more safe

Hehe... I'm not a complete linux newbe... ;)
It is just for a small webserver using a vm which has no connection to the "real world" - just for testing purposes... :)

But my problem isn't solved yet... :(

---

### Post by alarme on 2010-03-16
Can you log as other user?

---

### Post by eNc707 on 2010-03-16
Yep... that's no problem... :)

EDIT:

Solved the problem... there was no root password set... as default... sorry guys...
Anyway, thanks for help... :)

---

### Post by alarme on 2010-03-16
try:
ufw status

if enabled, you can:

a) disable the firewall
$ ufw disable

b) open only port 22
$ ufw allow 22/tcp

c) open all ports only to LAN
$ ufw allow from 192.168.1.0/24

---

### Post by eNc707 on 2010-03-16
Changed my last post same time you answered...
Tanks for your help... :)

---

