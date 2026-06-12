---
title: "Mtink doesn't work even though I'm a member of the group lp"
date: 2012-03-10
forum: General Help
---

### Post by Amurko on 2012-03-10
sudo adduser (myself) lp

The user `(myself)' is already a member of `lp'

So I try running sudo mtink.

Still says "No access to printer device file" (blah blah blah) You must be a member of the group lp.

I can't check my ink levels anymore.  This is highly unacceptable!!  I don't care if mtink no longer works, I need something that'll enable me to check my ink!!!!

---

### Post by Amurko on 2012-03-10
Never Mind..  Solved:

sudo gedit /etc/modprobe.d/blacklist-cups-usblp.conf
comment out blacklist (e.g. #blacklist usblp)

Reboot

run sudo modprobe usblp

---

