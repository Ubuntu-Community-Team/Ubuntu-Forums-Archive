---
title: "sudoers syntax, &quot;lecture=always&quot; not working"
date: 2006-05-16
forum: General Help
---

### Post by halfvolle melk on 2006-05-16
Hi,
I'd like to get a lecture every time I use sudo just for fun.

Changing the line
```
Defaults        !lecture,tty_tickets,!fqdn
```
to
```
Defaults        lecture=always,tty_tickets,!fqdn
```
doesn't work, but doesn't return errors either. I've tried a few variants, some return an error, some don't, none work. I don't understand the man page.

Also, something wierd happens when editing it. Using 'sudo visudo' afterwards it always says
```
visudo: sudoers file unchanged
```
but if I then do 'sudo cat /etc/sudoers' it does show the changes. I also tried if it makes a difference editing as root with vi (a big no-no I'll bet) but it doesn't.

Any ideas on how to get lecture working?
Thanks.

Ps: insults is working fine :mrgreen:

edit: well, the syntax appears to be correct anyway. It works after 'sudo -K' and then 'sudo something'. And I should have read the visudo man page ... don't change the name of the lock file.

edit2: Oh, I forgot. The lecture is quite boring and  always the same. Any way to randomize it and spice it up?

---

