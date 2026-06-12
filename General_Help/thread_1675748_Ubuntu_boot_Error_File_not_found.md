---
title: "Ubuntu boot: Error: File not found"
date: 2011-01-26
forum: General Help
---

### Post by jordsters on 2011-01-26
First of all, sorry if I have posted this in the wrong section. I have recently upgraded to 11.04 Natty Narwhal, and when I boot it up, I get "error: file not found" then if you wait a minute or two, it boots up as normal. Is this something I should take notice of? Thanks.

---

### Post by djeikyb on 2011-01-26
I have no idea what that refers to. You might try looking through /var/log. I'd start with these:

boot
boot.log
bootstrap.log
syslog
dmesg

---

### Post by gordintoronto on 2011-01-26
Note that there is a forum for beta testing.

---

### Post by jordsters on 2011-01-26
> **djeikyb said:**
> I have no idea what that refers to. You might try looking through /var/log. I'd start with these:

boot
boot.log
bootstrap.log
syslog
dmesg
Ahh, thanks, will do. Come to think of it, I might just downgrade back to 10.10.

> **gordintoronto said:**
> Note that there is a forum for beta testing.
Ok, thanks. I'll check that out.

EDIT: I've downgraded back to 10.10. I'll just wait for 11.04 to come out of alpha. Thanks anyway.

---

